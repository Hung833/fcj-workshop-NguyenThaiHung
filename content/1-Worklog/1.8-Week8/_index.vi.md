---
title: "Worklog Tuần 8"
date: 2026-07-20
weight: 8
chapter: false
pre: " <b> 1.8. </b> "
---

### Mục tiêu tuần 8:
* Setup cảnh báo lỗi tự động (Monitoring) qua Email.
* Gom tất cả các script chạy tay từ tuần 3 đến tuần 6 thành một Pipeline tự động duy nhất (MLOps).

### Các công việc triển khai:
| Thứ | Công việc | Hoàn thành |
| --- | --- | --- |
| 2 (20/07) | Viết script tạo CloudWatch Alarm đo lỗi 5xx của API Gateway, link với Amazon SNS để báo qua email. | 20/07/2026 |
| 3 (21/07) | Cố tình bơm lỗi giả lập (Chaos Testing) qua AWS CLI để ép hệ thống gửi email báo động. Email đã báo thành công. | 21/07/2026 |
| 4 (22/07) | Fix lỗi thư viện `sagemaker` bị đụng version, chốt cứng bản v2.x (`sagemaker<3.0`). | 22/07/2026 |
| 5 (23/07) | Code file `create_mlops_pipeline.py`. Nối bước Training và Register Model thành một DAG chạy tự động. | 23/07/2026 |
| 6 (24/07) | Bấm chạy thử Pipeline. AWS tự động cấp server, train xong tự đẩy lên Registry. Cực kỳ tiện lợi. | 24/07/2026 |

### Kết quả đạt được:
* Team đã tự động hóa xong quy trình MLOps và có cả hệ thống báo động qua mail miễn phí. Code sạch sẽ, chạy mượt.
