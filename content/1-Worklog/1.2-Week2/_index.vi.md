---
title: "Tuần 2"
date: 2026-06-08
weight: 2
chapter: false
pre: " <b> 1.2. </b> "
---

### Mục tiêu tuần 2
* Tạo tập data nhỏ (Toy Dataset) để train thử nghiệm cho tiết kiệm tiền AWS.
* Hoàn thành bài Blog công nghệ đầu tiên nộp lên hệ thống.

### Tiến độ công việc
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Nhóm chốt kiến trúc: Chuyển sang làm Serverless toàn bộ (API Gateway + Lambda + SageMaker) để tối ưu chi phí. | 08/06/2026 | 08/06/2026 | [AWS Serverless Architecture](https://aws.amazon.com/serverless/) |
| 3 | - Mình nhận task code Python script `create_toy_dataset.py` để random lấy 120 ảnh X-Quang phổi cân bằng các class. | 09/06/2026 | 09/06/2026 | [Python Pandas Docs](https://pandas.pydata.org/docs/) |
| 4 | - Run script chia data, check lại folder Train/Val.<br>- Bạn cùng nhóm tạo S3 bucket. | 10/06/2026 | 10/06/2026 | [Amazon S3 User Guide](https://docs.aws.amazon.com/AmazonS3/latest/userguide/) |
| 5 | - Mình dùng AWS CLI để sync (push) toàn bộ Toy Dataset lên S3 bucket của dự án. | 11/06/2026 | 11/06/2026 | [AWS CLI S3 Commands](https://docs.aws.amazon.com/cli/latest/reference/s3/) |
| 6 | - Cả nhóm viết và format bài Blog số 1 về "Kiến trúc Serverless MLOps" để submit. | 12/06/2026 | 12/06/2026 | [Quy định FCAJ Blog](https://cloudjourney.awsstudygroup.com/) |

### Thành tựu đạt được
* Có sẵn tập data thu gọn trên S3. Việc này giúp việc test code sau này chỉ tốn 1-2 phút, đảm bảo FinOps.
* Bài Blog 1 hoàn thành đúng deadline.
