---
title: "Worklog Week 2"
date: 2026-06-08
weight: 2
chapter: false
pre: " <b> 1.2. </b> "
---

### Week 2 Objectives:
* Construct a minimized testing dataset workflow (Toy Dataset) from the raw pulmonary X-ray database to optimize cloud consumption bounds.
* Re-engineer the inference distribution model into a highly secure distributed Serverless pipeline, replacing the insecure legacy framework that loads model binaries locally.
* Finalize the technical syllabus and write-up for Tech Blog Post 1 for submission to the cloud learning management system.

### Tasks Implemented This Week:
| Day | Task Description | Start Date | End Date | Reference Materials |
| --- | --- | --- | --- | --- |
| Mon | - Assessed security and structural risks within the legacy `app.py` script loading local Keras/TFLite files.<br>- Outlined a robust Serverless migration topology incorporating cryptographic access layers. | 08/06/2026 | 08/06/2026 | AWS Architecture Reference Sheets |
| Tue | - Designed the structural skeleton for a 3-part cloud logging blog sequence required by FCAJ criteria.<br>- Authored the complete draft for Blog 1: "Architecting Secure Serverless MLOps Pipelines and Cloud Cost Governance on AWS." | 09/06/2026 | 09/06/2026 | AWS Study Group Content Guidelines |
| Wed | - Engineered a python data engineering script `create_toy_dataset.py` executing a balanced stratified random sampling to extract 120 X-ray images (100 Train, 20 Test/Val split across target labels). | 10/06/2026 | 10/06/2026 | Python Data Science Manuals |
| Thu | - Provisioned core cloud object storage primitives via AWS CLI to build target Amazon S3 Buckets (`fcj-pulmonary-suite-data-2026`).<br>- Validated data integrity and execution pathways of the processing script locally. | 11/06/2026 | 11/06/2026 | Amazon S3 Developer Guide |
| Fri | - Synchronized the complete hierarchical Toy Dataset directory up to the target cloud storage bucket via AWS CLI.<br>- Programmed a secure metadata signing algorithm within the reporting generator to assert programmatic ownership. | 12/06/2026 | 12/06/2026 | Internal Diagnostic Reporting Codebase |

### Results Achieved:
* Deployed a robust automated data downsampling workflow that structures the 120-image Toy Dataset, ensuring that subsequent SageMaker execution runs wrap up within 1-2 minutes and capping test burns under $0.50 credit per run.
* Successfully initialized structured cloud storage topologies and staged the preliminary baseline X-ray artifacts into secure Amazon S3 partitions via AWS CLI.
* Ratified a finalized secure Serverless architecture scheme: Streamlit interfaces route payloads through encrypted Amazon API Gateway REST proxies, triggering an AWS Lambda function that retrieves access tokens from AWS Secrets Manager to query an isolated SageMaker Endpoint.
* Integrated digital ownership metadata strings ("Verified by AI Engineer Nguyen Thai Hung - AWS MLOps Suite") into the backend analytical output layers (.xlsx/.txt modules).
* Successfully published Technical Blog Post 1, meeting all editorial and academic standards outlined by the AWS Study Group committee.
