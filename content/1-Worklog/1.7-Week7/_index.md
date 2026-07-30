---
title: "Week 7"
date: 2026-07-13
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---

### Week 7 Objectives
* Deploy model to Serverless Endpoint for cost optimization.
* Build Backend connection layer integrating API Gateway and AWS Lambda.

### Task Progress
| Day | Task | Start Date | Completion Date | Reference Sources |
| --- | --- | --- | --- | --- |
| Mon | - Packaged model archive with `requirements.txt` (adding Pillow, numpy) to ensure automated dependency installation upon deployment. | 07/13/2026 | 07/13/2026 | [Python PIP Packaging](https://packaging.python.org/en/latest/) |
| Tue | - Executed deployment code to provision SageMaker Serverless Endpoint V2 configured with 2GB RAM. | 07/14/2026 | 07/14/2026 | [SageMaker Serverless Inference](https://docs.aws.amazon.com/sagemaker/latest/dg/serverless-endpoints.html) |
| Wed | - Co-authored AWS Lambda handler. Configured `ENDPOINT_NAME` environment variable and assigned IAM execution permissions. | 07/15/2026 | 07/15/2026 | [AWS Lambda Env Vars](https://docs.aws.amazon.com/lambda/latest/dg/configuration-envvars.html) |
| Thu | - Configured API Gateway, mapping RESTful `POST /predict` method to the Lambda proxy. | 07/16/2026 | 07/16/2026 | [API Gateway REST APIs](https://docs.aws.amazon.com/apigateway/latest/developerguide/apigateway-rest-api.html) |
| Fri | - Tested API via cURL image request payloads, receiving valid JSON responses. | 07/17/2026 | 07/17/2026 | [cURL Documentation](https://curl.se/docs/) |

### Key Achievements
* Established complete Serverless Backend. Infrastructure scales down to zero when idle ($0.00 base cost).
