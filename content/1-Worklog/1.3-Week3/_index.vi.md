---
title: "Worklog Tuần 3"
date: 2026-06-15
weight: 3
chapter: false
pre: " <b> 1.3. </b> "
---

### Mục tiêu tuần 3:
* Khởi chạy quy trình tiền xử lý dữ liệu và trích xuất đặc trưng (Data Preprocessing & Feature Engineering) trên đám mây bằng cách chuyển cấu trúc lệnh cục bộ sang Amazon SageMaker Processing Job.
* Đồng bộ hóa và quản lý tập trung toàn bộ dữ liệu thô và dữ liệu đã qua xử lý trên kho lưu trữ đối tượng Amazon S3.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Tách mã nguồn tiền xử lý dữ liệu ảnh X-Quang thành file thực thi Python độc lập `preprocessing.py` thích hợp với môi trường container.<br>- Định nghĩa cấu trúc phân mục lưu trữ đầu ra cho dữ liệu trên S3. | 15/06/2026 | 15/06/2026 | Amazon SageMaker Developer Guide |
| 3 | - Thiết lập và phân quyền cho IAM Execution Role cho phép SageMaker có toàn quyền truy cập đọc/ghi dữ liệu trên S3 Bucket đã tạo.<br>- Khởi tạo môi trường làm việc tích hợp trên SageMaker Studio. | 16/06/2026 | 16/06/2026 | AWS IAM Permissions Reference |
| 4 | - Cấu hình và khởi chạy SageMaker Processing Job sử dụng SDK Python, chỉ định sử dụng Instance Type tối ưu chi phí (`ml.m5.xlarge`) để xử lý tệp mã nguồn `preprocessing.py`. | 17/06/2026 | 17/06/2026 | SageMaker Python SDK API |
| 5 | - Giám sát tiến độ thực thi tác vụ tiền xử lý, kiểm tra định dạng dữ liệu đầu ra và cấu trúc phân mảnh dữ liệu (Train/Test/Validation) tự động kết xuất về lại S3 bucket. | 18/06/2026 | 18/06/2026 | AWS SageMaker Console |
| 6 | - Đánh giá hiệu năng và chi phí tiêu thụ của tác vụ tiền xử lý đám mây.<br>- Bắt đầu phác thảo cấu trúc đề cương cho bài viết Blog công nghệ thứ hai. | 19/06/2026 | 19/06/2026 | AWS Cost Explorer |

### Kết quả đạt được tuần 3:
* Di chuyển thành công logic tiền xử lý ảnh từ máy trạm cục bộ lên hạ tầng điện toán đám mây phân tán của SageMaker Processing Job.
* Toàn bộ tệp ảnh X-Quang phổi thử nghiệm (Toy Dataset) đã được chuẩn hóa kích thước, tăng cường dữ liệu nền (Data Augmentation) và lưu trữ tự động vào các thư mục `/train`, `/test`, `/validation` biệt lập trên Amazon S3.
* Cấu hình thành công quyền kiểm soát IAM Role chuẩn xác, đảm bảo SageMaker Studio giao tiếp bảo mật tuyệt đối với tài nguyên lưu trữ đối tượng S3.
* Khống chế thời gian xử lý dữ liệu hình ảnh trên Cloud hoàn tất trong vòng dưới 3 phút với mức chi phí hạ tầng tối ưu.
