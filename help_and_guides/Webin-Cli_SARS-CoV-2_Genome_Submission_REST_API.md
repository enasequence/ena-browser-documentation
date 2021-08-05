# Webin-Cli SARS-CoV-2 Genome Submission REST API
## Introduction

Webin-Cli Covid-19 Genome Submission API, is a JSON based service uses Webin-Cli REST to validate, upload and submit COVID-19 genomic assemblies to the European Nucleotide Archive (ENA). 
Webin-CLI is the only way to submit assembled genomes and transcriptomes.

There are two submission services. One for test submissions and another for production submissions:
#### Test Service
- Test service URL: https://wwwdev.ebi.ac.uk/ena/submit/webin-cli/swagger-ui/index.html?configUrl=/ena/submit/webin-cli/v3/api-docs/swagger-config#/Covid-19%20GenomeAPI

The test service is recreated from the full content of the production service every day at 03.00 GMT/BST. Therefore, any submissions made to the test service will be removed by the following day.

When you are using the test service the receipt will contain the following message:
```sh
"info":["This submission is a TEST submission and will be discarded within 24 hours"] 
```
#### Production Service 
- Production service URL: https://www.ebi.ac.uk/ena/submit/webin-cli/swagger-ui/index.html?configUrl=/ena/submit/webin-cli/v3/api-docs/swagger-config#/Covid-19%20GenomeAPI

## Submission process 
#### Pre-register Study and Sample
Each submission must be associated with a pre-registered study and a sample.
- [Register a Study](https://ena-docs.readthedocs.io/en/latest/submit/study.html) 
- [Register a Sample](https://ena-docs.readthedocs.io/en/latest/submit/samples.html)

#### Authorisation 
By using either service (Test or Production), authorisation is needed by entering the Webin credentials (ID and password).
Webin user name and password must be provided using basic HTTP authentication.
When using curl the user name and password are provided using the ``` -u ``` option:
for example: 
```sh
curl -X 'POST'  -u WebinID:password  'https://wwwdev.ebi.ac.uk/ena/submit/webin-cli/api/v1/genome/covid-19/ ....etc
```
### Validation 
Base URL: /api/v1/genome/covid-19/validate
The validation step is necessary to detect the errors that found in the sequence or metadata. 
Please note that in the validation step, the error reporting is more specific, and it will specify the exact issue if present. 
### Submission 
Base URL: /api/v1/genome/covid-19

Requested body format (JSON file format)
```sh
{
  *"name": "string", #(Unique name for the assembly)
  *"study": "string", #(study accession number or unique name (alias))
  *"sample": "string", #(sample accession number or unique name (alias))
  *"coverage": number, ($double) #(The estimated depth of sequencing coverage)
  *"program": "string", #(The assembly program)
  *"platform": "string", #(The sequencing platform)
  *"sequence": "string", #(assembly sequence in nucleotides)
  "description": "string", #(Free text description of the genome assembly)
  "minGapLength": integer, ($int32) #(Minimum length of consecutive Ns to be considered a gap)
  "moleculeType": "genomic DNA",
  "runRef": "string", #(run accession number)
  "analysisRef": "string", #(analysis accession number)
  "tpa": boolean,
  "authors": "string",
  "address": "string",
  "submissionTool": "string", #(Webin-cli REST)
  "submissionToolVersion": "string" 
}
 "*" Indicates Mandatory Fields.
```

***Example***
```sh
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
  "tpa": false,
  "authors": "EMBL-EBI",
  "address": "United Kingdom",
  "submissionTool": "Webin-Cli REST",
  "submissionToolVersion": "v1"
}
```

***Webin-Cli API service using curl command (command-line) example:***
```sh
curl -X 'POST' -u WebinID:password   \
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
  "tpa": false,
  "authors": "test",
  "address": "test",
  "submissionTool": "webin-cli REST",
  "submissionToolVersion": "0"
}'
```

***Webin-Cli API service using python example:***
```python
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
      "tpa": False, "authors": "test", "address": "test"
    }
]

## Here we used the validation test(dev) URL
server = "https://wwwdev.ebi.ac.uk/ena/submit/webin-cli/api/v1/genome/covid-19/validate"

for sample in data:
    sample_json = json.dumps(sample)
    response = requests.post(
        server, headers={"accept":"application/json", "Content-Type":"application/json"}, 
        data=sample_json, auth=('Webin-56388', 'IlR07wf18uaE')
    )
    status = response.status_code
    if status != 200:
        print("Bad REST call : {}".format(status))
        sys.exit(1)
    else:
        receipt = json.loads(response.content)
        print("{} : {}".format(sample['name'], receipt))
```
### Receipt JSON Format
Once a submission has been processed a JSON receipt is returned

***Response body example (Submission)*** 
```sh
{
  "accession": "ERZ2881825",
  "alias": "webin-genome-test_1",
  "info": [
    "This submission is a TEST submission and will be discarded within 24 hours"
  ],
  "error": []
}
```
***Response body example (Validation) with no errors***
```sh
{
  "accession": null,
  "alias": null,
  "info": [],
  "error": []
}
```
***Response body examples (Validation) with errors***
```sh
#Example 1: Invalid MOLECULETYPE
{
  "accession": null,
  "alias": null,
  "info": [],
  "error": [
    "ERROR: Invalid MOLECULETYPE field value: \"reads\". Valid values are: [genomic DNA, genomic RNA, viral cRNA]. [manifest file: /tmp/288f4f48-132e-4e90-bb56-5d8afe8af4c45476417061259693052/manifest.json, file name: /tmp/288f4f48-132e-4e90-bb56-5d8afe8af4c45476417061259693052/manifest.json, field: MOLECULETYPE, value: reads]"
  ]
}

#Example 2: No study and sample been registered with the accession provided
{
  "accession": null,
  "alias": null,
  "info": [],
  "error": [
    "ERROR: Could not find study \"PRJEB46782\". The study must be owned by the submission account used for this submission or it must be private or temporarily suppressed and referenced by accession. Note that only a single study can be referenced. Unknown study PRJEB46782 or the study cannot be referenced by your submission account. Studies must be submitted before they can be referenced in the submission. [manifest file: /tmp/612ca908-39af-4b72-b9a4-f759bac7f1442135529880044742773/manifest.json, file name: /tmp/612ca908-39af-4b72-b9a4-f759bac7f1442135529880044742773/manifest.json, field: STUDY, value: PRJEB46782]"
  ]
}
```
### Responses 
| Code | Description |
| ------ | ------ |
| 200 | OK |
| 400 | Bad Request |
| 401 | Forbidden |
| 500 | Internal Server error |
