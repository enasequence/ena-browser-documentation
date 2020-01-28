=======================
CRAM Reference Registry
=======================

The CRAM reference registry provides access to reference sequences used in CRAM files.
Retrieval of reference sequences from the CRAM reference registry is provided by MD5 or
SHA1 checksum through the endpoints documented in the `CRAM reference registry API <https://www.ebi.ac.uk/ena/cram/>`_.

CRAM Format
===========

CRAM is a sequencing read file format that is highly space efficient by using reference-based compression of
sequence data and offers both lossless and lossy modes of compression. The format specification for CRAM is
maintained by the `Global Alliance for Genomics and Health (GA4GH) <https://www.ga4gh.org/cram/>`_
whose members provide multiple implementations and coordinate future specification changes.

The CRAM reference registry is used by GA4GH `Samtools <http://www.htslib.org/>`_.

CRAM Reference Registry reverse proxy
=====================================

To reduce network traffic originating from the use of the CRAM Reference Registry we recommend using locally
cached reference sequences. In addition to local caches supported by Samtools, it is possible to cache sequences
using an HTTP proxy.

Please see our tutorial for how to set up a local cache using Squid HTTP proxy on
Linux `here <https://ena-docs.readthedocs.io/en/latest/retrieval/programmatic-access/cram-reference-cache.html>`_.
