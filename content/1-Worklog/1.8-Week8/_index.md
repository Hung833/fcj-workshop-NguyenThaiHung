---
title: "Week 8"
date: 2026-07-20
weight: 8
chapter: false
pre: " <b> 1.8. </b> "
---

### Week 8 Objectives
* Set up automated email error notifications (Monitoring).
* Consolidate isolated scripts into an automated MLOps Pipeline.
* Write and submit Technical Blog Post 3.

### Task Progress
| Day | Task | Start Date | Completion Date | Reference Sources |
| --- | --- | --- | --- | --- |
| Mon | - Configured SNS Topic and CloudWatch Alarm monitoring API Gateway 5xx errors. Successfully verified email notifications. | 07/20/2026 | 07/20/2026 | [Amazon CloudWatch & SNS](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/AlarmThatSendsEmail.html) |
| Tue | - Initiated MLOps Pipeline development, linking Processing and Training scripts. | 07/21/2026 | 07/21/2026 | [SageMaker Pipelines SDK](https://sagemaker.readthedocs.io/en/stable/amazon_sagemaker_model_building_pipeline.html) |
| Wed | - Resolved dependency version conflicts by pinning `sagemaker<3.0`.<br>- Defined DAG containing `TrainingStep` and `RegisterModelStep`. | 07/22/2026 | 07/22/2026 | [PIP Dependency Management](https://pip.pypa.io/en/stable/user_guide/) |
| Thu | - Triggered test Pipeline execution. Monitored automated DAG workflow execution on SageMaker Studio interface. | 07/23/2026 | 07/23/2026 | [SageMaker Studio UI](https://docs.aws.amazon.com/sagemaker/latest/dg/pipelines-studio.html) |
| Fri | - Finalized and submitted Blog Post 3 titled "MLOps Automation". | 07/24/2026 | 07/24/2026 | [FCAJ Blog Guidelines](https://cloudjourney.awsstudygroup.com/) |

### Key Achievements
* Packaged end-to-end MLOps CI/CD system; new model retraining and registration triggerable with a single click.
* Successfully completed all 3 technical blog post obligations for the program.
