---
title: "Proposal"
date: 2026-06-01
weight: 2
chapter: false
pre: " <b> 2. </b> "
---

# AI Pulmonary Diagnostic Suite  
## AI Solution for Automated Pulmonary Disease Diagnosis on AWS MLOps Architecture  

### 1. Executive Summary
The **AI Pulmonary Diagnostic Suite** is an artificial intelligence (AI) platform specifically designed to assist radiologists in the early detection of pulmonary diseases using X-ray/CT imagery. The project harnesses the power of Deep Learning integrated with a modern **AWS MLOps** architecture. By utilizing 100% scalable AWS services—such as Amazon SageMaker, Amazon S3, and AWS Lambda—the solution delivers an automated workflow spanning data preprocessing, model training, hyperparameter optimization (HPO), and serverless inference deployment, optimizing operational costs while ensuring high diagnostic precision in healthcare.

### 2. Problem Statement
**Current Situation:**  
Analyzing high volumes of chest X-ray/CT scans daily requires significant time and effort from medical staff, creating potential risks of diagnostic oversights caused by subjective factors or workload burnout. Furthermore, deploying existing medical AI models often lacks a standardized pipeline (CI/CD/CT), making model updates and version control challenging while incurring high costs to maintain 24/7 inference servers during idle periods.

**Proposed Solution:**  
Build an end-to-end MLOps system on AWS:
*   Utilize **Amazon S3** as a Data Lake to store medical imaging datasets.
*   Leverage **Amazon SageMaker** to execute pipelines for Data Preprocessing, Model Training, and Hyperparameter Optimization (HPO).
*   Manage the model lifecycle via **SageMaker Model Registry**.
*   Deploy models as **SageMaker Serverless Endpoints** with scale-to-zero capabilities for cost efficiency.
*   Construct inference APIs using **Amazon API Gateway** and **AWS Lambda**.

**Key Benefits:**  
*   **Medical Workflow Optimization:** Assists doctors in rapid localization and diagnosis, significantly reducing patient wait times.
*   **Cost Optimization:** By applying Serverless Inference, the system incurs charges strictly when actual image diagnostic requests are processed, eliminating the expense of 24/7 active servers.
*   **Full Automation:** Pipelines are defined as code (Pipelines as Code), enabling seamless retraining and deployment whenever new patient data becomes available.

### 3. Solution Architecture

The system is designed following the AWS Well-Architected Framework, focusing specifically on the Machine Learning and Serverless Pillars.

![AI Pulmonary Architecture](/images/2-Proposal/mlops_architecture.jpeg)

**AWS Services & Functional Portfolio:**
*   **Amazon S3:** Stores raw data (`toy_data`), preprocessed data, and trained Model Artifacts (`.tar.gz` files).
*   **Amazon SageMaker Processing:** Executes image preprocessing scripts (`preprocessing.py`).
*   **Amazon SageMaker Training & HPO:** Manages compute resources (EC2 instances) for model training (`train.py`) and discovers optimal hyperparameter combinations.
*   **SageMaker Model Registry:** Registers and manages versioning for approved models.
*   **SageMaker Serverless Inference:** Provides endpoints for real-time predictions without infrastructure management overhead.
*   **AWS Lambda & API Gateway:** Constructs RESTful APIs to ingest client image payloads, invoke SageMaker Endpoints, and return diagnostic results.

### 4. Technical Implementation

Implementation is modularized into sequentially executed execution scripts (Pipelines):
*   **Data Pipeline:** Runs `run_processing_job.py` to clean, resize, and normalize X-ray/CT images.
*   **Training Pipeline:** Executes `run_training_job.py` and `run_hpo_job.py` to allocate automated training compute resources.
*   **Deployment Pipeline:** Scripts `repack_and_deploy.py` and `deploy_serverless_endpoint.py` automatically package model artifacts and update Serverless Endpoints with zero downtime.
*   **Monitoring:** Collects and audits system logs via `fetch_logs_v2.py` and `inspect_logs_all.py` on Amazon CloudWatch.

### 5. Roadmap & Milestones

*   **Phase 1:** Analyze medical data, set up S3 storage repositories, author `preprocessing.py` scripts, and generate sample datasets (`create_toy_dataset.py`).
*   **Phase 2:** Develop the Deep Learning model (`train.py`), and configure Training and HPO jobs on Amazon SageMaker.
*   **Phase 3:** Construct MLOps Pipelines (Model Registration, artifact repacking, Serverless Endpoint provisioning).
*   **Phase 4:** Establish API Gateway and AWS Lambda connections to Endpoints. Perform End-to-End testing and evaluate model performance.

### 6. Budget Estimation

Adopting Serverless Inference and Managed Training Jobs ensures highly effective budget control. Costs are primarily driven by model training execution.

**Estimated AWS Costs:**
*   **Amazon S3:** ~$1.00/month (Dataset and model artifact storage).
*   **SageMaker Training Jobs:** Dependent on active GPU instance runtimes (e.g., `ml.g4dn.xlarge`). Estimated at ~$10.00 – $20.00 for the development phase.
*   **SageMaker Serverless Inference:** Charged per millisecond of compute and memory allocation (Billed exclusively when API calls are triggered). Estimated at ~$1.00 – $3.00/month for lab environments.
*   **API Gateway & AWS Lambda:** Covered under the AWS Free Tier (Minimal cost).

### 7. Risk Management

| Risk | Probability | Impact | Mitigation Strategy |
| :--- | :--- | :--- | :--- |
| **Model Drift (Accuracy degradation)** | Medium | High | Establish SageMaker Model Monitor. Build automated retraining pipelines triggered by new data ingestion. |
| **Medical Data Security (PHI)** | Low | Critical | Enforce Data Encryption At-Rest on S3 (KMS) and In-Transit via TLS/SSL. Adhere strictly to Least Privilege IAM policies. |
| **Endpoint Cold Starts** | High | Medium | Execute `warmup_endpoint.py` scripts to maintain endpoint readiness, or use Provisioned Concurrency if absolute low latency is required. |
| **Uncontrolled Training Costs** | Low | Medium | Configure AWS Budgets and set `MaxRuntimeInSeconds` caps on Training/HPO Jobs for automatic termination. |

### 8. Expected Outcomes
Delivers a fully functional Cloud-Native automated medical diagnostic system. The project extends beyond an isolated AI model to establish a **complete MLOps workflow**. The outcome provides a highly available pulmonary diagnostic API, creating potential integration opportunities for clinical Web/Mobile applications in real-world healthcare settings.