---
title: "Blog 2"
date: 2026-07-25
weight: 2
chapter: false
pre: " <b> 3.2. </b> "
---

# Xây Dựng MLOps Pipeline: Chuyển Dịch Dữ Liệu X-Quang Về S3 Và Tối Ưu Script Huấn Luyện DenseNet121 Trực Tiếp Trên Amazon SageMaker

Xin chào mọi người!

Sau khi đã hoàn thành bước thiết lập chốt chặn tài chính FinOps (AWS Budgets & CloudWatch Alarms) để đảm bảo an toàn ngân sách $200 credit, bước đi tiếp theo trong hành trình MLOps của dự án **AI Pulmonary Diagnostic Suite** là chuyển dịch toàn bộ quy trình xử lý dữ liệu và huấn luyện mô hình từ môi trường Kaggle/Local Notebook lên hạ tầng đám mây Amazon SageMaker.

Ở giai đoạn làm PoC/Research trước đây, mô hình chẩn đoán viêm phổi DenseNet121 được huấn luyện trực tiếp trên file Notebook cục bộ với toàn bộ 5.800 ảnh X-Quang. Tuy nhiên, khi đưa vào vận hành chuẩn doanh nghiệp (Production-grade), việc lưu trữ dữ liệu rải rác và chạy code thủ công lộ ra nhiều điểm yếu:

1. Không quản lý tập trung được dữ liệu ảnh y tế.
2. Thời gian thực thi của máy chủ tính toán kéo dài, gây tiêu tốn tài nguyên và tăng cước phí.
3. Code bị phụ thuộc vào môi trường máy cục bộ, khó đóng gói tự động hóa.

Trong bài viết hôm nay, mình xin chia sẻ giải pháp giải quyết dứt điểm các vấn đề trên bằng cách xây dựng Data & Training Pipeline tập trung trên AWS.

---

## 1. Kiến trúc lưu trữ và xử lý dữ liệu đám mây (Data Architecture)

Thay vì để dữ liệu nằm trực tiếp trong thư mục dự án của ứng dụng Web (`app.py`), toàn bộ ảnh X-Quang được tập trung về Amazon S3 – dịch vụ lưu trữ đối tượng đạt chuẩn bảo mật và tính sẵn sàng cao.

### Chiến lược tối ưu chi phí: Tập dữ liệu thu nhỏ (Toy Dataset Strategy)

Nếu đẩy toàn bộ 5.800 ảnh lên S3 và kích hoạt SageMaker Training Job chạy trong hàng giờ, số tiền credit sẽ vọt lên rất nhanh. Vì mục tiêu chính của dự án giai đoạn này là chứng minh và hoàn thiện luồng MLOps End-to-End chứ không sa đà vào việc nâng cao thêm từng % độ chính xác của mô hình, mình đã áp dụng kỹ thuật lấy mẫu (Sampling):

* Trích xuất một tập dữ liệu Toy Dataset siêu nhẹ gồm 100 ảnh train (50 ca Normal, 50 ca Pneumonia) và 20 ảnh val/test.
* Cấu hình cấu trúc S3 Bucket chuẩn mực:
  * `s3://ai-pulmonary-data-bucket/chest_xray/train/`
  * `s3://ai-pulmonary-data-bucket/chest_xray/test/`

> **Kết quả:** Thời gian tải dữ liệu và khởi tạo môi trường của SageMaker Processing/Training Job giảm từ 45 phút xuống chỉ còn 1.5 phút, tiết kiệm hơn 90% chi phí tính toán máy chủ mà vẫn kiểm thử trọn vẹn toàn bộ luồng pipeline!

---

## 2. Refactor mã nguồn: Chuyển đổi Notebook thành Custom Training Script

Khi huấn luyện trên SageMaker, hệ thống sẽ tự động khởi tạo một Container ảo hóa (Docker Container). Do đó, code huấn luyện mạng DenseNet121 (`ai-pulmonary-diagnostic-suite.ipynb`) cần được tái cấu trúc thành một file Python độc lập (`train.py`) với các điểm cải tiến cốt lõi:

### a. Đọc tham số truyền vào qua `argparse`

Môi trường SageMaker sẽ tự động truyền các biến đường dẫn dữ liệu và cấu hình siêu tham số (Hyperparameters) thông qua giao diện dòng lệnh (CLI):

```python
import argparse
import os

parser = argparse.ArgumentParser()

# Nhận siêu tham số
parser.add_argument('--epochs', type=int, default=2)
parser.add_argument('--batch_size', type=int, default=32)
parser.add_argument('--learning_rate', type=float, default=0.001)

# Nhận đường dẫn thư mục do SageMaker Container tự động gắn (Mount) từ S3
parser.add_argument('--train', type=str, default=os.environ.get('SM_CHANNEL_TRAIN'))
parser.add_argument('--test', type=str, default=os.environ.get('SM_CHANNEL_TEST'))
parser.add_argument('--model_dir', type=str, default=os.environ.get('SM_MODEL_DIR'))

args = parser.parse_args()
```
### b. Đóng gói mô hình lõi DenseNet121 & Fine-tuning
Logic xử lý ảnh và Transfer Learning từ mạng DenseNet121 được giữ nguyên tính hiệu quả, nhưng file trọng số xuất ra (model.tar.gz) được tự động lưu thẳng vào thư mục SM_MODEL_DIR để SageMaker tự đồng bộ về S3 ngay khi quá trình huấn luyện hoàn tất.

---

## 3. Thực thi SageMaker Training Job bằng Python SDK
Từ môi trường SageMaker Studio, mình gọi lệnh kích hoạt một lượt huấn luyện bằng SDK sagemaker.tensorflow.TensorFlow:

```python
from sagemaker.tensorflow import TensorFlow

# Cấu hình TensorFlow Estimator
tf_estimator = TensorFlow(
    entry_point='train.py',                 # File script huấn luyện vừa refactor
    role=role,                               # IAM Role phân quyền tối thiểu
    instance_count=1,                        # Sử dụng 1 instance
    instance_type='ml.m5.xlarge',           # Dòng máy CPU giá rẻ để tối ưu chi phí
    framework_version='2.13.0',
    py_version='py310',
    hyperparameters={
        'epochs': 2,                        # Chạy 2 epochs thử nghiệm luồng
        'batch_size': 16,
        'learning_rate': 0.001
    }
)

# Kích hoạt Training Job đọc trực tiếp dữ liệu từ S3
tf_estimator.fit({
    'train': 's3://ai-pulmonary-data-bucket/chest_xray/train',
    'test':  's3://ai-pulmonary-data-bucket/chest_xray/test'
})
```
---

## 4. Kết quả đạt được & Bài học MLOps
* **Tự động hóa hoàn toàn luồng I/O:** Dữ liệu tự động được kéo từ S3 vào Container, mô hình huấn luyện xong tự động đẩy file artifact về S3 mà không cần thao tác tải lên/xuống thủ công bằng tay.
* **Tối ưu chi phí tuyệt đối:** Nhờ kết hợp dòng máy ml.m5.xlarge giá rẻ và tập dữ liệu thu nhỏ, tổng chi phí cho mỗi lượt chạy Training Job chỉ tốn dưới $0.20 credit!
* **Sẵn sàng cho các bước tiếp theo:** Mô hình lưu trên S3 đã sẵn sàng để đăng ký phiên bản vào SageMaker Model Registry (Tuần 5) và mở Endpoint thời gian thực qua AWS Lambda + API Gateway ở Tuần 6.
* **Bài học rút ra:** Việc tách biệt giữa code logic huấn luyện (train.py) và hạ tầng tính toán (SageMaker Container) giúp mã nguồn trở nên sạch sẽ, bảo mật và dễ dàng mở rộng quy mô khi doanh nghiệp có thêm hàng vạn dữ liệu mới trong tương lai.

#AWS #AmazonSageMaker #MLOps #FinOps #AI #DeepLearning #DenseNet121 #DataScience #CloudComputing #FirstCloudJourney
