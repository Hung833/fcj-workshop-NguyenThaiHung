---
title: "Week 3"
date: 2026-06-15
weight: 3
chapter: false
pre: " <b> 1.3. </b> "
---

### Week 3 Objectives
* Migrate data preprocessing code (resize, normalize) to run automatically on Amazon SageMaker Processing Jobs.

### Task Progress
| Day | Task | Start Date | Completion Date | Reference Sources |
| --- | --- | --- | --- | --- |
| Mon | - Refactored image processing functions from legacy Jupyter Notebooks into a standalone `preprocessing.py` file. | 06/15/2026 | 06/15/2026 | [Scikit-image Docs](https://scikit-image.org/docs/stable/) |
| Tue | - Configured SageMaker IAM Role with permissions to read images from S3 bucket.<br>- Initialized SageMaker Studio to test environment. | 06/16/2026 | 06/16/2026 | [SageMaker Execution Roles](https://docs.aws.amazon.com/sagemaker/latest/dg/sagemaker-roles.html) |
| Wed | - Authored SageMaker Processing Job execution script, configured to use a cost-effective `ml.m5.xlarge` instance. | 06/17/2026 | 06/17/2026 | [SageMaker Python SDK](https://sagemaker.readthedocs.io/en/stable/) |
| Thu | - Executed Processing Job. Monitored CloudWatch logs and verified processed dataset directory structures in S3. | 06/18/2026 | 06/18/2026 | [Amazon CloudWatch Logs](https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/) |
| Fri | - Audited AWS Cost Explorer with the team to analyze yesterday's Job execution costs.<br>- Drafted outline for Blog 2. | 06/19/2026 | 06/19/2026 | [AWS Billing Console](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/) |

### Key Achievements
* Successfully migrated data preparation pipeline to the Cloud. SageMaker fetches, processes, and stores data back to S3 in under 3 minutes.
