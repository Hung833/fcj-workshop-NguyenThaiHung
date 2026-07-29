---
title: "Week 8 Worklog"
date: 2026-07-20
weight: 8
chapter: false
pre: " <b> 1.8. </b> "
---

### Week 8 Objectives:
* Set up automated operational error monitoring and alerts via Email.
* Consolidate manual execution scripts from Weeks 3–6 into a unified automated pipeline (MLOps).

### Implemented Tasks:
| Day | Task | Completion Date |
| --- | --- | --- |
| Mon (07/20) | Developed scripts creating CloudWatch Alarms tracking API Gateway 5xx errors, linking them to Amazon SNS for email notifications. | 07/20/2026 |
| Tue (07/21) | Conducted chaos testing via AWS CLI by injecting synthetic failure payloads to force alert generation. Email alerts were triggered successfully. | 07/21/2026 |
| Wed (07/22) | Resolved `sagemaker` SDK version conflicts by pinning version requirements to v2.x (`sagemaker<3.0`). | 07/22/2026 |
| Thu (07/23) | Developed `create_mlops_pipeline.py`, linking Training and Model Registration steps into an automated DAG. | 07/23/2026 |
| Fri (07/24) | Executed test runs of the Pipeline. AWS automatically allocated compute infrastructure, trained the model, and registered artifacts seamlessly. | 07/24/2026 |

### Key Achievements:
* Successfully automated the MLOps pipeline and integrated a free email alerting mechanism. Clean codebase with smooth execution.
