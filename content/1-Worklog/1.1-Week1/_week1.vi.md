---
title: "Worklog Tuần 1"
date: 2026-06-01
weight: 1
chapter: false
pre: " <b> 1.1. </b> "
---

### Mục tiêu tuần 1:
* Kết nối, làm quen với điều phối viên và các thành viên trong chương trình First Cloud AI Journey (FCAJ).
* Khởi tạo tài khoản AWS môi trường doanh nghiệp bảo mật, làm quen với giao diện AWS Management Console và cấu hình AWS CLI.
* Khảo sát kiến trúc mã nguồn và tệp trọng số huấn luyện sẵn `pneumonia_model_finetuned.keras` của dự án ứng dụng chẩn đoán bệnh phổi AI (AI Pulmonary Diagnostic Suite) để chuẩn bị sơ đồ chuyển dịch hạ tầng MLOps đám mây.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Tham gia buổi định hướng định kỳ (Orientation), làm quen với quy trình làm việc tại đơn vị thực tập AWS Việt Nam <br> - Nhận chỉ mục tài khoản hạ tầng đám mây cho chương trình FCAJ | 01/06/2026 | 01/06/2026 | Tài liệu tập huấn nội bộ AWS |
| 3 | - Nghiên cứu tài liệu dịch vụ hạ tầng AWS cốt lõi (Compute, Storage, Networking, Identity Access Management)<br> - Khảo sát kiến trúc mô hình học sâu CNN nhận diện viêm phổi từ tệp `pneumonia_model_finetuned.keras` của dự án | 02/06/2026 | 02/06/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 4 | - Kích hoạt tài khoản AWS Management Console <br> - Cấu hình chính sách bảo mật Multi-Factor Authentication (MFA) cho tài khoản Root <br> - Khởi tạo tài khoản phân quyền quản trị IAM User theo nguyên tắc đặc quyền tối thiểu (PoLP) | 03/06/2026 | 03/06/2026 | AWS IAM Best Practices Guide |
| 5 | - Cài đặt môi trường máy trạm cục bộ: AWS CLI v2, Python MLOps SDK, Docker Engine <br> - Thực hiện cấu hình định danh cặp khóa bảo mật `aws configure` (Access Key, Secret Key, Default Region `ap-southeast-1`) | 04/06/2026 | 04/06/2026 | <https://docs.aws.amazon.com/cli/> |
| 6 | - Kiểm tra tính toàn vẹn của kết nối đám mây qua lệnh CLI kiểm thử <br> - Tạo nhánh Git cục bộ và ánh xạ cấu trúc Workspace báo cáo mẫu `fcj-workshop-template-main` chuẩn bị cho các tài liệu kỹ thuật giai đoạn sau | 05/06/2026 | 05/06/2026 | Dự án mã nguồn cá nhân & Mẫu FCAJ |

### Kết quả đạt được tuần 1:
* **Hạ tầng đám mây an toàn:** Kích hoạt thành công tài khoản đám mây AWS phục vụ dự án, cấu hình chặn quyền Root thông qua MFA cứng để cô lập rủi ro an ninh thông tin.
* **Thiết lập định danh IAM:** Khởi tạo IAM User riêng cho vai trò MLOps Engineer với đầy đủ quyền hạn thao tác lập trình mà không cần can thiệp Root Credential.
* **Cấu hình AWS CLI v2 thành công:** Máy trạm cục bộ đã giao tiếp mượt mà với AWS API Gateway khu vực Singapore (`ap-southeast-1`), thực thi các lệnh truy vấn tài nguyên cơ bản ổn định.
* **Bàn giao không gian Workspace:** Cấu hình thành công bộ khung tĩnh Markdown từ template `fcj-workshop-template-main`, sẵn sàng đồng bộ hóa tiến độ cho lộ trình dịch chuyển mô hình phân tích ảnh X-quang phổi lên Amazon SageMaker đám mây trong các tuần tiếp theo.
