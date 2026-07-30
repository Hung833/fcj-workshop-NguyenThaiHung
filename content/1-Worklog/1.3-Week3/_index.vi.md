---
title: "Tuần 3"
date: 2026-06-15
weight: 3
chapter: false
pre: " <b> 1.3. </b> "
---

### Mục tiêu tuần 3
* Bưng code tiền xử lý dữ liệu (resize, normalize) lên chạy tự động trên Amazon SageMaker Processing Job.

### Tiến độ công việc
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Gom các hàm xử lý ảnh từ file Jupyter Notebook cũ vào một file `preprocessing.py` riêng biệt. | 15/06/2026 | 15/06/2026 | [Scikit-image Docs](https://scikit-image.org/docs/stable/) |
| 3 | - Setup IAM Role cho SageMaker để nó có quyền get ảnh từ S3 bucket.<br>- Mở SageMaker Studio test môi trường. | 16/06/2026 | 16/06/2026 | [SageMaker Execution Roles](https://docs.aws.amazon.com/sagemaker/latest/dg/sagemaker-roles.html) |
| 4 | - Viết script gọi SageMaker Processing Job. Config dùng máy `ml.m5.xlarge` cho rẻ. | 17/06/2026 | 17/06/2026 | [SageMaker Python SDK](https://sagemaker.readthedocs.io/en/stable/) |
| 5 | - Run Job. Ngồi canh log trên CloudWatch và check S3 xem data đã được xử lý và chia đúng thư mục chưa. | 18/06/2026 | 18/06/2026 | [Amazon CloudWatch Logs](https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/) |
| 6 | - Nhóm check lại AWS Cost Explorer xem hôm qua chạy Job tốn bao nhiêu tiền.<br>- Lên sườn bài cho Blog 2. | 19/06/2026 | 19/06/2026 | [AWS Billing Console](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/) |

### Thành tựu đạt được
* Đẩy thành công bước chuẩn bị dữ liệu lên Cloud. SageMaker tự lấy ảnh, xử lý và cất lại vào S3 trong chưa đầy 3 phút.
