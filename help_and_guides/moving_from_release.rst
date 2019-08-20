============================
Moving away from the release
============================

..Outstanding tickets relating to this documentation
..DCP-2176 Add documentation endpoint to ENA Browser API, and include in swagger interface.
..DCP-2175 Add search endpoint to Browser API swagger interface
..DCP-2173 Partitioning from report improvements. Ability to obtain specific versions.
..DCO-2172 Add zip download option for the new sequence, coding and non-coding data types
..DCP-2172 Create new merged data types sequence coding and non-coding
..Decision on future of FTP update cumulative files. Will need a ticket to make the changes to the FTP file structure and disable flows.

Introduction
============

The ENA is retiring its periodic assembled/annotated sequence release in March 2020, the last release will be number 143.

The European Nucleotide Archive (ENA) captures, preserves and presents the world's nucleotide sequence data. Since 1982 the European Nucleotide Archive has made 140 individual releases, providing a quarterly snapshot of ENA assembled/annotated sequence data. During this time, changes to the ways in which users access ENA data, have led us to develop a portfolio of data access tools, such as our daily FTP products and the ENA Browser API, which are currently offered in parallel to the traditional release. In recent years we have faced growing pressure on the release process in response to increases in data volume and have also seen a shift towards our newer services from the majority of users. Our release process has remained largely unchanged for the last two decades, and following an internal review we have concluded that it is no longer viable for us to continue the current release process as part of our presentation portfolio.

New data is already included in the ENA on a continuous basis and distributed daily from our browser, FTP and RESTful API services. The key change is that we will no longer make an additional separate quarterly release of the assembled/annotated subset of sequences. We will focus our resources on further developing and supporting our continuous distribution presentation products.

As part of the release retirement we will no longer be creating cumulative FTP files in the FTP update folders (e.g. http://ftp.ebi.ac.uk/pub/databases/ena/sequence/update/). These cumulative files tracked daily changes in between release cycles and thus cannot continue to be produced sustainably. Release 143 will be the last available in the release folder (available here once released http://ftp.ebi.ac.uk/pub/databases/ena/sequence/release/), the update folder will be removed after this last release. Set based sequences have already been removed from the release and will continue to be added to the FTP in their corresponding folders (e.g. http://ftp.ebi.ac.uk/pub/databases/ena/wgs/public/).

After the final release in March 2020 we will be merging the '_release' and '_update' data types for sequence, coding and non-coding. So the data types'sequence_release' and 'sequence_update' will be replaced with the data type 'sequence'. This affects users of our API and browser advanced search services, you will need to use the updated data type end points. The new data types will be available in parallel ahead of the switchover, so we advise switching ahead of March 2020.

The following guide has been created to assist users in moving away from the release. This guide outlines accessing assembled/annotated sequences, guidance on how to identify data based on a last updated timestamp and advice for establishing your own mirroring procedures using our portfolio of other access services. 

Accessing assembled/annotated sequences
=======================================
..Edit if we are to discontinue FTP, following resolution of meeting about continuation  of this service.
Assembled/annotated sequences can be obtained from our continuous daily distribution resources, with API, FTP and web browser-based options. For most use cases we would recommend the ENA Browser API as it provides the greatest specificity and flexibility for obtaining a tailored dataset of assembled/annotated sequences for your requirements.

ENA API
-------
Assembled/annotated sequences can be identified and downloaded with our `ENA Browser API <https://www.ebi.ac.uk/ena/browser/api/>`_. The https API Swagger interface provides documentation on the endpoints, expected usage and errors.

Example of obtaining a single record by accession:
In EMBL format:

.. code:: curl
curl -X GET "https://www.ebi.ac.uk/ena/browser/api/embl/BN000065?download=true&lineLimit=0" -H "accept: text/plain"

In FASTA format

.. code:: curl
curl -X GET "https://www.ebi.ac.uk/ena/browser/api/fasta/BN000065?download=true&lineLimit=0" -H "accept: text/plain"

..Update the data type to sequence in below examples once DCP-2172 is complete
The ENA Browser API also allows the user to conduct a search for multiple Assembled/annotated sequences records and download them. In this example searching the sequence data type for human data distributed or updated since 19th August 2019:
In EMBL format

.. code:: wget
wget 'https://www.ebi.ac.uk/ena/browser/api/embl/search?result=sequence_update&query=tax_eq(9606)%20AND%20last_updated%3E%3D2019-08-18&limit=5' -O embl.txt

or

.. code:: curl
curl 'https://www.ebi.ac.uk/ena/browser/api/embl/search?result=sequence_update&query=tax_eq(9606)%20AND%20last_updated%3E%3D2019-08-18&limit=5' -o embl.txt

In FASTA format

.. code:: wget
wget 'https://www.ebi.ac.uk/ena/browser/api/fasta/search?result=sequence_update&query=tax_eq(9606)%20AND%20last_updated%3E%3D2019-08-18&limit=5' -O fasta.txt

or

.. code:: curl
curl 'https://www.ebi.ac.uk/ena/browser/api/fasta/search?result=sequence_update&query=tax_eq(9606)%20AND%20last_updated%3C%3D2019-08-18&limit=5' -o fasta.txt

We have added limits to the above examples to only return 5 records, remove this under normal use. You can search using the sequence, coding or non-coding data type endpoints. In general when using the API search it is important to be as specific as possible with your query to save on downloading sequences that you do not require.

.. read current release notes on data types to help here.

..Edit if we are to discontinue FTP, following resolution of meeting about continuation of this service.
ENA FTP
-------
Alternatively assembled/annotated sequence files our distributed daily to the `ENA FTP service <http://ftp.ebi.ac.uk/pub/databases/ena/sequence/>`_. 

The release folders, for example the sequence release folder (http://ftp.ebi.ac.uk/pub/databases/ena/sequence/release/) will contain the final release 143 made in March 2020.

..how to download distributed files, if we continue this service.
..mention aspera download as alternative for large downloads as more stable?

ENA Browser
-----------
For the majority of use cases we would recommend utilising the `ENA Browser API <https://www.ebi.ac.uk/ena/browser/api/>`_ for obtaining assembled/annotated sequences, however these are also available to search and download from the `ENA browser <https://www.ebi.ac.uk/ena/browser/home>`_. The advanced search service documented here is also useful for assistance with constructing complex API queries, particularly if using the graphical interface to construct the query and then using the "Copy Curl Request" button.

The `ENA browser <https://www.ebi.ac.uk/ena/browser/home>`_ provides direct access to sequences by accession, with subsequent option for download in EMBL (text) or FASTA format, for example see https://www.ebi.ac.uk/ena/browser/view/BN000065

The `ENA browser <https://www.ebi.ac.uk/ena/browser/home>`_ also provides an `ENA advanced search <https://www.ebi.ac.uk/ena/browser/advanced-search>`_ for searching for appropriate assembled/annotated sequences for download.

Detailed guidance on the usage of advanced search is available in `our advanced search documentation <https://ena-browser-docs.readthedocs.io/en/latest/browser/search/advanced.html>`_, but briefly to obtain assembled/annotated sequences using this service:
1. Start an advanced search at https://www.ebi.ac.uk/ena/browser/advanced-search
1. Select an assembled/annotated sequence data type such as 'sequence', 'coding' or 'non-coding'.
2. Recommend that you be as specific as possible with constructing a query to limit the resulting dataset to your needs from the available filters. Key filters include:
  - limiting by date. Database record -> last updated
  - taxon. Taxonomy and related -> NCBI taxonomy.
3. (Optional) You can also use inclusion and exclusion lists of accessions, alter the returned result fields and limit the number of records returned.
4. Once you have run your query you can select to download the data in either EMBL or FASTA format.
5. (Optional) If desired you can copy your query for use with the ENA APIs using the "Copy Curl Request" button.
6. (Optional) You can save this query for future use, by saving it to your Rulespace account using the 'Save To Rulespace' button, please refer to this `guide for more information <>`_.

How to identify data based on a last updated timestamp
======================================================
One common usage of the ENA release was to obtain all assembled/annotated sequence data changes since the last release, eother an entire release or by using the incremental update folders. This can be fully replicated in the `ENA Browser API <https://www.ebi.ac.uk/ena/browser/api/>`_ and `ENA Browser advanced search <https://www.ebi.ac.uk/ena/browser/advanced-search>`_  by using the "last_updated" query filter with a date value.

For the `ENA Browser API <https://www.ebi.ac.uk/ena/browser/api/>`_ search endpoint, you can include the 'last_updated' filter and provide a timestamp. This is essentially performing a less than equal search, so will provide all records that are new or have been updated from the provided date to the present day). It is recomended that you further customise the query with further filters (for example taxon or geographic) to avoid unesserily downloading data you do not require.

Example in FASTA format

.. code:: curl
curl 'https://www.ebi.ac.uk/ena/browser/api/fasta/search?result=sequence_update&query=last_updated%3E%3D2019-08-18&limit=5' -o fasta.txt

or in EMBL format

.. code:: curl
curl 'https://www.ebi.ac.uk/ena/browser/api/embl/search?result=sequence_update&query=last_updated%3E%3D2019-08-18&limit=5' -o embl.txt

You can also provide multiple timestamp filters to give a specific from and to date range, rather than all data to this date, for example data for the first 5 days of August 2019:

.. code:: curl
curl 'https://www.ebi.ac.uk/ena/browser/api/fasta/search?result=sequence_update&query=last_updated%3E%3D2019-08-01%20AND%20last_updated%3C%3D2019-08-05&limit=5' -o fasta.txt

We have added limits to the above examples to only return 5 records, remove this under normal use. You can search using the sequence, coding or non-coding data type endpoints. In general when using the API search it is important to be as specific as possible with your query to save on downloading sequences that you do not require.

.. Give link for more information on API when DCP-2176 is complete

For the `ENA Browser advanced search <https://www.ebi.ac.uk/ena/browser/advanced-search>`_ the 'last_updated' filter can be included in your query. It is located in the Database record filter section.

Establishing your own mirroring procedures
==========================================
.. Use API or advanced search to create a query with a to and from date.

..Optional, Start portal API to get accessions. If you customise the field output make sure you include sequence version.

..You can then get them from browser API.

..BUT more efficient to rerun query on browser API. more efficient.

..Importantly record the timestamp from when you run the current query and store this so that you can use it for your next update. Obviously you can now pick an update frequency that most suits your use case, by 

..If you are wanting to establish 

..So if you want a list of everything, use the portal API report. Same query against discovery API to get list of accessions, then same query against browser API to get flat files.

..Note make sure you run the query direct on 

..The reason you generate the report is that if you repeat the same search at a later date you may get different results because some records may have been updated or supressed. 

..The important for your users is to provide the report you generated earlier, they can then get a better reconstruction of the same dataset as it will contain supressed records. Killed records can never be retrieved.

..For large downloads we would advise parallel downloads, instructions on how to do this.

..If you need to resume a download, we currently would recommend using a grep to calculate how many you got, show instructions, and then use offset, please be aware data may have changed in between the call.

.. Describe new endpoint that will tell you if any records in report file have been updated supressed or killed since it was generated.

.. Describe how you can use the report to get the exact same versions as the mirror download

.. example of a query with a to and from date

.. State that it is better to be very specific with the query for what is actually required for your release, if you only need a certain data type, data from a certain taxon or from a particular region then you should limit this in your query, instructions for constructing queries here.


.. Comment that Rulespace can be used to save a complex query for repeated use

.. Comment that we may establish partitions for users depending on requirements.

.. Give link for more information on any APIs or tech used above


More information resources
==========================
Further documentation on the above services is available in their respective documentation:
- `ENA Discovery Portal API documentation <https://www.ebi.ac.uk/ena/portal/api/doc>`_
- `ENA Browser documentation <https://ena-browser-docs.readthedocs.io/en/latest/>`_

Further assistance
==================
If you currently rely on any aspect of the separate assembled/annotated sequence release process for your work or resource, and cannot switch to one of our continuous distribution processes outlined above, please feel free to contact us to discuss your requirements. 

In your query please list what features you utilised from the release process. We can discuss your requirements and determine how we might support your use case through one of our existing services or collaborate on an adapted or novel solution. Contacting us promptly with your requirements will allow us to ensure adequate time and resources to collaborate on a solution.
 
Please contact us with your questions or concerns at datasubs@ebi.ac.uk with the subject ‘ENA release retirement’.



Spot an edit or improvement to this page? Please report it using our `ENA Support Service <https://www.ebi.ac.uk/ena/browser/support>`_ quoting the URL of this page in your query. Alternatively submit a pull request with your proposed text change to the `Readthedocs Browser GitHub <https://github.com/enasequence/ena-browser-documentation>`_.
..consider update to specific URL for this page
