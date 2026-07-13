---
title: "Worklog Tuần 2"
date: 2026-06-08
weight: 2
chapter: false
pre: " <b> 1.2. </b> "
---

### Mục tiêu tuần 2:
* Xây dựng giải pháp dữ liệu thử nghiệm rút gọn (Toy Dataset) từ tập dữ liệu X-Quang phổi gốc nhằm khống chế hiệu quả hạn mức chi phí trên đám mây.
* Tái thiết kế kiến trúc phân phối, nâng cấp luồng suy luận sang mô hình Serverless phân tán, thay thế cho kiến trúc load file mô hình cục bộ không an toàn hiện tại.
* Lập đề cương kỹ thuật và hoàn thiện bài viết chuyên lập trình (Blog 1) nộp lên hệ thống quản lý học tập đám mây.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Đánh giá rủi ro an ninh hệ thống cũ từ file `app.py` đang load trực tiếp file Keras/TFLite.<br>- Thiết lập sơ đồ kiến trúc Serverless tích hợp mã hóa khóa nâng cao. | 08/06/2026 | 08/06/2026 | Sơ đồ giải pháp AWS Architecture |
| 3 | - Phác thảo cấu trúc chuỗi 3 bài viết công nghệ phục vụ tiêu chí đánh giá của FCAJ.<br>- Hoàn thiện nội dung chi tiết bài Blog 1: "Xây dựng hạ tầng MLOps Serverless và tối ưu hóa chi phí trên AWS". | 09/06/2026 | 09/06/2026 | Quy định viết bài AWS Study Group |
| 4 | - Lập trình script Python `create_toy_dataset.py` thực hiện phân tách lấy mẫu ngẫu nhiên cân bằng 120 ảnh X-quang phổi (100 Train, 20 Test/Val chia đều cho 2 lớp bệnh lý). | 10/06/2026 | 10/06/2026 | Tài liệu Python Data Science |
| 5 | - Khởi tạo tài nguyên lưu trữ Amazon S3 Buckets (`fcj-pulmonary-suite-data-2026`) thông qua giao diện dòng lệnh AWS CLI.<br>- Kiểm thử tính toàn vẹn của tệp lệnh trích xuất dữ liệu cục bộ. | 11/06/2026 | 11/06/2026 | Amazon S3 Developer Guide |
| 6 | - Đồng bộ hóa toàn bộ cấu trúc thư mục dữ liệu Toy Dataset lên Cloud qua AWS CLI S3 commands.<br>- Phát triển logic nhúng Metadata chữ ký số bản quyền vào module xuất báo cáo chẩn đoán lâm sàng để khẳng định bản quyền kỹ sư. | 12/06/2026 | 12/06/2026 | Mã nguồn phân hệ báo cáo dự án |

### Kết quả đạt được tuần 2:
* Phát triển thành công công cụ trích xuất dữ liệu tự động, thu gọn tập dữ liệu xuống 120 ảnh, giúp các tác vụ xử lý của SageMaker sau này hoàn tất chỉ trong 1-2 phút, giới hạn chi phí dưới $0.50 cho mỗi lượt chạy thử nghiệm.
* Phân định thành công không gian lưu trữ và hoàn tất đẩy kho ảnh X-Quang thử nghiệm lên Amazon S3 dưới cấu trúc lưu trữ phân cấp an toàn.
* Hoàn thiện bản thiết kế kiến trúc Serverless an toàn: Ứng dụng Streamlit gửi ảnh qua REST API của Amazon API Gateway, kích hoạt AWS Lambda lấy thông tin xác thực từ AWS Secrets Manager để gọi dự đoán bảo mật đến SageMaker Endpoint biệt lập.
* Module xuất bản kết quả lâm sàng được tích hợp thành công chuỗi Metadata định danh tác quyền cá nhân ("Báo cáo được xác thực bởi Kỹ sư AI Nguyễn Thái Hưng - Hệ thống AWS MLOps Suite").
* Bài viết Blog công nghệ số 1 được hoàn thiện đúng hạn, đạt các tiêu chí học thuật của AWS Study Group.
