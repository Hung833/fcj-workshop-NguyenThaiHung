---
title: "Worklog Week 1"
date: 2026-06-01
weight: 1
chapter: false
pre: " <b> 1.1. </b> "
---
### Week 1 Objectives:
* Network and align workflows with the First Cloud AI Journey (FCAJ) program coordinators and peers.
* Initialize a secured corporate AWS environment, familiarize with the AWS Management Console interface, and configure the AWS CLI endpoint.
* Analyze the existing repository codebase and pre-trained weights architecture `pneumonia_model_finetuned.keras` of the AI Pulmonary Diagnostic Suite to prepare for Cloud MLOps migration mapping.

### Tasks Implemented This Week:
| Day | Task Description | Start Date | End Date | Reference Materials |
| --- | --- | --- | --- | --- |
| Mon | - Attended the corporate orientation session; synchronized with onboarding guidelines at AWS Viet Nam <br> - Received cloud infrastructure organizational enrollment indexes for FCAJ | 01/06/2026 | 01/06/2026 | AWS Internal Training Docs |
| Tue | - Reviewed core AWS service documentation (Compute, Storage, Networking, Identity Access Management)<br> - Assessed the structural topology of the pre-trained CNN model within `pneumonia_model_finetuned.keras` | 02/06/2026 | 02/06/2026 | <https://cloudjourney.awsstudygroup.com/> |
| Wed | - Activated the AWS Management Console enterprise node <br> - Enforced Multi-Factor Authentication (MFA) baseline policies on the Root Account <br> - Provisioned administrative IAM users adhering strictly to the Principle of Least Privilege (PoLP) | 03/06/2026 | 03/06/2026 | AWS IAM Best Practices Guide |
| Thu | - Standardized local workstation dependencies: AWS CLI v2, Python MLOps SDK environment, Docker Engine <br> - Conducted programmatic authentication setup using `aws configure` (Access Key, Secret Key, Target Region `ap-southeast-1`) | 04/06/2026 | 04/06/2026 | <https://docs.aws.amazon.com/cli/> |
| Fri | - Validated cloud connectivity endpoints through programmatic CLI verification commands <br> - Initialized the local workspace framework matching `fcj-workshop-template-main` structural paradigms for future technical docs | 05/06/2026 | 05/06/2026 | Personal Repository & FCAJ Template |

### Results Achieved:
* **Secured Cloud Infrastructure Base:** Successfully provisioned the primary AWS tenant environment and isolated Root Account threat vectors using mandatory hardware/virtual MFA locks.
* **Administrative IAM Architecture:** Formulated isolated IAM user accounts tailored specifically for the Cloud/MLOps engineering scope without exposing base subscription credentials.
* **AWS CLI v2 Operability:** Established authenticated communication channels between local development nodes and the Singapore region (`ap-southeast-1`) AWS API endpoints.
* **Workspace Framework Standardization:** Completed the structural workspace baseline utilizing the `fcj-workshop-template-main` layout, prepping files for the upcoming integration of pneumonia X-ray deep learning pipelines on AWS SageMaker.
