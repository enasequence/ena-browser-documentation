======================================
Accessing ENA Content Programmatically
======================================

The European Nucleotide provides a number of REST APIs for programmatic access to the archive. These enable programmatic
access to the functionality of the ENA Advanced Search as well as direct download of ENA
records and access to associated files.

Data retrieval and download
===========================

The ENA Browser is backed by the `ENA Browser API <https://www.ebi.ac.uk/ena/browser/api/>`_ which can be used to
retrieve public ENA records in XML, flat file or fasta format.

Explore some worked through examples of how to use the ENA Browser API in our
`retrieval tutorial <>`_.

Search
======

The ENA Advanced search is backed by the `ENA Discovery Portal API <https://www.ebi.ac.uk/ena/portal/api/>`_ which can
be used to perform warehouse searches of the archive and specify which metadata to return. These searches can be
performed in combination with the `ENA Browser API <https://www.ebi.ac.uk/ena/browser/api/>`_ to download all records
resulting from a search. Using the two APIs together gives the full functionality of the
`ENA Advanced Search <https://www.ebi.ac.uk/ena/browser/advanced-search>`_.

Related external records and publications can also be explored and searched by programmatically accessing the
`ENA Cross Reference Service <https://www.ebi.ac.uk/ena/xref/rest/>`_.

For some worked through examples of how to perform some advanced searches programmatically, see our
`retrieval tutorials <>`_.

Explore Taxonomy and Related Records
====================================

All sample records in ENA have taxonomic assignment as a result, the majority of records stored within the archive
can be searched based on their taxonomy. The ENA has a REST API for access to taxonomic information (e.g. lineage and
rank) so taxonomic records can be explored programmatically.

For tutorials on taxon based searches or API usage, see our `retrieval tutorials <>`_.

Sequence similarity search
==========================

EBI's central NCBI BLAST service can be accessed via
`REST and SOAP <https://www.ebi.ac.uk/seqdb/confluence/display/JDSAT/Job+Dispatcher+Sequence+Analysis+Tools+Home>`_.
For usage details and parameter options, see the
`NCBI BLAST+ documentation <https://www.ebi.ac.uk/seqdb/confluence/pages/viewpage.action?pageId=94147939>`_.
