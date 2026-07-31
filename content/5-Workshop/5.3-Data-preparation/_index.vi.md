---
title : "Tiền xử lý dữ liệu"
date : 2026-06-15 
weight : 3
chapter : false
pre : " <b> 5.3. </b> "
---

Trong lĩnh vực chẩn đoán hình ảnh y tế (Medical Imaging), dữ liệu ảnh X-quang hoặc CT chụp từ các thiết bị khác nhau thường có kích thước, độ phân giải và cường độ sáng không đồng nhất. Nếu đưa trực tiếp dữ liệu thô này vào huấn luyện, mô hình AI sẽ hội tụ rất chậm hoặc suy giảm độ chính xác.

Do đó, trước khi đến bước Training, chúng ta cần một bước Tiền xử lý dữ liệu (Data Preparation / Preprocessing).

### 1. Amazon SageMaker Processing là gì?
Thay vì phải tự tạo máy ảo (EC2), tải dữ liệu từ S3 về, chạy code xử lý, rồi upload ngược lại lên S3 một cách thủ công, AWS cung cấp **Amazon SageMaker Processing**. 

Dịch vụ này cho phép chúng ta tự động hóa toàn bộ luồng trên:
1. SageMaker tự động bật một máy ảo (instance) tạm thời.
2. Tải dữ liệu hình ảnh thô (`toy_data`) từ S3 bucket xuống máy ảo.
3. Chạy đoạn mã xử lý dữ liệu của chúng ta (file `src/data/preprocessing.py`). Đoạn mã này sẽ làm nhiệm vụ thay đổi kích thước ảnh (resize), chuẩn hóa điểm ảnh (normalize pixel values) và chia tập dữ liệu thành các phần Train/Validation/Test.
4. Tải dữ liệu đã xử lý xong lên lại một thư mục đích trên S3.
5. Tự động tắt máy ảo để tiết kiệm chi phí.

### 2. Thực thi Data Pipeline trên CloudShell

Chúng ta đã định nghĩa toàn bộ cấu hình hạ tầng cho bước này trong file kịch bản `pipelines/run_processing_job.py`. Để kích hoạt quá trình xử lý, bạn hãy quay lại môi trường **AWS CloudShell**.

Thực thi lệnh sau:

```bash
python pipelines/run_processing_job.py
```

Khi lệnh được thực thi, AWS SageMaker Python SDK sẽ đóng gói file preprocessing.py, gửi yêu cầu khởi tạo Processing Job lên AWS và in ra các dòng log tiến trình (Provisioning instances, Downloading data, Running processing script, v.v.).

*Quá trình này có thể mất từ 3 đến 5 phút tùy thuộc vào lượng dữ liệu và thời gian khởi tạo máy ảo của AWS.*

Sau khi hoàn tất, bạn sẽ thấy dữ liệu đã được xử lý và lưu trữ trong S3 bucket của bạn. Bạn có thể kiểm tra bằng cách truy cập vào S3 bucket và xác nhận rằng các tập dữ liệu Train, Validation và Test đã được tạo ra đúng cách.

![Hoàn tất bước tiền xử lý dữ liệu](/images/5-Workshop/5.3-Data-preparation/run-processing-job.png)

### 3. Kiểm tra kết quả trên AWS Console
Để quan sát trực quan những gì hệ thống MLOps vừa thực hiện ngầm, chúng ta có thể kiểm tra trực tiếp trên giao diện AWS.

Kiểm tra SageMaker Processing Job:
Truy cập vào dịch vụ Amazon SageMaker -> Ở menu bên trái, chọn mục Processing -> Processing jobs. Bạn sẽ thấy một Job mới vừa được tạo ra với trạng thái là Completed (Đã hoàn thành).

![Kiểm tra Processing Job trên AWS Console](/images/5-Workshop/5.3-Data-preparation/sagemaker-processing-job.png)

Kiểm tra dữ liệu đầu ra trên Amazon S3:
Tiếp tục truy cập vào dịch vụ Amazon S3 và mở Bucket chứa dữ liệu của dự án. Lúc này, bạn sẽ thấy hệ thống tự động tạo ra một thư mục mới (ví dụ: processed_data hoặc cấu trúc thư mục chứa train, validation, test). Đây chính là dữ liệu "sạch" đã sẵn sàng cho khâu huấn luyện.

![Kiểm tra dữ liệu đầu ra trên Amazon S3](/images/5-Workshop/5.3-Data-preparation/s3-processed-data.png)

Với dữ liệu đã được chuẩn hóa thành công và lưu trữ an toàn trên S3, pipeline của chúng ta đã hoàn tất pha tiền xử lý và sẵn sàng bước vào giai đoạn cốt lõi nhất: Huấn luyện mô hình.
