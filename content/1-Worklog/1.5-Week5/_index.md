---
title: "Week 5 Worklog"
date: 2026-06-29
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---

### Week 5 Objectives:
* Run Hyperparameter Optimization (HPO) jobs to let AWS automatically identify optimal model parameters instead of manual trial and error.

### Implemented Tasks:
| Day | Task | Completion Date |
| --- | --- | --- |
| Mon (06/29) | Defined Search Space parameters: Learning rate from `1e-5` to `1e-2`, Batch size set to 16 or 32. | 06/29/2026 |
| Tue (06/30) | Configured `HyperparameterTuner` in SageMaker targeting optimization of the Recall metric. | 06/30/2026 |
| Wed (07/01) | Triggered the HPO Job with a limit of 3 concurrent jobs to optimize execution time. | 07/01/2026 |
| Thu (07/02) | Analyzed job results. Selected the model candidate achieving the highest Recall score for project usage. | 07/02/2026 |
| Fri (07/03) | Authored and submitted Technical Blog Post 2 to the FCAJ portal. | 07/03/2026 |

### Key Achievements:
* Successfully identified the optimal parameter set without labor-intensive manual trials. Submitted Blog Post 2 on schedule.
