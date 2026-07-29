---
title: "Week 4 Worklog"
date: 2026-06-22
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---

### Week 4 Objectives:
* Develop DenseNet121 model training code and execute SageMaker Training Jobs.

### Implemented Tasks:
| Day | Task | Completion Date |
| --- | --- | --- |
| Mon (06/22) | One member developed `train.py` using Keras/TensorFlow, configuring command-line argument parsing. | 06/22/2026 |
| Tue (06/23) | The other member configured the SageMaker Estimator inside a notebook, specifying AWS pre-built TensorFlow Deep Learning Container images. | 06/23/2026 |
| Wed (06/24) | Attached input data channels from S3 to the Estimator and triggered the Training Job on a GPU instance (`ml.p3.2xlarge`) for accelerated training. | 06/24/2026 |
| Thu (06/25) | Monitored CloudWatch Logs to track training progression, checking Loss and Accuracy metrics. | 06/25/2026 |
| Fri (06/26) | Verified the `model.tar.gz` artifact on S3, confirming that model training and standard packaging completed successfully. | 06/26/2026 |

### Key Achievements:
* AWS TensorFlow Container executed seamlessly without library dependencies issues. Output weight artifacts were securely stored on S3, ready for subsequent stages.
