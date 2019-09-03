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

Organisation of a Project in ENA
--------------------------------

When data is submitted to the archive, the data submitter establishes relationships 
between each record in a research project following the ENA metadata model:

.. image:: images/metadata-model.png

This is so someone viewing the data can easily navigate between the records. 
This makes it easy to explore the data generated from biological samples which were 
sequenced/analysed within the same research project.

Cross-references
----------------

From this tab you can also see any links from the record out to external data resources 
that have used or generate these records as part of their services. These links are generated 
as part of ENA's cross-reference service and so only show data from resources that are 
registered with us. You can see more details on what services are 
registered `here <https://www.ebi.ac.uk/ena/browser/xref>`_.

*Note: This view only gives a view of the associated records submitted as part of the 
originally submitted research project and any registered cross-references. For a view 
showing all ENA records which are associated with this record (including any other 
links to this record within other ENA submission projects), you can see this in the Portal 
Links tab (available for Project, Sample and Taxon records).*

Read Files
==========

Display and download any associated raw read files.

You can download a Report of all the data displayed in the table or download files selected 
from the table. To download all files in the column, click the download icon in the table 
header.

To choose additional metadata to add to the table display and report, use the 'Show selected 
columns' expandable menu.

*Note: You can also download files from ENA using `enaBrowserTools <https://github.com/enasequence/enaBrowserTools>`_. *


Analysis Files
==============

Display and download any associated analysis files.

You can download a Report of all the data displayed in the table or download files selected 
from the table. To download all files in the column, click the download icon in the table 
header.

To choose additional metadata to add to the table display and report, use the 'Show selected 
columns' expandable menu.

*Note: You can also download files from ENA using `enaBrowserTools <https://github.com/enasequence/enaBrowserTools>`_. *

Publications
============

Explore publications that either cite the record or document the research 
where the record was generated.

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

This view provides a summary of all data associated with this record. Any submission in 
ENA that is associated with this record is available here.

This view is only available for three ENA record types:

**Study**: Here you can find all components of the project including any sequence or 
assembly records associated with the project.

**Sample**: Here you can find all sequencing records or analyses associated with the 
sample including assembly or sequence records. This view shows any third party uses 
of the sequencing data registered with ENA.

**Taxon**: Here you can see a summary of all ENA records registered with that particular 
taxon. This view also shows a summary of any records registered with descendant taxa.

Tax Tree
========

Here you can view the full tax tree of this taxon record.

From this view you can access all taxon records within this tax tree and explore ENA 
records that are registered with related taxa.

Click the arrows to expand the tree and explore the full lineage of the taxon.

Assembly Versions
=================

If this assembly has been updated, you can view the past assembly versions here.


Assembly Statistics
===================

Assembly statistics are generated for all assemblies submitted to INSDC.

**Total Length** (total sequence length) - total length of all top-level sequences.

**Ungapped Length** (total ungapped length) - total length of all top-level sequences 
ignoring gaps. Any stretch of 10 or more Ns in a sequence is treated like a gap.

**Chromosomes & Plasmids** (total number of chromosomes and plasmids) - total number 
of chromosomes, organelle genomes, and plasmids in the assembly.

**Spanned Gaps** - total number of gaps between contigs/scaffolds.

**Unspanned Gaps** - total number of unspanned gaps between scaffolds.

**Regions/Patches/Alternative Loci** - (number of regions with alternate loci or 
patches) - number of genomic regions that contain one or more alternate loci or 
patch scaffolds.

**Scaffolds** (number of scaffolds) - number of scaffolds including placed, 
unlocalized, unplaced, alternate loci and patch scaffolds.

**Scaffold N50** - length such that scaffolds of this length or longer include 
half the bases of the assembly.

**Contigs** (number of contigs) - total number of sequence contigs in the assembly. 
Any stretch of 10 or more Ns in a sequence is treated as a gap between two contigs 
in a scaffold when counting contigs and calculating contig N50 & L50 values.

**Contig N50** - length such that sequence contigs of this length or longer include 
half the bases of the assembly. 

Chromosomes
===========

When an assembly is is declared as assembled to full chromosomal level on 
submission, chromosome sequences are generated for each chromosome submitted 
in the assembly.
 
These chromosomes are available as individual sequence records and can be 
explored in full here.

BlobToolKit
===========

*help section coming soon*

Checklist Fields
================

Sample Checklists are lists of fields that are required/recommended to be used 
during registration to describe samples (depending on the type of sample).

Explore the mandatory, recommended and optional fields defined as part of this 
checklist.

You can filter these fields further by requirement or by keywords in the field 
name or description.

In some cases, fields can be restricted by regular expression, a list of text 
choices, by valid taxonomy or by valid ontology terms.
