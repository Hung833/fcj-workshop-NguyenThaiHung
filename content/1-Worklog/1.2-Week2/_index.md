---
title: "Week 2 Worklog"
date: 2026-06-08
weight: 2
chapter: false
pre: " <b> 1.2. </b> "
---

### Week 2 Objectives:
* Preprocess data. Since the original dataset was too large and costly for Cloud execution, the team decided to construct a compact "Toy Dataset".
* Re-architect the system into a Serverless design to minimize server maintenance expenses.

### Implemented Tasks:
| Day | Task | Completion Date |
| --- | --- | --- |
| Mon (06/08) | Finalized the new architecture: Utilizing API Gateway + Lambda to invoke SageMaker instead of loading model files directly on the app. | 06/08/2026 |
| Tue (06/09) | Divided tasks: One member wrote the Python script `create_toy_dataset.py` to randomly sample 120 X-ray images, while the other managed S3 bucket creation. | 06/09/2026 |
| Wed (06/10) | Executed data splitting script (100 Training images, 20 Test/Val images evenly distributed across 2 classes). | 06/10/2026 |
| Thu (06/11) | Provisioned the S3 bucket `fcaj-pulmonary-suite-data-hung2026` via AWS CLI. | 06/11/2026 |
| Fri (06/12) | Pushed the entire Toy Dataset to S3. Started drafting Blog Post 1 for submission to the portal. | 06/12/2026 |

### Key Achievements:
* Successfully staged the downscaled dataset on S3. Training now takes only 1–2 minutes, allowing flexible code testing at a cost under $0.50.
* Finalized the Serverless system architecture design and submitted Blog Post 1 on schedule.
