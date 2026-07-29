---
title: "Worklog Tuần 4"
date: 2026-06-22
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---

### Mục tiêu tuần 4:
* Viết code train mô hình DenseNet121 và chạy thử SageMaker Training Job.

### Các công việc triển khai:
| Thứ | Công việc | Hoàn thành |
| --- | --- | --- |
| 2 (22/06) | Một bạn chịu trách nhiệm viết file `train.py` dùng Keras/TensorFlow, nhận param truyền vào từ bên ngoài. | 22/06/2026 |
| 3 (23/06) | Bạn còn lại setup SageMaker Estimator trong file notebook, cấu hình image TensorFlow có sẵn của AWS. | 23/06/2026 |
| 4 (24/06) | Gắn input data từ S3 vào Estimator, bấm chạy Training Job. Chọn máy GPU `ml.p3.2xlarge` để train nhanh. | 24/06/2026 |
| 5 (25/06) | Mở CloudWatch Logs xem quá trình train, check các chỉ số Loss và Accuracy. | 25/06/2026 |
| 6 (26/06) | Vào S3 check file `model.tar.gz`. Xác nhận mô hình đã được train xong và đóng gói chuẩn. | 26/06/2026 |

### Kết quả đạt được:
* Container TensorFlow của AWS chạy mượt, không bị lỗi thư viện. File trọng số (weights) đã nằm gọn gàng trên S3 sẵn sàng cho các bước sau.
