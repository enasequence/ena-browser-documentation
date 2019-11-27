======================================
Uploading Search Results to MicroReact
======================================

This section covers building an advanced search output for uploading to MicroReact for visualisation.

Building Search
---------------
Firstly, build an advanced search query. This involves selecting the data type to be queried (e.g. sample) and building the query with the desired parameters. Following this, in the fields section, select ‘Manually select fields’ and specify fields which correspond to, and therefore map to, the required input for uploading to MicroReact (see `here <https://microreact.org/instructions>`_ for MicroReact uploading instructions). Specifically, this includes values for id,  map_countryField, map_latitude, map_longitude and date. For example, for each of the aforementioned, within the advanced search, example fields to select include:

- sample_accession for id
- country for map_countryField
- lat for map_latitude
- lon for map_longitude
- collection_date for date


Search the built query with the specified fields and then within the browser copy the curl request (using the 'Copy Curl Request' button on the search results page), an example is shown below. This is required to construct a URL pointing to the search results which are utilised within the configuration file for MicroReact upload.

Example browser advanced search result curl command to obtain human samples collected following 1/1/2018
::

    curl  -X POST -H "Content-Type: application/x-www-form-urlencoded" -d "dataPortal=pathogen&result=sample&query=collection_date%3E%3D2018-01-01%20AND%20host_tax_id%3D9606&fields=sample_accession%2Ccollection_date%2Ccountry&format=tsv" "https://www.ebi.ac.uk/ena/portal/api/search"

To construct the URL required for MicroReact upload configuration, paste the Portal API URL with the query, as shown below.

The example URL from the advanced search curl command becomes:
"https://www.ebi.ac.uk/ena/portal/api/search?query==collection_date%3E%3D2018-01-01%20AND%20host_tax_id%3D9606&fields=sample_accession%2Ccollection_date%2Ccountry%2lat%2lon&format=tsv"

MicroReact Configuration
------------------------
Once the above steps have been completed, create a configuration file (JSON format) utilising the built search result information. The URL created above, forms the value for 'data'. The values for id, map_countryField, map_latitude, map_longitude and date must correspond to the field names specified in the advanced search.

An example of the contents of a configuration file (@microreact_configuration):
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
The configuration file above should then be utilised in a MicroReact POST curl in order to generate a MicroReact project:
::

    curl -i -H "Content-type: application/json; charset=UTF-8" -X post -d @microreact_configuration https://microreact.org/api/project

For more information on this, visit `MicroReact <https://microreact.org/showcase>`_.
