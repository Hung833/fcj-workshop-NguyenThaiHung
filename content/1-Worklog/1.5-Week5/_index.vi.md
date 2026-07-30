---
title: "Tuần 5"
date: 2026-06-29
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---

### Mục tiêu tuần 5
* Chạy HPO (Hyperparameter Tuning) để máy tự dò bộ tham số tốt nhất cho model.
* Hoàn thiện bài Blog số 2.

### Tiến độ công việc
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Khai báo vùng tìm kiếm (Search Space) cho HPO: Learning rate (1e-5 đến 1e-2), Batch size (16 hoặc 32). | 29/06/2026 | 29/06/2026 | [SageMaker HPO Guide](https://docs.aws.amazon.com/sagemaker/latest/dg/automatic-model-tuning.html) |
| 3 | - Setup `HyperparameterTuner` trong code, đặt Objective Metric là tối đa hóa chỉ số Recall. | 30/06/2026 | 30/06/2026 | [Boto3 HyperparameterTuner API](https://sagemaker.readthedocs.io/en/stable/api/training/tuner.html) |
| 4 | - Run HPO Job. Config chạy tối đa 3 jobs song song để tiết kiệm thời gian chờ. | 01/07/2026 | 01/07/2026 | [AWS Tuning Best Practices](https://docs.aws.amazon.com/sagemaker/latest/dg/automatic-model-tuning-considerations.html) |
| 5 | - Job chạy xong. Nhóm phân tích biểu đồ trên SageMaker Studio, pick ra model có điểm Recall ngon nhất. | 02/07/2026 | 02/07/2026 | [SageMaker Studio Analytics](https://docs.aws.amazon.com/sagemaker/latest/dg/studio-analyze.html) |
| 6 | - Mình hoàn thành phần viết bài Blog 2 và submit lên hệ thống. | 03/07/2026 | 03/07/2026 | [Quy định FCAJ Blog](https://cloudjourney.awsstudygroup.com/) |

### Thành tựu đạt được
* Tìm được bộ tham số ưng ý nhất mà không cần ngồi sửa code chạy tay nhiều lần.
* Đăng tải thành công Blog công nghệ số 2.
