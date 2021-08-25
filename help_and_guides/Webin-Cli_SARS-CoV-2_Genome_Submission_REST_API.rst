Webin SARS-CoV-2 Genome Submission Web API
==========================================

Introduction
------------

Webin SARS-CoV-2 Genome Submission Web API is a JSON based service used
to submit SARS-CoV-2 genome assemblies to the European Nucleotide
Archive (ENA). For further information on submitting SARS-CoV-2 genomes,
see our `SARS-CoV-2 Submission
Instructions <https://ena-browser-docs.readthedocs.io/en/latest/help_and_guides/sars-cov-2-submissions.html#submitting-assemblies>`__.

There are two submission services: 

- `Test service <https://wwwdev.ebi.ac.uk/ena/submit/webin-cli>`__ 

- `Production service <https://www.ebi.ac.uk/ena/submit/webin-cli>`__

The test service is recreated from the full content of the production
service every day at 03.00 GMT/BST. Therefore, any submissions made to
the test service will be removed by the following day.

When you are using the test service the receipt will contain the
following message:

.. code:: sh

    "info":["This submission is a TEST submission and will be discarded within 24 hours"] 

Service endpoints
-----------------

This service has two endpoints.

1. Submit SARS-CoV-2 genomes:

-  Test service :
   https://wwwdev.ebi.ac.uk/ena/submit/webin-cli/api/v1/genome/covid-19
-  Production service:
   https://www.ebi.ac.uk/ena/submit/webin-cli/api/v1/genome/covid-19

2. Validate but do NOT submit SARS-CoV-2 genomes:

-  Test service:
   https://wwwdev.ebi.ac.uk/ena/submit/webin-cli/api/v1/genome/covid-19/validate
-  Production service:
   https://www.ebi.ac.uk/ena/submit/webin-cli/api/v1/genome/covid-19/validate

The second endpoint can be used to test if a SARS-CoV-2 genome is valid
without submitting it into ENA.

Submission process
------------------

Pre-register Study and Sample
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Each submission must be associated with a pre-registered study and a
sample.

Please find instruction on how to register studies and samples below: -
`Register a
Study <https://ena-docs.readthedocs.io/en/latest/submit/study.html>`__ -
`Register a
Sample <https://ena-docs.readthedocs.io/en/latest/submit/samples.html>`__

Authentication
~~~~~~~~~~~~~~

This service supports basic HTTP authentication only. Please use your
Webin submission account name (Webin-N) as the username with your Webin
submission account password. New Webin submission accounts can be
registered in `Webin
Portal <https://www.ebi.ac.uk/ena/submit/webin/>`__.

When using curl the username and password are provided using the ``-u``
option:

.. code:: sh

    curl -X 'POST'  -u Webin-N:password  'https://wwwdev.ebi.ac.uk/ena/submit/webin-cli...

JSON payload
~~~~~~~~~~~~

Both the submission and validation endpoints require a JSON payload in
the HTTP body. Below, mandatory fields are marked by \* and field
descriptions start with #:

.. code:: sh

    {
      *"name": "string", # Unique name for the assembly within the Webin submission account
      *"study": "string", # Study accession number or unique name (alias)
      *"sample": "string", # Sample accession number or unique name (alias)
      *"coverage": "number", # The estimated depth of sequencing coverage
      *"program": "string", # The assembly program
      *"platform": "string", # The sequencing platform
      *"sequence": "string", # The assembled genome sequence
      "description": "string", # Free text description of the genome assembly
      "minGapLength": "integer", # Minimum length of consecutive Ns to be considered a gap
      "moleculeType": "genomic DNA",
      "runRef": "string", # Run accession number containing the raw reads associated with this genome assembly
      "tpa": boolean, # Set to true for third party assemblies (by default false)
      "authors": "string" # List of authors associated with this genome assembly (by default authors of the submission account will be used)
      "address": "string", # Address where this genome was assembled (by default addrss of the submission account will be used)
      "submissionTool": "string", # Submission tool that called this endpoint
      "submissionToolVersion": "string"  # Submission tool version that called this endpoint
    }

***Example***

.. code:: sh

    {
      "name": "Test",
      "study": "PRJEB46468",
      "sample": "ERS6670887",
      "coverage": 100,
      "program": " Minimap2",
      "platform": " OXFORD_NANOPORE ",
      "sequence": "CTCTCGATCGATCAAATTTGGGTTTAAGGCCCTTGGAATT",
      "description": "This is a test submission",
      "minGapLength": 1,
      "moleculeType": "genomic DNA",
      "authors": "EMBL-EBI",
      "address": "United Kingdom"
    }

Submission
~~~~~~~~~~

Example using curl
^^^^^^^^^^^^^^^^^^

.. code:: sh

    curl -X 'POST' -u Webin-N:password   \
      'https://wwwdev.ebi.ac.uk/ena/submit/webin-cli/api/v1/genome/covid-19' \
      -H 'accept: application/json' \
      -H 'Content-Type: application/json' \
      -d '{
      "name": "test_1",
      "study": "PRJEB46468",
      "sample": "ERS6670887",
      "coverage": 100,
      "program": "Ilumina",
      "platform": "Ilumina",
      "sequence": "CTCTCGATCGATCAAATTTGGGTTTAAGGCCCTTGGAATT",
      "description": "test",
      "minGapLength": 1,
      "moleculeType": "genomic DNA",
      "authors": "test",
      "address": "test"
    }'

Example using python
^^^^^^^^^^^^^^^^^^^^

.. code:: python

    import sys
    import requests
    import json

    data = [
        {
          "name": "test_1", "study": "PRJEB46811", "sample": "ERS7306048",
          "coverage": 100, "program": "Ilumina", "platform": "Ilumina",
          "sequence": "CTCTCGATCGATCAAATTTGGGTTTAAGGCCCTTGGAATT",
          "description": "test", "minGapLength": 1, "moleculeType": "genomic DNA",
          "tpa": False, "authors": "test", "address": "test"
        },
        {
          "name": "test_2", "study": "PRJEB46811", "sample": "ERS7306049",
          "coverage": 100, "program": "Ilumina", "platform": "Ilumina",
          "sequence": "CTCTCGATCGATCAAATTTGGGTTTAAGGCCCTTGGAATT",
          "description": "test", "minGapLength": 1, "moleculeType": "genomic DNA",
           "authors": "test", "address": "test"
        }
    ]

    ## Please remove /validate from the URL to submit the genome instead of just validating it
    server = "https://wwwdev.ebi.ac.uk/ena/submit/webin-cli/api/v1/genome/covid-19/validate"

    for sample in data:
        sample_json = json.dumps(sample)
        response = requests.post(
            server, headers={"accept":"application/json", "Content-Type":"application/json"}, 
            data=sample_json, auth=('Webin-XXXXXX', 'password')
        )
        status = response.status_code
        if status != 200:
            print("Bad REST call : {}".format(status))
            sys.exit(1)
        else:
            receipt = json.loads(response.content)
            print("{} : {}".format(sample['name'], receipt))

JSON response and HTTP status code
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

HTTP status code 200 indicates that the submission was successful. More
information is available from the JSON response returned in the response
body including the assigned accession number and any validation errors.

Please note that an accession will not be assigned when using the
``/validate`` endpoint.

HTTP status codes
^^^^^^^^^^^^^^^^^

+--------+-------------------------+
| Code   | Description             |
+========+=========================+
| 200    | OK                      |
+--------+-------------------------+
| 400    | Bad Request             |
+--------+-------------------------+
| 401    | Forbidden               |
+--------+-------------------------+
| 500    | Internal Server error   |
+--------+-------------------------+

JSON response body example: Successful test service submission
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code:: sh

    {
      "accession": "ERZ2881825",
      "alias": "webin-genome-test_1",
      "info": [
        "This submission is a TEST submission and will be discarded within 24 hours"
      ],
      "error": []
    }

JSON response body example: Successful production service submission
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code:: sh

    {
      "accession": "ERZ2881825",
      "alias": "webin-genome-test_1",
      "info": [],
      "error": []
    }

JSON response body example: Successful validation
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code:: sh

    {
      "accession": null,
      "alias": null,
      "info": [],
      "error": []
    }

JSON response body example: Failed validation
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Invalid molecule type:

.. code:: sh

    {
      "accession": null,
      "alias": null,
      "info": [],
      "error": [
        "ERROR: Invalid MOLECULETYPE field value: \"reads\". Valid values are: [genomic DNA, genomic RNA, viral cRNA]. [manifest file: /tmp/288f4f48-132e-4e90-bb56-5d8afe8af4c45476417061259693052/manifest.json, file name: /tmp/288f4f48-132e-4e90-bb56-5d8afe8af4c45476417061259693052/manifest.json, field: MOLECULETYPE, value: reads]"
      ]
    }


No study and sample found:

::

    {
      "accession": null,
      "alias": null,
      "info": [],
      "error": [
        "ERROR: Could not find study \"PRJEB46782\". The study must be owned by the submission account used for this submission or it must be private or temporarily suppressed and referenced by accession. Note that only a single study can be referenced. Unknown study PRJEB46782 or the study cannot be referenced by your submission account. Studies must be submitted before they can be referenced in the submission. [manifest file: /tmp/612ca908-39af-4b72-b9a4-f759bac7f1442135529880044742773/manifest.json, file name: /tmp/612ca908-39af-4b72-b9a4-f759bac7f1442135529880044742773/manifest.json, field: STUDY, value: PRJEB46782]"
      ]
    }

