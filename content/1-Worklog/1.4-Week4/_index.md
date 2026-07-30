---
title: "Week 4"
date: 2026-06-22
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---

### Week 4 Objectives
* Train AI model (DenseNet121) using SageMaker Training Job with the preprocessed dataset from last week.

### Task Progress
| Day | Task | Start Date | Completion Date | Reference Sources |
| --- | --- | --- | --- | --- |
| Mon | - Authored Keras `train.py` script, incorporating `argparse` to parse external hyperparameter inputs. | 06/22/2026 | 06/22/2026 | [TensorFlow API Docs](https://www.tensorflow.org/api_docs) |
| Tue | - Initialized SageMaker TensorFlow Estimator, mapping S3 input data channels. | 06/23/2026 | 06/23/2026 | [SageMaker TensorFlow Estimator](https://sagemaker.readthedocs.io/en/stable/frameworks/tensorflow/sagemaker.tensorflow.html) |
| Wed | - Launched Training Job using GPU-accelerated `ml.p3.2xlarge` instance for faster execution. | 06/24/2026 | 06/24/2026 | [Amazon EC2 Instance Types](https://aws.amazon.com/ec2/instance-types/) |
| Thu | - Monitored training progress via CloudWatch Logs.<br>- Resolved minor OS pathing bugs within container. | 06/25/2026 | 06/25/2026 | [SageMaker Training Logs](https://docs.aws.amazon.com/sagemaker/latest/dg/logging-cloudwatch.html) |
| Fri | - Verified output artifacts on S3. Confirmed successful generation of `model.tar.gz`. | 06/26/2026 | 06/26/2026 | [SageMaker Model Output](https://docs.aws.amazon.com/sagemaker/latest/dg/your-algorithms-training-algo-output.html) |

### Key Achievements
* Trained team's first AI model on AWS. Weight artifacts were properly packaged following SageMaker standards and securely stored in S3.
