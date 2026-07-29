---
title: "Worklog Tuần 7"
date: 2026-07-13
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---

### Mục tiêu tuần 7:
* Triển khai model lên Serverless Endpoint để không tốn tiền nuôi server 24/7.
* Code Lambda và API Gateway để làm cổng giao tiếp an toàn.

### Các công việc triển khai:
| Thứ | Công việc | Hoàn thành |
| --- | --- | --- |
| 2 (13/07) | Viết script repack lại model, tự động nhúng `requirements.txt` (chứa numpy, Pillow) vào file tar.gz. | 13/07/2026 |
| 3 (14/07) | Chạy script deploy tạo SageMaker Serverless Endpoint V2. | 14/07/2026 |
| 4 (15/07) | Code file `lambda_function.py`. Set biến môi trường `ENDPOINT_NAME` cho Lambda để không phải hardcode. | 15/07/2026 |
| 5 (16/07) | Setup Amazon API Gateway, nối vào Lambda, tạo route `POST /predict`. | 16/07/2026 |
| 6 (17/07) | Test luồng API bằng lệnh `curl`. Hệ thống đã trả về kết quả JSON báo % xác suất viêm phổi ngon lành. | 17/07/2026 |

### Kết quả đạt được:
* Xây xong phần Backend Serverless cực kỳ tiết kiệm chi phí. Khi không ai xài, AWS tự tắt máy chủ, bill tự động về 0.
