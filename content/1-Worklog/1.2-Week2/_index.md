---
title: "Week 2"
date: 2026-06-08
weight: 2
chapter: false
pre: " <b> 1.2. </b> "
---

### Week 2 Objectives
* Generate a small dataset (Toy Dataset) for experimental training to optimize AWS costs.
* Complete and submit the first technical Blog post to the portal.

### Task Progress
| Day | Task | Start Date | Completion Date | Reference Sources |
| --- | --- | --- | --- | --- |
| Mon | - Team finalized architecture: Shifted entirely to Serverless (API Gateway + Lambda + SageMaker) to optimize operational costs. | 06/08/2026 | 06/08/2026 | [AWS Serverless Architecture](https://aws.amazon.com/serverless/) |
| Tue | - Assigned to write the `create_toy_dataset.py` Python script to randomly extract a class-balanced sample of 120 chest X-ray images. | 06/09/2026 | 06/09/2026 | [Python Pandas Docs](https://pandas.pydata.org/docs/) |
| Wed | - Executed data splitting script and verified Train/Val folder integrity.<br>- Teammate created the Amazon S3 bucket. | 06/10/2026 | 06/10/2026 | [Amazon S3 User Guide](https://docs.aws.amazon.com/AmazonS3/latest/userguide/) |
| Thu | - Used AWS CLI to sync (upload) the complete Toy Dataset to the project S3 bucket. | 06/11/2026 | 06/11/2026 | [AWS CLI S3 Commands](https://docs.aws.amazon.com/cli/latest/reference/s3/) |
| Fri | - Collaborated on writing and formatting Blog 1 on "Serverless MLOps Architecture" for submission. | 06/12/2026 | 06/12/2026 | [FCAJ Blog Guidelines](https://cloudjourney.awsstudygroup.com/) |

### Key Achievements
* Prepared downscaled dataset on S3. Subsequent code testing now takes only 1–2 minutes, ensuring FinOps compliance.
* Submitted Blog Post 1 on schedule.
