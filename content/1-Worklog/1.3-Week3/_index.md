---
title: "Week 3 Worklog"
date: 2026-06-15
weight: 3
chapter: false
pre: " <b> 1.3. </b> "
---

### Week 3 Objectives:
* Migrate local image processing code to run on Amazon SageMaker Processing Jobs.

### Implemented Tasks:
| Day | Task | Completion Date |
| --- | --- | --- |
| Mon (06/15) | Consolidated image resizing and color normalization logic into a standalone `preprocessing.py` file. | 06/15/2026 |
| Tue (06/16) | Created an IAM Role granting SageMaker read/write permissions to the project's S3 bucket. Provisioned SageMaker Studio. | 06/16/2026 |
| Wed (06/17) | Scripted the Processing Job execution sequence. Selected `ml.m5.xlarge` instance type for cost-effective and adequate performance. | 06/17/2026 |
| Thu (06/18) | Executed test Job runs. Monitored AWS Console to verify if data was correctly partitioned into `/train` and `/test` folders on S3. | 06/18/2026 |
| Fri (06/19) | Reviewed AWS Cost Explorer to ensure Job execution stayed strictly within budget limits. Drafted outline for Blog Post 2. | 06/19/2026 |

### Key Achievements:
* Completely eliminated the need for local data preprocessing. SageMaker automatically pulled images from S3, normalized them, and pushed clean output artifacts back to S3 within 3 minutes.
