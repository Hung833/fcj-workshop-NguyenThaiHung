---
title: "Week 7 Worklog"
date: 2026-07-13
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---

### Week 7 Objectives:
* Deploy the model onto a Serverless Endpoint to eliminate 24/7 idle server costs.
* Develop Lambda and API Gateway components to serve as a secure communication layer.

### Implemented Tasks:
| Day | Task | Completion Date |
| --- | --- | --- |
| Mon (07/13) | Wrote a model repackaging script to embed `requirements.txt` (containing numpy, Pillow) directly into `model.tar.gz`. | 07/13/2026 |
| Tue (07/14) | Executed deployment scripts provisioning a SageMaker Serverless Endpoint V2. | 07/14/2026 |
| Wed (07/15) | Developed `lambda_function.py`, setting `ENDPOINT_NAME` as an environment variable to prevent hardcoding. | 07/15/2026 |
| Thu (07/16) | Configured Amazon API Gateway, integrated it with Lambda, and created route `POST /predict`. | 07/16/2026 |
| Fri (07/17) | Tested the end-to-end API workflow using `curl`. The system returned JSON payloads with pneumonia probability percentages accurately. | 07/17/2026 |

### Key Achievements:
* Completed a highly cost-efficient Serverless Backend. When idle, AWS automatically spins down compute resources, reducing billing charges to zero.
