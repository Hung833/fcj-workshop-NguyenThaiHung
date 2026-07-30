---
title: "Tuần 6"
date: 2026-07-06
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---

### Mục tiêu tuần 6
* Quản lý phiên bản mô hình bằng SageMaker Model Registry để chuẩn bị đem đi Deploy.

### Tiến độ công việc
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Mình tạo Model Package Group tên là `Pulmonary-Diagnostic-Models` trên SageMaker. | 06/07/2026 | 06/07/2026 | [SageMaker Model Registry](https://docs.aws.amazon.com/sagemaker/latest/dg/model-registry.html) |
| 3 | - Dùng code Python (boto3) để register model tốt nhất từ đợt HPO tuần trước vào Registry. | 07/07/2026 | 07/07/2026 | [Boto3 ModelPackage API](https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/sagemaker.html) |
| 4 | - Cấu hình quy trình duyệt. Chuyển status của version này sang `Approved` để đánh dấu sẵn sàng lên Production. | 08/07/2026 | 08/07/2026 | [MLOps Model Approval](https://docs.aws.amazon.com/sagemaker/latest/dg/model-registry-approve.html) |
| 5 | - Nhóm bắt đầu viết file `inference.py` (Custom Handler) để xử lý logic nhận ảnh Base64 từ Frontend gửi xuống. | 09/07/2026 | 09/07/2026 | [SageMaker Inference Toolkit](https://github.com/aws/sagemaker-inference-toolkit) |
| 6 | - Review chéo lại đoạn code xử lý array numpy trong file inference để chống lỗi tràn RAM. | 10/07/2026 | 10/07/2026 | [NumPy Memory Management](https://numpy.org/doc/stable/user/basics.html) |

### Thành tựu đạt được
* Model đã được đánh version (v1) và quản lý tập trung, chuyên nghiệp. Không còn lưu file lung tung trong ổ cứng.
