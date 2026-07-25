---
title: "Blog 2"
date: 2026-07-25
weight: 2
chapter: false
pre: " <b> 3.2. </b> "
---

# Building an MLOps Pipeline: Migrating X-Ray Data to S3 and Optimizing DenseNet121 Training Script Directly on Amazon SageMaker

Hello everyone!

After completing the FinOps financial safeguards (AWS Budgets & CloudWatch Alarms) to secure our $200 credit budget, the next step in our **AI Pulmonary Diagnostic Suite** MLOps journey is migrating the entire data processing and model training pipeline from Kaggle/Local Notebooks to the Amazon SageMaker cloud infrastructure.

During the previous PoC/Research phase, the DenseNet121 pneumonia diagnosis model was trained directly in a local Notebook using all 5,800 X-ray images. However, when moving toward production-grade operations, scattered data storage and manual code execution revealed several critical drawbacks:

1. Inability to centrally manage medical imaging data.
2. Extended compute server execution time, leading to resource waste and increased costs.
3. Code dependencies on local machine environments, making automated packaging difficult.

In today's post, I would like to share how we permanently resolved these issues by building a centralized Data & Training Pipeline on AWS.

---

## 1. Cloud Data Storage & Processing Architecture

Instead of storing data directly inside the Web application's local project directory (`app.py`), all X-ray images are centralized into **Amazon S3**—a highly secure and available object storage service.

### Cost Optimization Strategy: Toy Dataset Strategy

Uploading all 5,800 images to S3 and running SageMaker Training Jobs for hours would quickly consume our credit balance. Since the primary objective at this stage is proving and refining the End-to-End MLOps pipeline rather than obsessing over incremental model accuracy gains, I applied a data sampling technique:

* Extracted a lightweight **Toy Dataset** containing 100 training images (50 Normal, 50 Pneumonia cases) and 20 validation/test images.
* Configured a standardized S3 Bucket structure:
  * `s3://ai-pulmonary-data-bucket/chest_xray/train/`
  * `s3://ai-pulmonary-data-bucket/chest_xray/test/`

> **Result:** Data download and environment setup time for SageMaker Processing/Training Jobs was reduced from 45 minutes to just 1.5 minutes, saving over 90% in server compute costs while thoroughly testing the entire pipeline flow!

---

## 2. Refactoring Source Code: Converting Notebook to Custom Training Script

When training on SageMaker, the system automatically provisions a virtualized Docker Container. Therefore, the DenseNet121 training code (`ai-pulmonary-diagnostic-suite.ipynb`) needed to be refactored into an independent Python file (`train.py`) with several core enhancements:

### a. Parsing Input Arguments via `argparse`

The SageMaker environment automatically passes data directory paths and hyperparameter configurations via the Command Line Interface (CLI):

```python
import argparse
import os

parser = argparse.ArgumentParser()

# Receive hyperparameters
parser.add_argument('--epochs', type=int, default=2)
parser.add_argument('--batch_size', type=int, default=32)
parser.add_argument('--learning_rate', type=float, default=0.001)

# Receive directory paths automatically mounted from S3 by the SageMaker Container
parser.add_argument('--train', type=str, default=os.environ.get('SM_CHANNEL_TRAIN'))
parser.add_argument('--test', type=str, default=os.environ.get('SM_CHANNEL_TEST'))
parser.add_argument('--model_dir', type=str, default=os.environ.get('SM_MODEL_DIR'))

args = parser.parse_args()
```

### b. Packaging Core DenseNet121 Model & Fine-Tuning

While image processing logic and Transfer Learning performance from DenseNet121 were preserved, output model weights (`model.tar.gz`) are automatically saved directly to the `SM_MODEL_DIR` directory, allowing SageMaker to auto-sync artifacts back to S3 upon training completion.

---

## 3. Executing SageMaker Training Job via Python SDK

From SageMaker Studio, we trigger a training run using the `sagemaker.tensorflow.TensorFlow` SDK:

```python
from sagemaker.tensorflow import TensorFlow

# Configure TensorFlow Estimator
tf_estimator = TensorFlow(
    entry_point='train.py',                 # Refactored training script file
    role=role,                              # IAM Role with least-privilege permissions
    instance_count=1,                       # Single instance execution
    instance_type='ml.m5.xlarge',           # Cost-effective CPU instance type
    framework_version='2.13.0',
    py_version='py310',
    hyperparameters={
        'epochs': 2,                        # Run 2 test epochs to verify pipeline flow
        'batch_size': 16,
        'learning_rate': 0.001
    }
)

# Trigger Training Job reading data directly from S3
tf_estimator.fit({
    'train': 's3://ai-pulmonary-data-bucket/chest_xray/train',
    'test':  's3://ai-pulmonary-data-bucket/chest_xray/test'
})
```

---

## 4. Key Results Achieved & MLOps Lessons Learned

* **Fully Automated I/O Pipeline:** Data is automatically pulled from S3 into the Container, and the trained model artifacts are automatically pushed back to S3 without any manual upload/download steps.
* **Maximum Cost Optimization:** Combining the low-cost `ml.m5.xlarge` instance with the Toy Dataset strategy resulted in a total cost of under **$0.20 credit** per Training Job run!
* **Production-Ready Next Steps:** The model saved on S3 is ready to be version-registered into SageMaker Model Registry (Week 5) and exposed as a real-time endpoint via AWS Lambda + API Gateway in Week 6.
* **Key Takeaway:** Decoupling training logic (`train.py`) from compute infrastructure (SageMaker Container) keeps the codebase clean, secure, and easily scalable when dealing with tens of thousands of new data points in the future.

#AWS #AmazonSageMaker #MLOps #FinOps #AI #DeepLearning #DenseNet121 #DataScience #CloudComputing #FirstCloudJourney
