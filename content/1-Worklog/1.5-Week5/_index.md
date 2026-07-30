---
title: "Week 5"
date: 2026-06-29
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---

### Week 5 Objectives
* Execute Hyperparameter Optimization (HPO) to automatically discover optimal model parameters.
* Complete and submit Blog Post 2.

### Task Progress
| Day | Task | Start Date | Completion Date | Reference Sources |
| --- | --- | --- | --- | --- |
| Mon | - Defined HPO Search Space: Learning Rate (`1e-5` to `1e-2`), Batch Size (16 or 32). | 06/29/2026 | 06/29/2026 | [SageMaker HPO Guide](https://docs.aws.amazon.com/sagemaker/latest/dg/automatic-model-tuning.html) |
| Tue | - Configured `HyperparameterTuner` object, setting Objective Metric to maximize Recall. | 06/30/2026 | 06/30/2026 | [Boto3 HyperparameterTuner API](https://sagemaker.readthedocs.io/en/stable/api/training/tuner.html) |
| Wed | - Launched HPO Job configured to run up to 3 parallel jobs to minimize waiting time. | 07/01/2026 | 07/01/2026 | [AWS Tuning Best Practices](https://docs.aws.amazon.com/sagemaker/latest/dg/automatic-model-tuning-considerations.html) |
| Thu | - HPO Job completed. Analyzed SageMaker Studio comparison charts and selected the model with the highest Recall score. | 07/02/2026 | 07/02/2026 | [SageMaker Studio Analytics](https://docs.aws.amazon.com/sagemaker/latest/dg/studio-analyze.html) |
| Fri | - Finalized writing Blog Post 2 and submitted it to the platform. | 07/03/2026 | 07/03/2026 | [FCAJ Blog Guidelines](https://cloudjourney.awsstudygroup.com/) |

### Key Achievements
* Identified optimal hyperparameter configuration systematically without manual code edits.
* Successfully published Technical Blog Post 2.
