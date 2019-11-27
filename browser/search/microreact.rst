======================================
Uploading Search Results to MicroReact
======================================

This section covers building an advanced search output for uploading to MicroReact for visualisation. With this approach, we can provide a full ENA search result set as input to MicroReact without needing to save the results as a file anywhere.

Building The Search Query
-------------------------
Firstly, build an advanced search query. This involves selecting the data type to be queried (e.g. sample) and building the query with the desired parameters. Following this, in the fields section, select ‘Manually select fields’ and specify the fields which correspond to, and therefore map to, the required input for uploading to MicroReact (see `here <https://microreact.org/instructions>`_ for MicroReact uploading instructions). Specifically, this includes values for id,  country, latitude, longitude and date for each record. For each of the aforementioned, within the advanced search, the fields to select are:

- sample_accession for id
- country for country
- lat for latitude
- lon for longitude
- collection_date for date

Then you can set additional paramters like limit if necessary. Execute the built query with the specified fields to check if the results are what you expected, and then export the full search request using the 'Copy Curl Request' button in the search wizard (an example is shown below). This is required to construct a URL pointing to the search results which are utilised within the configuration file for MicroReact upload.

Example advanced search curl command to obtain human samples collected after 1/1/2018
::

    curl  -X POST -H "Content-Type: application/x-www-form-urlencoded" -d "dataPortal=pathogen&result=sample&query=collection_date%3E%3D2018-01-01%20AND%20host_tax_id%3D9606&fields=sample_accession%2Ccollection_date%2Ccountry&format=tsv" "https://www.ebi.ac.uk/ena/portal/api/search"

To construct the input URL required for MicroReact upload configuration, take the request body and join it to the Portal API search endpoint URL, as shown below.

The GET URL from the advanced search curl command becomes:
"https://www.ebi.ac.uk/ena/portal/api/search?query==collection_date%3E%3D2018-01-01%20AND%20host_tax_id%3D9606&fields=sample_accession%2Ccollection_date%2Ccountry%2lat%2lon&format=tsv"

MicroReact Configuration
------------------------
Once the above steps have been completed, we need to create a configuration file (JSON format) that utilises the search query. The URL created above forms the value for 'data'. The values for id, map_countryField, map_latitude, map_longitude and date must correspond to the field names specified in the advanced search.

An example of the contents of a configuration file. You can save the below in a file (e.g. microreact_configuration.json) and edit the name, description, email, website fields as required.
::

    {
    "name": "ENA Sample Test1",
    "description": "Test samples country",
    "email": "your@email",
    "website": "https://website.co.uk",
    "map_countryField": "country",
    "map_latitude": "lat",
    "map_longitude": "lon",
    "id": "sample_accession",
    "date": "collected_date"
    "data":"https://www.ebi.ac.uk/ena/portal/api/search?query==collection_date%3E%3D2018-01-01%20AND%20host_tax_id%3D9606&fields=sample_accession%2Ccollection_date%2Ccountry%2lat%2lon&format=tsv"
    }

MicroReact Usage
----------------
The configuration file above can then be utilised in a POST request to MicroReact in order to generate a MicroReact project:
::

    curl -i -H "Content-type: application/json; charset=UTF-8" -X post -d @microreact_configuration.json https://microreact.org/api/project

For more information on this, visit `MicroReact <https://microreact.org/showcase>`_.
