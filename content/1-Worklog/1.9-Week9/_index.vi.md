---
title: "Worklog Tuần 9"
date: 2026-07-27
weight: 9
chapter: false
pre: " <b> 1.9. </b> "
---

### Mục tiêu tuần 9:
* Tự động hóa toàn phần chuỗi quy trình Machine Learning (Tiền xử lý → Huấn luyện → Đăng ký mô hình) thành một pipeline duy nhất bằng SageMaker Pipelines.
* Định hình luồng MLOps CI/CD cơ bản (Continuous Integration / Continuous Training).

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Định nghĩa cấu trúc `ProcessingStep` kết nối mã nguồn tiền xử lý tuần 3 vào SageMaker Pipeline. | 27/07/2026 | 27/07/2026 | AWS SageMaker Pipelines SDK |
| 3 | - Thiết lập mã lệnh cấu hình `TrainingStep` (huấn luyện mạng DenseNet121) và liên kết biến số (Data Dependency) giữa các Steps. | 28/07/2026 | 28/07/2026 | Amazon SageMaker Automation |
| 4 | - Cấu hình `RegisterModelStep` để tự động hóa đăng ký mô hình vào Registry nếu thỏa mãn điều kiện độ chính xác đầu ra. | 29/07/2026 | 29/07/2026 | AWS MLOps Pipeline Reference |
| 5 | - Khởi tạo thực thể Pipeline hoàn chỉnh, biên dịch thành đồ thị DAG và chạy thử nghiệm (Execution) trên SageMaker Studio. | 30/07/2026 | 30/07/2026 | SageMaker Studio Pipeline DAG |
| 6 | - Xử lý các lỗi phân bổ quyền hạn tài nguyên giữa các Step (nếu có). Trích xuất mã nguồn Pipeline đẩy lên GitHub. | 31/07/2026 | 31/07/2026 | Nhật ký triển khai MLOps |

### Kết quả đạt được tuần 9:
* Chuyển đổi thành công các tác vụ kỹ thuật phân mảnh thành một DAG tự động hóa tuần tự khép kín, sẵn sàng chạy bằng 1 cú click chuột.
* Nâng tầm quy trình làm việc chuẩn doanh nghiệp, tiết kiệm hàng chục giờ thao tác thủ công.
