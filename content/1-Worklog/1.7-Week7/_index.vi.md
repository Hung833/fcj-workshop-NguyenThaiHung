---
title: "Worklog Tuần 7"
date: 2026-07-13
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---

### Mục tiêu tuần 7:
* Triển khai mô hình AI lên hạ tầng bất biến (Immutable Infrastructure) bằng Amazon SageMaker Serverless Inference V2 để tối ưu hóa chi phí (FinOps).
* Thiết lập tầng giao tiếp API Serverless bằng Amazon API Gateway và AWS Lambda, quản lý cấu hình thông qua Biến môi trường (Environment Variables).

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Đóng gói Artifact mô hình chuẩn TensorFlow Serving (TFS), tự động hóa nạp thư viện `numpy`, `Pillow`, `requests` qua `requirements.txt` nhằm triệt tiêu lỗi thiếu Dependency. | 13/07/2026 | 13/07/2026 | AWS SageMaker Deployment |
| 3 | - Kích hoạt triển khai SageMaker Serverless Endpoint V2. Xây dựng script dọn dẹp tài nguyên (Self-cleanup) tránh lỗi ResourceInUse. | 14/07/2026 | 14/07/2026 | SageMaker Serverless Inference |
| 4 | - Lập trình hàm AWS Lambda (Python 3.12) nhận Base64, thiết lập IAM Role theo nguyên tắc Least Privilege để kết nối đến SageMaker Endpoint nội bộ. | 15/07/2026 | 15/07/2026 | AWS Lambda Developer Guide |
| 5 | - Khởi tạo Amazon API Gateway, cấu hình phương thức `POST /predict` và tích hợp với hàm Lambda, loại bỏ hoàn toàn mã hóa cứng (hardcode) qua biến môi trường. | 16/07/2026 | 16/07/2026 | Amazon API Gateway Guide |
| 6 | - Kiểm thử toàn trình (End-to-End) qua cURL, xác thực luồng dữ liệu Serverless trả về JSON dự đoán lâm sàng với độ trễ tối ưu. | 17/07/2026 | 17/07/2026 | Nhật ký kiểm thử hệ thống |

### Kết quả đạt được tuần 7:
* Chuyển đổi thành công sang kiến trúc Serverless 100%, bảo vệ ngân sách AWS ở mức $0.00 khi không có lưu lượng truy cập.
* Mã nguồn `inference.py` hoạt động ổn định như một Proxy giao tiếp với TFS C++ Engine, khắc phục triệt để các lỗi Crash ẩn.
* API Gateway và Lambda được thiết lập bảo mật, sẵn sàng tích hợp với Frontend (Web Streamlit).
