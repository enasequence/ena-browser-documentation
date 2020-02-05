==================
GSC MIxS Standards
==================

The MIxS is a unified standard developed by the `Genomic Standards Consortium (GSC) <http://gensc.org/>`_ for reporting
of minimum information about any (x) nucleotide sequence
(`Yilmaz et al, 2011 <http://www.nature.com/nbt/journal/v29/n5/full/nbt.1823.html>`_).

A number of environmental checklists that extend upon MIxS were developed by environment-specific community
experts. These provide extensive range of environmental and epidemiological contextual data fields for accurate
and consistent description of the sequenced sample, its environment and sequencing experiments performed with the sample.

MIxS is made up of a number of mandatory core terms which are shared between the checklists to improve interoperability
between different sample types.The individual MIxS checklists are extensions of these core terms. ENA has implemented
the MIxS core terms as part of all the MIxS sample checklists available for submission.

ENA Sample Fields for Core MIxS terms
=====================================

+------------------------------------------+-----------------------------------------------------------------+
| **Sample Field**                         | **Description**                                                 |
+------------------------------------------+-----------------------------------------------------------------+
| investigation type                       | | Nucleic Acid Sequence Report is the root element of all MIxS  |
|                                          | | compliant reports as standardised by Genomic Standards        |
|                                          | | Consortium.                                                   |
+------------------------------------------+-----------------------------------------------------------------+
| project name                             | Name of the project within which the sequencing was organized.  |
+------------------------------------------+-----------------------------------------------------------------+
| geographic location (latitude)           | | The geographical origin of the sample as defined by latitude. |
|                                          | | The values should be reported in decimal degrees and in WGS84 |
|                                          | | system.                                                       |
+------------------------------------------+-----------------------------------------------------------------+
| geographic location (longitude)          | | The geographical origin of the sample as defined by           |
|                                          | | longitude. The values should be reported in decimal degrees   |
|                                          | | and in WGS84 system.                                          |
+------------------------------------------+-----------------------------------------------------------------+
| geographic location (country and/or sea) | | The geographical origin of the sample as defined by the       |
|                                          | | country or sea. Country or sea names should be chosen from    |
|                                          | | the INSDC country list (http://insdc.org/country.html).       |
+------------------------------------------+-----------------------------------------------------------------+
| collection date                          | | The date of sampling, either as an instance (single point in  |
|                                          | | time) or interval. In case no exact time is available, the    |
|                                          | | date/time can be right truncated i.e. all of these are valid  |
|                                          | | ISO8601 compliant times: 2008-01-23T19:23:10+00:00;           |
|                                          | | 2008-01-23T19:23:10; 2008-01-23; 2008-01; 2008.               |
+------------------------------------------+-----------------------------------------------------------------+
| environment (biome)                      | | Biomes are defined based on factors such as plant structures, |
|                                          | | leaf types, plant spacing, and other factors like climate.    |
|                                          | | Biome should be treated as the descriptor of the broad        |
|                                          | | ecological context of a sample. Examples include: desert,     |
|                                          | | taiga, deciduous woodland, or coral reef. EnvO (v 2013-06-14) |
|                                          | | terms can be found via the link:                              |
|                                          | | www.environmentontology.org/Browse-EnvO                       |
+------------------------------------------+-----------------------------------------------------------------+
| environment (feature)                    | | Environmental feature level includes geographic environmental |
|                                          | | features. Compared to biome, feature is a descriptor of the   |
|                                          | | more local environment. Examples include: harbor, cliff, or   |
|                                          | | lake. EnvO (v 2013-06-14) terms can be found via the link:    |
|                                          | | www.environmentontology.org/Browse-EnvO                       |
+------------------------------------------+-----------------------------------------------------------------+
| environment (material)                   | | The environmental material level refers to the material that  |
|                                          | | was displaced by the sample, or material in which a sample    |
|                                          | | was embedded, prior to the sampling event. Environmental      |
|                                          | | material terms are generally mass nouns. Examples include:    |
|                                          | | air, soil, or water. EnvO (v 2013-06-14) terms can be found   |
|                                          | | via the link: www.environmentontology.org/Browse-EnvO         |
+------------------------------------------+-----------------------------------------------------------------+
| sequencing method                        | | Sequencing method used; e.g. Sanger, pyrosequencing, ABI-solid|
+------------------------------------------+-----------------------------------------------------------------+
