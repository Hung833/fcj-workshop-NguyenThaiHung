---
title : "Introduction"
date : 2026-06-01 
weight : 1
chapter : false
pre : " <b> 5.1. </b> "
---

#### What is a Serverless MLOps Architecture?
In typical medical AI projects, keeping an inference server (such as an Amazon EC2 instance) running 24/7 wastes resources and incurs significant costs, especially since diagnostic imaging requests from clinics don't arrive continuously.

To solve this problem, in the **AI Pulmonary Diagnostic Suite** project, our team decided to use a **Serverless Inference** architecture through the Amazon SageMaker platform.
Simply put: our AI model goes to "sleep" (scales down to zero) when no one is using it. Only when a doctor uploads an X-ray/CT image to the system to request a diagnosis is the endpoint activated, performs inference, and is billed per millisecond of processing. By combining **Amazon SageMaker**, **AWS Lambda**, **Amazon API Gateway**, and **Amazon S3**, we get a flexible AI system that can automatically scale with load and thoroughly optimize the AWS bill.

#### Workshop Overview
In this workshop, I'll walk you through building the **AI Pulmonary Diagnostic Suite** system yourself, from data preparation all the way to deploying a complete diagnostic API.

We'll go through the following main sections:
+ **Create a Data Lake & Process Data:** Create an Amazon S3 bucket to hold raw lung imaging data (`toy_data`) and configure data preprocessing tasks.
+ **Train the AI Model:** Set up Amazon SageMaker Training Jobs to train the Deep Learning model.
+ **Deploy a Serverless Endpoint:** Store the model artifacts and automatically deploy the model to a SageMaker Serverless Endpoint.
+ **Build the Backend API:** Write an AWS Lambda function and wire it up with API Gateway to create a REST API gateway responsible for receiving images and returning lung diagnosis results.
+ **Web Interface & Authentication:** Deploy the Next.js website source code to AWS Amplify for doctors to use, while using Amazon Cognito to secure and manage access.

*(Note: Training the model on SageMaker may require GPU/CPU virtual machine resources and incur costs. Be sure to monitor your budget and remember to complete the final step — cleaning up resources — so AWS doesn't charge you unintentionally!)*

![Project architecture overview](/images/5-Workshop/5.1-Workshop-overview/diagram1.png)