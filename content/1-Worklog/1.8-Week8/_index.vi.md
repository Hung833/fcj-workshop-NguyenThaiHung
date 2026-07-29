---
title: "Worklog Tuần 8"
date: 2026-07-20
weight: 8
chapter: false
pre: " <b> 1.8. </b> "
---

### Mục tiêu tuần 8:
* Thiết lập hệ thống giám sát hiệu năng (Performance Monitoring) tinh gọn, miễn phí dựa trên Amazon CloudWatch thay vì SageMaker Model Monitor.
* Thiết lập hệ thống cảnh báo vận hành (Alarms) phát hiện lỗi 5xx, 4xx và độ trễ (Latency).
* Hoàn thiện bài viết truyền thông công nghệ số 3 (Blog 3).

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Nghiên cứu hệ thống CloudWatch Metrics mặc định của API Gateway và Lambda (Invocations, Errors, Duration). | 20/07/2026 | 20/07/2026 | Amazon CloudWatch Metrics |
| 3 | - Thiết lập CloudWatch Alarms: Cấu hình gửi thông báo khẩn cấp qua Amazon SNS khi tỷ lệ lỗi (Error Rate) vượt ngưỡng 5% hoặc độ trễ vượt 5 giây. | 21/07/2026 | 21/07/2026 | Amazon CloudWatch Alarms |
| 4 | - Kiểm thử hệ thống báo động bằng cách bắn lưu lượng dữ liệu rác (Payload giả) để ép hệ thống tạo log lỗi và kích hoạt Alarm. | 22/07/2026 | 22/07/2026 | Nhật ký vận hành hệ thống |
| 5 | - Thực hiện viết bài viết công nghệ số 3 với tiêu đề: "Chiến lược giám sát Serverless AI chi phí 0 đồng trên AWS bằng CloudWatch". | 23/07/2026 | 23/07/2026 | Quy định viết bài AWS |
| 6 | - Tối ưu hóa lại toàn bộ cấu trúc thư mục dự án (Clean Code), gom nhóm các scripts MLOps chuẩn bị cho bước xây dựng Pipeline. | 24/07/2026 | 24/07/2026 | Tiêu chuẩn Enterprise MLOps |

### Kết quả đạt được tuần 8:
* Xây dựng thành công lá chắn giám sát sức khỏe API hoàn toàn tự động và bảo vệ chi phí FinOps (miễn phí 100%).
* Quản trị rủi ro chủ động thông qua hệ thống cảnh báo thời gian thực (Real-time Alerting) của Amazon SNS.
* Bài viết Blog công nghệ số 3 được hoàn thiện xuất sắc và định hình tư duy thực dụng (Pragmatic Engineering).
