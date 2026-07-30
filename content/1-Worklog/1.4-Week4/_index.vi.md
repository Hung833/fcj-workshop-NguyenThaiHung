---
title: "Tuần 4"
date: 2026-06-22
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---

### Mục tiêu tuần 4
* Train mô hình AI (DenseNet121) bằng SageMaker Training Job với cục data đã xử lý tuần trước.

### Tiến độ công việc
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Mình code file `train.py` dùng Keras, setup dùng `argparse` để nhận hyperparameter từ bên ngoài truyền vào. | 22/06/2026 | 22/06/2026 | [TensorFlow API Docs](https://www.tensorflow.org/api_docs) |
| 3 | - Khởi tạo SageMaker TensorFlow Estimator. Chỉ định đường dẫn data đầu vào từ S3. | 23/06/2026 | 23/06/2026 | [SageMaker TensorFlow Estimator](https://sagemaker.readthedocs.io/en/stable/frameworks/tensorflow/sagemaker.tensorflow.html) |
| 4 | - Bấm chạy Training Job. Chọn máy GPU `ml.p3.2xlarge` để train cho nhanh. | 24/06/2026 | 24/06/2026 | [Amazon EC2 Instance Types](https://aws.amazon.com/ec2/instance-types/) |
| 5 | - Monitor quá trình train qua CloudWatch Logs.<br>- Fix vài bug lặt vặt về đường dẫn OS path trong container. | 25/06/2026 | 25/06/2026 | [SageMaker Training Logs](https://docs.aws.amazon.com/sagemaker/latest/dg/logging-cloudwatch.html) |
| 6 | - Lên S3 check output. Xác nhận file `model.tar.gz` đã được sinh ra thành công. | 26/06/2026 | 26/06/2026 | [SageMaker Model Output](https://docs.aws.amazon.com/sagemaker/latest/dg/your-algorithms-training-algo-output.html) |

### Thành tựu đạt được
* AWS đã train xong model AI đầu tiên của nhóm. File trọng số (weights) được đóng gói đúng chuẩn SageMaker và lưu an toàn trên S3.
