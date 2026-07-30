---
title: "Tuần 8"
date: 2026-07-20
weight: 8
chapter: false
pre: " <b> 1.8. </b> "
---

### Mục tiêu tuần 8
* Setup cảnh báo lỗi qua Email (Monitoring).
* Gom tất cả script rời rạc thành MLOps Pipeline tự động.
* Viết bài Blog số 3.

### Tiến độ công việc
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Mình tạo SNS Topic và CloudWatch Alarm giám sát lỗi 5xx của API Gateway. Test báo động qua email thành công. | 20/07/2026 | 20/07/2026 | [Amazon CloudWatch & SNS](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/AlarmThatSendsEmail.html) |
| 3 | - Bắt tay làm Pipeline. Gom mã nguồn Processing và Training lại. | 21/07/2026 | 21/07/2026 | [SageMaker Pipelines SDK](https://sagemaker.readthedocs.io/en/stable/amazon_sagemaker_model_building_pipeline.html) |
| 4 | - Khắc phục lỗi đụng độ thư viện bằng cách ghim version `sagemaker<3.0`.<br>- Định nghĩa DAG gồm `TrainingStep` và `RegisterModelStep`. | 22/07/2026 | 22/07/2026 | [PIP Dependency Management](https://pip.pypa.io/en/stable/user_guide/) |
| 5 | - Kích hoạt Pipeline chạy thử. Theo dõi luồng DAG tự động trên giao diện SageMaker Studio. | 23/07/2026 | 23/07/2026 | [SageMaker Studio UI](https://docs.aws.amazon.com/sagemaker/latest/dg/pipelines-studio.html) |
| 6 | - Cả nhóm hoàn thiện bài Blog số 3 về "Tự động hóa MLOps" và submit. | 24/07/2026 | 24/07/2026 | [Quy định FCAJ Blog](https://cloudjourney.awsstudygroup.com/) |

### Thành tựu đạt được
* Đóng gói thành công hệ thống MLOps CI/CD. Chỉ cần 1 click là AWS tự động train và đẩy model mới.
* Hoàn thành xong chuỗi 3 bài Blog công nghệ của chương trình.
