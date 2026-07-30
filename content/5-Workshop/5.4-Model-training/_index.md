---
title : "Model Training"
date : 2026-06-22 
weight : 4
chapter : false
pre : " <b> 5.4. </b> "
---

Once the data has been preprocessed and stored in normalized form on Amazon S3, the next step in the MLOps workflow is Model Training.

For medical image analysis tasks like lung X-ray/CT, training convolutional neural networks (CNNs) usually requires powerful hardware (especially GPUs). Building our own server for this would be costly to set up and maintain.

### 1. How Training Works on Amazon SageMaker
**Amazon SageMaker Training** provides a fully-managed infrastructure solution. Here's how it works:
1. SageMaker automatically provisions high-performance virtual machines (EC2 instances) based on the configuration we request.
2. It downloads our training source code (`src/train.py`) and the dataset from S3 onto the instance.
3. It runs the model training process.
4. As soon as training completes, the system packages the model (model artifacts) and automatically uploads them back to Amazon S3.
5. Finally, SageMaker immediately cleans up and shuts down the instance, so we **only pay for the actual number of seconds the instance ran**.

### 2. Triggering the Training Pipeline from CloudShell
Instead of doing this manually through the web console, we'll automate kicking off this training flow using the `run_training_job.py` script.

Go back to the **AWS CloudShell** terminal screen and run the following command:

```bash
python pipelines/run_training_job.py
```

Once the script is triggered, SageMaker will begin provisioning resources and the training process will start.
Once training finishes, you'll see a completion message and the trained model will be stored on S3.

![Model training success notification](/images/5-Workshop/5.4-Model-training/run-training-job.png)

*(Note: Training the AI model can take anywhere from a few minutes to several dozen minutes depending on the amount of data (toy_data) and the instance type you use. To save time here, we're only training on 120 representative images.)*

### 3. Checking Progress and Results in the AWS Console
While waiting for the CloudShell command to finish, you can check progress directly in the AWS interface.

* **Monitoring the SageMaker Training Job:**
From the AWS Console, open the Amazon SageMaker service. In the left-hand menu, select Training -> Training jobs. You'll see the list of training tasks.

Once the task completes, its status will change to Completed.

* **Checking the Model Artifact on S3:**
After training, the model isn't left on the instance — it's compressed into a `.tar.gz` file and stored safely on S3.
Go to the Amazon S3 service, find the project's bucket, and open the training output folder (usually the `output/` folder). You'll see the `model.tar.gz` file. That's our result!

![Training notification on SageMaker and on S3](/images/5-Workshop/5.4-Model-training/aws-run-training-job.png)

*Your deep learning lung diagnosis model is now ready to be registered (Model Registry) and deployed as an API (Deployment)!*