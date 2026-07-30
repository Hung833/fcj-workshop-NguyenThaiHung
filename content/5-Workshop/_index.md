---
title: "Workshop"
date: 2026-07-30
weight: 5
chapter: false
pre: " <b> 5. </b> "
---

# Deploying an AI Pulmonary Diagnostics System with Serverless MLOps Architecture

#### Overview

**AI Pulmonary Diagnostic Suite** is an artificial intelligence (AI) platform specifically designed to assist radiologists in early detection of pulmonary diseases using X-ray/CT imagery.

In this lab, we will build an end-to-end MLOps workflow on AWS, covering everything from data preparation to deploying a production-ready diagnostic API. Unlike traditional systems that require 24/7 server uptime leading to resource waste, this project is engineered for maximum cost optimization.

We will combine core AWS services to create an automated system with scale-to-zero capabilities:
+ **Amazon S3** - Serves as a secure Data Lake to store raw chest imaging data (toy dataset) and model artifacts[cite: 6].
+ **Amazon SageMaker** - Automates data preprocessing tasks, provisions compute resources for model training, and provides a Serverless Endpoint for serverless inference.
+ **AWS Lambda & Amazon API Gateway** - Form the intermediate backend API layer to receive images from the web interface, process the payloads, and invoke the SageMaker Endpoint to return diagnostic results.

#### Table of Contents

1. [Introduction](5.1-Workshop-overview/)
2. [Prerequisites](5.2-Prerequisite/)
3. [Data Preprocessing](5.3-Data-preparation/)
4. [Model Training](5.4-Model-training/)
5. [Model Deployment](5.5-Model-deployment/)
6. [API Setup](5.6-API-setup/)
7. [Frontend Web Interface](5.7-Frontend/)