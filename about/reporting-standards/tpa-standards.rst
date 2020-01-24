================
Third Party Data
================

Third PArty data (TPA) are submitted to the International Nucleotide Sequence Databases as part of the process of
publishing biological studies that include the assembly and/or annotation of existing INSDC reads and primary sequences.
Publicly accessible TPA data are therefore linked to a publication or publications that document the derivation of the
data supported by peer-reviewed scientific evidence.

All TPA records belong to one of these classes: **TPA:experimental**, **TPA:inferential**, **TPA:specialist_db**, or
**TPA:assembly**.

**TPA:experimental** describes records that include functional annotation derived at least in part from peer-reviewed
wet-lab experimental investigation.

**TPA:inferential** describes records that include functional annotation derived from peer-reviewed bioinformatic
investigation.

**TPA:specialist_db** describes records whose sequences are submitted from an existing authoritative public database
that is built using INSDC sequence data and is described in an accepted peer-reviewed publication. The existing
database is therefore recognized to be comprehensive, to have added value, and to be maintained long term.

**TPA:assembly** describes records reporting assembly or reassembly, for which the generation, whether it is purely
informatic or informed by experimentation, has been subject to peer review. Annotation may or may not be available
and does not require to be part of the peer review for this TPA class. A further requirement for TPA:assembly is
for submitters to provide a reference to the original SRA/ERA/DRA reads used for the third party assembly. For further
details on how to do this please contact the ENA Helpdesk or read the ENA submission documentation:
https://ena-docs.readthedocs.io/en/latest/ and search for RUN_REF. Note that referencing the original reads is a
mandatory requirement for TPA:assembly tier but recommended for primary assemblies.

TPA records are clearly labeled with keywords indicating their TPA status and their class. Constructed genomes where
no experimental evidence is presented (in **TPA:assembly**) are permitted to include only annotation relating to genes of
known function (as opposed to hypothetical proteins, for example). Submissions containing neither assembly information
nor annotation that has resulted from peer-reviewed in vivo, in vitro or in silico experimentation are not accepted in
TPA. The outputs of computational tools, feature identification algorithms, and homology search tools alone are not
sufficient for TPA.

TPA Submissions
===============

TPA submissions have to follow strict guidelines to ensure the original data generators are fairly acknowledged
and to link the data suitably with its source.

If your submission uses any third party data, please contact us via our
`support form <https://www.ebi.ac.uk/ena/browser/support>`_ and provide the details of your methods used to derive your
third party submission.
