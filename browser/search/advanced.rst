===============
Advanced Search
===============

Introduction
============

Customise your own search query and retrieve a set of ENA records tailored to your 
search criteria.

All searches are performed against a subset of the archive specified by 
the *Data type* you choose to search against. You can then build your search 
query to specify what data you are looking for and select what fields you want to 
retrieve from your search. There are additional options to include/exclude specific  
datasets as well as filter the number of results you wish to return.

If you intend to repeat the same search at a later date, you can save this 
as a Rule using `Rulespace <https://www.ebi.ac.uk/ena/browser/rulespace>`_. If you 
want to access the same data programmatically, you can copy the produced curl request and run 
this yourself against the `ENA Portal API <https://www.ebi.ac.uk/ena/portal/api/>`_.

Data Types
==========

Each data type is a subset of the data and metadata held within the ENA 
(e.g. the read_study datatype contains all studies that hold raw reads).

You must specify which datatype you wish to search across before you can 
narrow down your search results with any additional criteria. Hover over 
the data type options for more information on what each data type holds.

Search Query
============

To build a query you need to create a list of rules that the resulting 
data sets should be restricted to.

This is done by clicking any relevant metadata types you would like to 
restrict (listed as buttons on the left) then selecting the relevant filters 
and specifying the desired restrictions for those:

.. image:: images/example-tax-filter.png

When specifying taxonomy in your search, you can include all subordinate taxa 
within that tax tree and when searching by geographical range you can 
interactively drag the box or circle over the desired region to automatically fill out  
the location range.

These rules can be grouped and nested within AND or OR logical statements. 
For example, a query for *all metagenomic analyses where the sample was 
collected after 01 Jan 2019 AND the environmental material is either dental OR 
saliva* would look as follows:

.. image:: images/example-query.png

Inclusion/Exclusion of datasets
===============================

If there are any known public datasets that do or do not fit the criteria 
you have specified that you wish to include or exclude from the results, 
you can list the accessions in a comma separated list here (with no spaces).

Return Fields
=============

By default, you will receive the accession and description/title
of the main datatype you are searching against. If you wish to customise the 
metadata which your search will return, you can manually select your search 
return fields from a list of all indexed fields for the specified datatype.

Select and order fields
-----------------------

To select fields you would like returned from your search, drag across any 
desired fields from the **Available Fields** list to the **Selected Fields** 
list. Alternatively, use the arrow buttons in the middle to move fields across 
from one list to the other.

The order of the **Selected Fields** list will define the order that you 
receive those metadata from your search. To specify the return order of these 
fields, you can drag and drop these into the desired order.

Field sets
----------

Field sets are a pre-defined set of fields that can be returned together and 
are available for some data types. For example, for the analysis datatype, 
you can toggle the 'Submitted Files' field set which can be used to return 
all relavent fields relating to the original set of submitted files (e.g. 
this set includes the aspera, ftp and galaxy links for the submitted files, 
the size of the files (in bytes) and the files' md5 checksums).

Data Filters
============

Offset
------

You can specify an offset for the number of records you would like to skip
from the beginning of your search. This can be used to fetch the results 
available beyond the maximum number of records that can be fetched in one go
(100 000).

If you do not wish to skip any records, you can leave this field blank or 
enter an offset of '0'.

Limit
-----

You can specify a data limit for the maximum number of records you would like 
to retrieve from your search (up to a maximum of 100 000).

If you wish to fetch the full result set, leave this field blank or enter '0'. 
The browser table display will only show up to 100 000 results but for large 
datasets, you can see all the results if you download the report or copy and run 
the curl request.

Download results - metadata
===========================

Download results as an XML
--------------------------

This feature allows you to download all the ENA metadata objects that resulted 
from your search in XML format.

This will download **all** the metadata for each object in the standard ENA XML 
format (the same XML format that is used for data submission and for data to be 
displayed in the browser). If you wish to only download the fields returned that 
were specified in your search, use one of the **Download report** options 
(JSON or TSV).

Download results report
-----------------------

This feature allows you to download all the results from your search in the 
format of a JSON or TSV file. Any data filters set by you will apply here. If you 
specified to return the full set, you can download all the results here.

Download results - files
========================

Pre-Conditions
--------------

To see file download columns in your results, you have to search against either 
the analysis or read_run data types and select the relevant fields that end with '_ftp'. 

For example: 

**Data Type** = analysis and **fields** = submitted_ftp

**Data Type** = read_run and **fields** = fastq_ftp / sra_ftp / submitted_ftp

Download files
--------------

You can download the data files resulting from your search in a number of ways:

1. You can download a single file directly from its link in the table.

2. You can choose a selection of files to download using the available check boxes. 
   Once you are happy with the selection, you can use the 'Download selected files' 
   button at the top of the table to download these. If you wish to download these in 
   a single ZIP format, you can use the 'Download files as ZIP' toggle switch.
   
3. You can download all files resulting from your search by clicking the icon 
   in the table collumn header:
   
   .. image:: images/download-all.png
   
*Please note: When downloading all files resulting from your search, if there 
are large file sizes then there is a risk of incomplete download.*

If you wish to exclude any files from your search before you download the set 
of resulting files, you can go back and define these in the "Exclude Accessions" 
stage then repeat the search. 

