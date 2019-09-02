===================
Viewing ENA Records
===================

ENA Records
===========

You can view any public ENA records using their Accession (unique identifier) or 
as the result of a search.

Exploring an ENA record
-----------------------

.. image:: images/record-guide.png

All records have a selection of standard, indexed metadata which tells you about the 
database entry. For example, where it is submitted, basic information on the record's 
title and description etc.

For more information about this record, you can click *Show More* to access additional data 
that the data submitter has provided.

To explore a record further, you can use the navigation box in the top right of the view 
to show/hide different additional subsections of information.

This gives you access to any other associated data, such as if a project has any data 
files or publications associated with it.

Any links that looks like *accessions* (a series of letters then numbers) will take you 
to an associated record.

An ENA record can be one of the following types:

Record types
------------

+-----------------------+---------------------------------------------+------------------------+
| **Record Type**       | **Description**                             | **Example accessions** |
+-----------------------+---------------------------------------------+------------------------+
| Projects/Studies      | | Contains information on a biological      | PRJEB12345/ERP123456   |
|                       | | research project. This holds all the data |                        |
|                       | | generated as part of this research.       |                        |
+-----------------------+---------------------------------------------+------------------------+
| Samples               | | Represents biological samples collected   | ERS123456/SAMEA123456  |
|                       | | and sequenced in real life                |                        |
+-----------------------+---------------------------------------------+------------------------+
| Runs/Experiments      | Hold raw read files and sequencing methods  | ERR123456/ERX123456    |
+-----------------------+---------------------------------------------+------------------------+
| Analyses              | | Hold results files of analyses performed  | ERZ123456              |
|                       | | on sequencing data and analysis methods   |                        |
+-----------------------+---------------------------------------------+------------------------+
| WGS contig set        | | Hold Whole Genome Sequencing contig sets  |  ABCD01000000.1        |
|                       | | generated as part of a genome assembly.   |                        |
+-----------------------+---------------------------------------------+------------------------+
| Assemblies            | | Represents an entire genome assembly and  | GCA_123456789.1        |
|                       | | holds any contig sets or sequence records |                        |
|                       | | generated as part of the assembly         |                        |
+-----------------------+---------------------------------------------+------------------------+
| | Assembled/Annotated | | Any sequence records from coding or       | A12345.1               | 
| | Sequences           | | non-coding regions to full assembled      |                        |
|                       | | chromosomes                               |                        |
+-----------------------+---------------------------------------------+------------------------+
| Taxon                 | | The sequenced organism or metagenome of a | Taxon:9606             |
|                       | | sample                                    |                        |
+-----------------------+---------------------------------------------+------------------------+
| Sample Checklist      | | The checklist of metadata that the sample | ERC000012              |
|                       | | was registered with                       |                        |
+-----------------------+---------------------------------------------+------------------------+

Navigation and Cross References
===============================

From here you can navigate through all associated records that were submitted within the same 
submission Project.

Organisation of a project in ENA
--------------------------------

.. image:: images/metadata-model.png

When a user submits data to the archive, they establish relationships between the records they 
submit so someone viewing the data can easily navigate between the data types. This makes it easy 
to explore the data generated from biological samples which were sequenced/analysed within the same 
research project.

This view gives a snapshot of the contents of the originally submitted research project 
and any associated cross-references. For a view showing *all* records held in ENA which 
are associated with this record (including any third-part analyses), you can see this in the 
Portal Links tab (available for Project, Sample and Taxon records).

Cross-references
----------------

From this tab you can also see any links from the record out to external data resources 
that have used or generate these data which have registered with us as part of ENA's 
cross-reference service.

Read Files
==========

Display and download any associated raw read files.

You can download a Report of all the data displayed in the table or download files selected 
from the table. To download all files in the column, click the download icon in the table 
header.

To choose additional metadata to add to the table display and report, use the 'Show selected 
columns' expandable menu.


Analysis Files
==============

Display and download any associated analysis files.

You can download a Report of all the data displayed in the table or download files selected 
from the table. To download all files in the column, click the download icon in the table 
header.

To choose additional metadata to add to the table display and report, use the 'Show selected 
columns' expandable menu.


Publications
============

Explore publications that either cite the record or where the record was generated.

This view provides links to the DOI or in some cases, a direct link to the PDF or article in 
Europe PMC.


Component Projects
==================

In the case of an **Umbrella Project** (a project which is used to group many related 
sub-projects) there is the option to explore its Component Projects.

Component projects are the same as other project records in ENA but are grouped under one 
'umbrella' meaning they will often have the same research motivation and will often represent 
a collaborative research effort.

Portal Links
============
*coming soon*


Tax Tree
========
*coming soon*


Sequence Versions
=================
*coming soon*


Assembly Versions
=================
*coming soon*


Assembly Statistics
===================
*coming soon*


Chromosomes
===========

*coming soon*


BlobToolKit
===========

*coming soon*
