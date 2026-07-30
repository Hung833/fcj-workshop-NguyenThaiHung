---
title: "Week 6"
date: 2026-07-06
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---

### Week 6 Objectives
* Version control model artifacts using SageMaker Model Registry in preparation for deployment.

### Task Progress
| Day | Task | Start Date | Completion Date | Reference Sources |
| --- | --- | --- | --- | --- |
| Mon | - Created Model Package Group named `Pulmonary-Diagnostic-Models` in SageMaker. | 07/06/2026 | 07/06/2026 | [SageMaker Model Registry](https://docs.aws.amazon.com/sagemaker/latest/dg/model-registry.html) |
| Tue | - Registered top-performing model from HPO tuning into Registry using Python Boto3 SDK. | 07/07/2026 | 07/07/2026 | [Boto3 ModelPackage API](https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/sagemaker.html) |
| Wed | - Configured approval workflow. Updated version status to `Approved` to mark readiness for Production. | 07/08/2026 | 07/08/2026 | [MLOps Model Approval](https://docs.aws.amazon.com/sagemaker/latest/dg/model-registry-approve.html) |
| Thu | - Initiated development of `inference.py` (Custom Handler) to process incoming Base64 image payloads from Frontend. | 07/09/2026 | 07/09/2026 | [SageMaker Inference Toolkit](https://github.com/aws/sagemaker-inference-toolkit) |
| Fri | - Conducted cross-code reviews on NumPy array transformations in inference script to prevent RAM overflow issues. | 07/10/2026 | 07/10/2026 | [NumPy Memory Management](https://numpy.org/doc/stable/user/basics.html) |

### Key Achievements
* Versioned (v1) and centralized model lifecycle management, eliminating arbitrary local storage files.
