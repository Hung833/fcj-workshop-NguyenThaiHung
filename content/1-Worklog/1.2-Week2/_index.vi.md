---
title: "Worklog Tuần 2"
date: 2026-06-08
weight: 2
chapter: false
pre: " <b> 1.2. </b> "
---

### Mục tiêu tuần 2:
* Xử lý lại data. Data gốc lớn quá sẽ tốn tiền Cloud, nên nhóm quyết định tạo một tập "Toy Dataset" nhỏ gọn.
* Lên ý tưởng lại kiến trúc hệ thống sang dạng Serverless để đỡ tốn tiền duy trì server.

### Các công việc triển khai:
| Thứ | Công việc | Hoàn thành |
| --- | --- | --- |
| 2 (08/06) | Chốt kiến trúc mới: Dùng API Gateway + Lambda gọi qua SageMaker thay vì load file model thẳng trên app. | 08/06/2026 |
| 3 (09/06) | Chia việc: Một bạn viết code Python `create_toy_dataset.py` lấy random 120 ảnh X-Quang, bạn kia lo tạo bucket S3. | 09/06/2026 |
| 4 (10/06) | Chạy script chia data (100 ảnh Train, 20 ảnh Test/Val chia đều cho 2 class). | 10/06/2026 |
| 5 (11/06) | Dùng lệnh AWS CLI tạo S3 bucket `fcaj-pulmonary-suite-data-hung2026`. | 11/06/2026 |
| 6 (12/06) | Push toàn bộ Toy Dataset lên S3. Nhóm bắt đầu viết bài Blog 1 nộp lên hệ thống. | 12/06/2026 |

### Kết quả đạt được:
* Có sẵn tập data rút gọn trên S3. Từ giờ training chỉ mất 1-2 phút, giúp nhóm test code thoải mái mà chi phí chưa tới $0.50.
* Chốt xong bản thiết kế hệ thống Serverless và nộp bài Blog 1 đúng hạn.
