---
title : "Data Preparation"
date : 2026-06-15 
weight : 3
chapter : false
pre : " <b> 5.3. </b> "
---

In medical imaging, X-ray or CT images captured by different devices often vary in size, resolution, and brightness. If this raw data is fed directly into training, the AI model will converge very slowly or suffer degraded accuracy.

So, before the Training step, we need a Data Preparation / Preprocessing step.

### 1. What is Amazon SageMaker Processing?
Instead of manually spinning up a virtual machine (EC2), downloading data from S3, running processing code, and then uploading it back to S3, AWS provides **Amazon SageMaker Processing**.

This service lets us automate the entire flow:
1. SageMaker automatically spins up a temporary instance.
2. It downloads the raw image data (`toy_data`) from the S3 bucket to the instance.
3. It runs our data processing code (the `src/data/preprocessing.py` file). This code resizes the images, normalizes pixel values, and splits the dataset into Train/Validation/Test sets.
4. It uploads the processed data to a destination folder on S3.
5. It automatically shuts down the instance to save cost.

### 2. Running the Data Pipeline in CloudShell

We've already defined the full infrastructure configuration for this step in the `pipelines/run_processing_job.py` script. To kick off the processing job, go back to your **AWS CloudShell** environment.

Run the following command:

```bash
python pipelines/run_processing_job.py
```

Once the command runs, the AWS SageMaker Python SDK will package the preprocessing.py file, send a request to create a Processing Job on AWS, and print out progress logs (Provisioning instances, Downloading data, Running processing script, etc.).

*This process may take 3 to 5 minutes depending on the amount of data and AWS's instance provisioning time.*

Once it's done, you'll see the processed data stored in your S3 bucket. You can verify this by opening the S3 bucket and confirming that the Train, Validation, and Test datasets have been created correctly.

        ![Data preprocessing step completed](/images/5-Workshop/5.3-Data-preparation/run-processing-job.png)

### 3. Verifying the Results in the AWS Console
To visually observe what the MLOps system just did behind the scenes, we can check directly in the AWS console.

Checking the SageMaker Processing Job:
Go to the Amazon SageMaker service -> in the left-hand menu, select Processing -> Processing jobs. You'll see a new job with a status of Completed.

![Checking the Processing Job in the AWS Console](/images/5-Workshop/5.3-Data-preparation/sagemaker-processing-job.png)

Checking the output data in Amazon S3:
Next, go to the Amazon S3 service and open the bucket holding the project's data. You'll see the system has automatically created a new folder (for example: processed_data, or a folder structure containing train, validation, test). This is the "clean" data now ready for the training stage.

![Checking the output data in Amazon S3](/images/5-Workshop/5.3-Data-preparation/s3-processed-data.png)

With the data successfully normalized and safely stored on S3, our pipeline has completed the preprocessing phase and is ready to move into the most crucial stage: Model Training.