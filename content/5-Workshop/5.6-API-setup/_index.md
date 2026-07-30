---
title : "API Setup"
date : 2026-07-20
weight : 6
chapter : false
pre : " <b> 5.6. </b> "
---

Although our model has already been successfully deployed on a SageMaker Serverless Endpoint, this endpoint by default can only communicate within AWS's internal network. In order for the client-facing application (Frontend) to be able to securely upload diagnostic images over the internet, we need to build an intermediary API layer.

### 1. The Role of AWS Lambda and Amazon API Gateway

In this project's architecture, we use AWS's classic serverless duo:
*   **AWS Lambda (Inference Function):** Acts as an intermediary logic handler. When it receives an X-ray/CT image from the user, Lambda quickly preprocesses the image, reformats the payload as needed, and invokes the SageMaker Endpoint. After SageMaker returns a result, Lambda reformats it into JSON to send back to the application.
*   **Amazon API Gateway:** Provides a public RESTful API URL for the Frontend to call. API Gateway also handles routing and can integrate with Amazon Cognito to block invalid requests.

### 2. Setting Up the API from AWS CloudShell

The project already includes automation code for setting up the Lambda Function and API Gateway: `setup_serverless_api.py`.

Go back to the **AWS CloudShell** terminal and run the following command:

```bash
python pipelines/setup_serverless_api.py
```

This step uses the AWS SDK (Boto3) to:

1. Package the Lambda function's source code.

2. Grant permissions (IAM Role) allowing Lambda to invoke the SageMaker Endpoint.

3. Create a REST API on API Gateway and set up a route connected to the newly created Lambda function.

4. Deploy the API and print the complete URL to the screen.

After running the `python pipelines/setup_serverless_api.py` command in CloudShell, wait for the script to finish and print out the line containing the API Gateway URL.

![API Gateway URL](/images/5-Workshop/5.6-API-setup/setup-api.png)

### 3. Checking the Resources in the AWS Console
To confirm everything has been set up correctly according to the architecture, let's check these two services.

* **Checking AWS Lambda:**
Open the AWS Lambda service in the console, select Functions. You'll see a newly created function (for example: PulmonaryInferenceFunction). Click on it and you can view the Python source code responsible for communicating with SageMaker.

![Checking the Lambda Function](/images/5-Workshop/5.6-API-setup/lambda-function1.png)
![Checking the Lambda Function](/images/5-Workshop/5.6-API-setup/lambda-function2.png)

* **Checking Amazon API Gateway:**
Open the API Gateway service in the console. You'll see a new API (for example: PulmonaryDiagnosticAPI). Click into it, and you'll see the route structure (for example: a POST method on the /diagnose resource) configured to point directly to the Lambda function.

![Checking API Gateway](/images/5-Workshop/5.6-API-setup/api-gateway.png)

*We now have a complete API URL. The final step of the project is to integrate this URL into the Web Frontend so users can directly experience the AI diagnosis feature!*