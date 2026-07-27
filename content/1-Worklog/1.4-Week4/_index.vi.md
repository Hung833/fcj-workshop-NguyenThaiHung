---
title: "Worklog Tuần 4"
date: 2026-06-22
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---

### Mục tiêu tuần 4:
* Triển khai tác vụ huấn luyện mô hình sâu (SageMaker Training Job) trên Cloud sử dụng Custom Script để huấn luyện cấu trúc mô hình DenseNet121 nhận diện viêm phổi.
* Quản lý luồng nạp dữ liệu huấn luyện đầu vào trực tiếp từ kênh dẫn lưu của Amazon S3.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Viết tệp lệnh huấn luyện mô hình Keras độc lập `train.py`, cấu hình cơ chế nhận tham số đầu vào (Hyperparameters) qua bộ phân tích luận lý của SageMaker. | 22/06/2026 | 22/06/2026 | TensorFlow AWS Deep Learning Containers |
| 3 | - Cấu hình SageMaker Estimator trong Studio, thiết lập định danh môi trường Framework (TensorFlow/Keras) và trỏ kênh dẫn dữ liệu đầu vào (Input Channels) đến các thư mục S3 đã tiền xử lý. | 23/06/2026 | 23/06/2026 | SageMaker Estimator API |
| 4 | - Khởi chạy tác vụ SageMaker Training Job trên một máy chủ ảo tối ưu hóa đồ họa GPU (`ml.p3.2xlarge`) để huấn luyện kiến trúc mạng DenseNet121 với tập dữ liệu rút gọn Toy Dataset. | 24/06/2026 | 24/06/2026 | AWS SageMaker Instance Pricing |
| 5 | - Theo dõi tiến độ hội tụ của hàm mất mát (Loss) và độ chính xác (Accuracy/Recall) thông qua luồng Log xuất trực tiếp từ Container về CloudWatch Logs. | 25/06/2026 | 25/06/2026 | Amazon CloudWatch Logs Console |
| 6 | - Kiểm tra và xác thực tệp mô hình kết xuất đầu ra được đóng gói tự động dưới dạng nén `model.tar.gz` đẩy ngược lưu trữ bảo mật trên phân mục S3 Out. | 26/06/2026 | 26/06/2026 | Dự án mã nguồn cá nhân & Hồ sơ MLOps |

### Kết quả đạt được tuần 4:
* Khởi chạy thành công quy trình huấn luyện mô hình học sâu thông qua Custom Script trên hạ tầng máy chủ ảo GPU của SageMaker Training Job.
* Mô hình mạng DenseNet121 nhận diện ảnh bệnh lý phổi hoàn tất chu kỳ huấn luyện một cách trơn tru, không phát sinh lỗi bất tương thích thư viện trong Docker Container.
* Hệ thống tự động thu thập và xuất bản toàn bộ chỉ số hiệu năng (Metrics) thời gian thực lên bảng điều khiển CloudWatch.
* Tệp trọng số đầu ra `model.tar.gz` chứa cấu trúc mạng của dự án được đóng gói chuẩn quy cách và lưu trữ an toàn trên Amazon S3 phục vụ cho việc deploy sau này.
