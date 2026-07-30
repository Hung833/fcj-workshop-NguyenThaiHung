---
title : "Model Deployment"
date : 2026-07-13 
weight : 5
chapter : false
pre : " <b> 5.5. </b> "
---

The result of the training process is a compressed model artifact file (`model.tar.gz`) stored safely on Amazon S3. However, in order for a doctor's Web or App application to be able to upload new X-ray/CT images and receive diagnosis results, we need to deploy this model as an API endpoint.

### 1. Why Choose Amazon SageMaker Serverless Inference?

Normally, keeping a real-time inference instance running 24/7 is expensive, especially when a clinic doesn't have a continuous stream of patients.

In this project, we use **SageMaker Serverless Inference**. This serverless mechanism offers great benefits:
*   **Auto-scaling:** Automatically provisions compute resources when a request comes in, and scales down to zero (sleep mode) when no one is using it.
*   **Cost optimization:** You only pay for the time (measured in milliseconds) and memory the system actually uses to produce a diagnosis result.

### 2. Deploying from AWS CloudShell

The project already includes MLOps scripts to automate this deployment step. Go back to the **AWS CloudShell** terminal and run the following command to set up the Serverless Endpoint:

```bash
python pipelines/deploy_serverless_endpoint.py
```

The system will automatically perform 3 tasks:

1. Register the model (create a SageMaker Model pointing to the `.tar.gz` file on S3).

2. Create an Endpoint Configuration of type Serverless (specifying the maximum RAM and the number of concurrent requests).

3. Deploy the actual Endpoint.

*Note: Deploying the endpoint may take about 3 to 5 minutes for AWS to configure resources behind the scenes.*

Once the script completes, you'll see a success message along with the name of the created endpoint. Remember this name, since you'll need it in the next step to test the API.

![Endpoint deployment success notification](/images/5-Workshop/5.5-Model-deployment/run-deploy-endpoint.png)

### 3. Checking the Endpoint in the AWS Console
To make sure our endpoint is ready to serve requests:

* **Step 1:** From the AWS Console, open the Amazon SageMaker service.
* **Step 2:** In the left-hand menu, scroll down to the Inference section and select Endpoints.
* **Step 3:** You'll see the name of the project's endpoint that was just created. Once the Status column changes to InService (green), that means your lung diagnosis API is fully ready to receive requests!

![Checking the Endpoint status in the AWS Console](/images/5-Workshop/5.5-Model-deployment/sagemaker-endpoint-inservice.png)

*The AI model has now been successfully deployed to the cloud at the most optimized cost.*