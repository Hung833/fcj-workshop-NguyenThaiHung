---
title: "Worklog Tuần 6"
date: 2026-07-06
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---

### Mục tiêu tuần 6:
* Đưa mô hình tốt nhất vào SageMaker Model Registry để quản lý phiên bản chuyên nghiệp.

### Các công việc triển khai:
| Thứ | Công việc | Hoàn thành |
| --- | --- | --- |
| 2 (06/07) | Tạo Model Package Group tên là `Pulmonary-Diagnostic-Models` trên giao diện Studio. | 06/07/2026 |
| 3 (07/07) | Dùng code Python (Boto3) đăng ký mô hình tốt nhất từ đợt HPO tuần trước vào Registry. | 07/07/2026 |
| 4 (08/07) | Đánh giá mô hình, chuyển status của model sang `Approved` để chuẩn bị cho việc Deploy. | 08/07/2026 |
| 5 (09/07) | Tạo file `inference.py` (Custom Handler) để chuẩn bị cho bước triển khai endpoint, xử lý vụ nhận ảnh Base64. | 09/07/2026 |
| 6 (10/07) | Review chéo (cross-check) lại code của nhau để đảm bảo file inference không bị bug. | 10/07/2026 |

### Kết quả đạt được:
* Mô hình đã được quản lý version đàng hoàng. File code `inference.py` đã sẵn sàng để tích hợp vào Endpoint.
