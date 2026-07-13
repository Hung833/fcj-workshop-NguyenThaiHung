---
title: "Worklog Tuần 1"
date: 2026-06-01
weight: 1
chapter: false
pre: " <b> 1.1. </b> "
---

### Mục tiêu tuần 1:
* Kết nối, làm quen với các điều phối viên kỹ thuật tại đơn vị thực tập AWS Việt Nam và tìm hiểu lộ trình chương trình First Cloud AI Journey.
* Tiếp cận tài nguyên, tìm hiểu dịch vụ AWS cơ bản và các công cụ quản trị hệ thống đám mây bao gồm AWS Management Console và AWS CLI.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Tham gia buổi định hướng chương trình Workforce Bootcamp - FCAJ.<br>- Đọc và lưu ý các nội quy, quy định làm việc bảo mật thông tin nội bộ tại AWS Việt Nam. | 01/06/2026 | 01/06/2026 | Tài liệu tập huấn nội bộ AWS |
| 3 | - Tìm hiểu AWS và nhóm dịch vụ hạ tầng đám mây cốt lõi:<br>&emsp; + Compute (EC2)<br>&emsp; + Storage (S3)<br>&emsp; + Networking (VPC)<br>&emsp; + Identity & Access Management (IAM) | 02/06/2026 | 02/06/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 4 | - Kích hoạt tài khoản AWS Enterprise do chương trình cấp phát.<br>- Tìm hiểu giao diện AWS Management Console và cài đặt công cụ dòng lệnh AWS CLI v2 trên máy trạm cục bộ. | 03/06/2026 | 03/06/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 5 | - Nghiên cứu tài liệu về dịch vụ điện toán Amazon EC2 cơ bản:<br>&emsp; + Phân loại EC2 Instance types, AMI (Amazon Machine Image).<br>&emsp; + Cơ chế lưu trữ khối Elastic Block Store (EBS) và Elastic IP. | 04/06/2026 | 04/06/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 6 | - **Thực hành kỹ thuật:**<br>&emsp; + Cấu hình lệnh `aws configure` kết nối Access Key và Secret Key lên Cloud.<br>&emsp; + Khởi tạo thử nghiệm một thực thể EC2 Instance, gắn kèm EBS Volume và cấu hình remote kết nối qua giao thức SSH bảo mật. | 05/06/2026 | 05/06/2026 | <https://cloudjourney.awsstudygroup.com/> |

### Kết quả đạt được tuần 1:
* Nắm rõ quy trình vận hành hạ tầng đám mây AWS và cơ chế bảo mật dùng quyền truy cập tối thiểu (Least Privilege).
* Tài khoản hạ tầng AWS Enterprise được thiết lập bảo mật thành công bằng cơ chế xác thực đa yếu tố (MFA).
* Hoàn thành cấu hình AWS CLI v2 trên máy trạm cục bộ, kết nối thành công tới Region mặc định `ap-southeast-1` (Singapore).
* Thực thi các câu lệnh CLI cơ bản để truy vấn danh sách region, kiểm tra thông tin tài khoản và xác thực cấu hình đồng bộ hóa dữ liệu.
* Khởi tạo và kết nối SSH thành công vào EC2 instance, nắm rõ phương thức mở rộng dung lượng qua EBS volume.
