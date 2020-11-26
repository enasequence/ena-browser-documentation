========================================================================
SARS-CoV-2 (Severe acute respiratory syndrome coronavirus 2) Submissions
========================================================================

Please see below for instructions on how to submit SARS-CoV-2 (Severe acute respiratory syndrome coronavirus 2) or COVID-19 related data. If you have any queries or require assistance with your submission please contact us at: virus-dataflow@ebi.ac.uk.

Registering Studies
===================
Data submissions to the ENA require that you register a study to contextualise and group your data. Details of how to do this can be found in our `Study Registration Guide <https://ena-docs.readthedocs.io/en/latest/submit/study.html>`_. Please ensure you describe your study adequately, as well as provide an informative title.

Registering Samples
===================
Having registered a study, please proceed to register your samples. These are metadata objects that describe the source biological material of your experiments. Following this, the sequence data can be registered (as described in later sections).

Instructions for sample registration can be found in our `Sample Registration Guide <https://ena-docs.readthedocs.io/en/latest/submit/samples.html.>`_. As part of this process, you must select a sample checklist to describe metadata. If you require any support regarding sample metadata, please contact virus-dataflow@ebi.ac.uk.

###Viral Samples
The most appropriate checklist for SARS-CoV-2 submissions is the “ENA virus pathogen reporting standard checklist” - `ERC000033 <https://www.ebi.ac.uk/ena/browser/view/ERC000033>`_. This presents 9 mandatory, 15 recommended and 11 optional fields (along with any additional user-defined fields).

Please use the organism name “Severe acute respiratory syndrome coronavirus 2” and taxonomic ID 2697049. It is recommended, as a minimum, that collection date and geographic location (e.g. country) are specified and sample capture status field is provided a value of ‘active surveillance in response to outbreak’.

###Metagenomic Samples
Data submissions which include metagenomic samples, should be registered with a relevant metagenome taxonomy - visit our FAQ on `Tips for Taxonomy <https://ena-docs.readthedocs.io/en/latest/faq/taxonomy.html#environmental-biome-level-taxonomy>`_ for more information. A few examples include human lung metagenome - `433733 <https://www.ebi.ac.uk/ena/browser/view/Taxon:433733>`_, human saliva metagenome - `1679718 <https://www.ebi.ac.uk/ena/browser/view/Taxon:1679718>`_, human tracheal metagenome - `1712573 <https://www.ebi.ac.uk/ena/browser/view/Taxon:1712573>`_ or human metagenome - `646099 <https://www.ebi.ac.uk/ena/browser/view/Taxon:646099>`_, among many others.

The most appropriate sample checklists depending on the source of your biological samples, are likely to include:
* GSC MIxS host associated (`ERC000013 <https://www.ebi.ac.uk/ena/browser/view/ERC000013>`_)
* GSC MIxS human associated (`ERC000014 <https://www.ebi.ac.uk/ena/browser/view/ERC000014>`_)

Visit our `ENA Sample Checklists <https://www.ebi.ac.uk/ena/browser/checklists>`_ page for a full listing of sample checklists.

When using the GSC MIxS checklists for your submission, please include the optional field ‘host disease status’ with a value of ‘COVID-19’.

###Other Sample Fields
If you have already submitted data to the GISAID database, a corresponding GISAID ID can be specified when using a sample checklist by creating a user-defined field named ‘GISAID Accession ID’.

Submitting Reads
================
After registering your study and samples, you can submit your read files along with experimental (library-related) metadata. See our `Read Submission Guide <https://ena-docs.readthedocs.io/en/latest/submit/reads.html>`_ for detailed instructions on submitting reads.

We encourage submissions to include information on specific protocols used for the experiment. This should be provided in the library description. This can be, for example, the name and/or URL to a specific protocol. View our listing of the available `full experimental metadata dictionaries <https://ena-docs.readthedocs.io/en/latest/submit/reads/webin-cli.html>`_.

Submitting Assemblies
=====================
If submitting assemblies, you must have registered a study and a sample beforehand. It is also advised that the associated read data is also submitted. For instructions on assembly submission view our `Assembly Submission Guide <https://ena-docs.readthedocs.io/en/latest/submit/assembly.html>`_.

Assemblies can only be submitted using `Webin-CLI <https://ena-docs.readthedocs.io/en/latest/submit/general-guide/webin-cli.html>`_, using `-context genome`.  During the process, you must define metadata in the `manifest file(s) <https://ena-docs.readthedocs.io/en/latest/submit/assembly/genome.html#manifest-files>`_. Please specify ‘COVID-19 outbreak’ as the ‘ASSEMBLY_TYPE’.

Any annotations, where provided, are captured according to `INSDC Feature Table Definitions <http://www.insdc.org/files/feature_table.html>`_.

In alignment with INSDC partners, COVID-19 assemblies will **not** be assigned a GCA accession. However, sequence accessions will continue to be assigned, alongside ERZ analysis accessions which are the point of access for the submitted file(s). For more details on accessioning, view our `Accessions Guide <https://ena-docs.readthedocs.io/en/latest/submit/general-guide/accessions.html>`_. To cite data, top-level project accessions (PRJ...) should be used as these are the most stable long-term accessions. View our `guide to cite data <https://ena-docs.readthedocs.io/en/latest/submit/general-guide/accessions.html#how-to-cite-your-ena-study>`_ for further details.

Submitting Targeted Sequences
=============================
If submitting targeted or annotated sequences, you must register a study as described above. See our `Targeted Sequence Submission Guide <https://ena-docs.readthedocs.io/en/latest/submit/sequence.html>`_ for submission instructions. When submitting annotated sequences, you must select an appropriate `Annotation Checklist <https://ena-docs.readthedocs.io/en/latest/submit/sequence/annotation-checklists.html>`_. There are several virus-specific annotation checklists, with “Single Viral CDS” the most appropriate for complete or partial coding sequences from a viral gene. If your sequences do not fit the annotation checklists above please contact us at virus-dataflow@ebi.ac.uk.

Any annotations, where provided, are captured according to `INSDC Feature Table Definitions <http://www.insdc.org/files/feature_table.html>`_.

If submitting single contig assemblies, or for any other support or issues around SARS-CoV-2 submissions please contact virus-dataflow@ebi.ac.uk.

Release of Data
===============
We recommend that submitted data is set to public as soon as possible to enable early presentation in `ENA <https://www.ebi.ac.uk/ena/browser/home>`_ and also on the `COVID-19 data platform <https://www.covid19dataportal.org/>`_. Users are responsible for releasing data they submit to ENA. This is done by setting an appropriate release date, as detailed in our `Data Release Policies <https://ena-docs.readthedocs.io/en/latest/faq/release.html#can-i-advance-postpone-the-release-date>`_.