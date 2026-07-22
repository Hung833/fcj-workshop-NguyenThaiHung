---
title: "Worklog Week 3"
date: 2026-06-15
weight: 3
chapter: false
pre: " <b> 1.3. </b> "
---

### Week 3 Objectives:
* Migrate localized data preparation workflows into cloud-native distributed environments by executing data preprocessing and feature engineering via Amazon SageMaker Processing Jobs.
* Establish unified, scalable data management for raw and processed lung X-ray training data artifacts on Amazon S3.

### Tasks Implemented This Week:
| Day | Task Description | Start Date | End Date | Reference Materials |
| --- | --- | --- | --- | --- |
| Mon | - Factored the localized chest X-ray image transformation logic into a standalone python execution script `preprocessing.py` adapted for secure containers.<br>- Mapped S3 data output directory partitions. | 15/06/2026 | 15/06/2026 | Amazon SageMaker Developer Guide |
| Tue | - Structured and attached strict IAM Execution Roles granting Amazon SageMaker robust read/write access privileges on the designated S3 buckets.<br>- Initialized the composite SageMaker Studio domain environment. | 16/06/2026 | 16/06/2026 | AWS IAM Permissions Reference |
| Wed | - Configured and launched a SageMaker Processing Job using the SageMaker Python SDK, allocating cost-efficient instances (`ml.m5.xlarge`) to execute the containerized `preprocessing.py` workload. | 17/06/2026 | 17/06/2026 | SageMaker Python SDK API |
| Thu | - Monitored processing execution states, validating output matrix formats and verifying the automatic delivery of the split data arrays (Train/Test/Validation) back into S3 namespaces. | 18/06/2026 | 18/06/2026 | AWS SageMaker Console |
| Fri | - Audited infrastructure cost efficiencies and job completion metrics for the cloud-based data processing workloads.<br>- Initiated the structural ideation and programmatic syllabus for Technical Blog Post 2. | 19/06/2026 | 19/06/2026 | AWS Cost Explorer |

### Results Achieved:
* Successfully migrated the localized data engineering and X-ray image transformation logic onto Amazon SageMaker Processing Job distributed compute infrastructure.
* Standardized, augmented, and automatically partitioned the target pulmonary X-ray Toy Dataset into segregated cloud folders (`/train`, `/test`, `/validation`) hosted inside Amazon S3.
* Enforced tight IAM security boundaries, ensuring seamless, encrypted communications between SageMaker Studio components and cloud object storage layers.
* Completed cloud image data engineering cycles in under 3 minutes, achieving highly optimized cloud infrastructure utilization.
