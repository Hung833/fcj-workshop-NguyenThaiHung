---
title : "Huấn luyện mô hình"
date : 2026-06-22 
weight : 4
chapter : false
pre : " <b> 5.4. </b> "
---

Sau khi dữ liệu đã được tiền xử lý và lưu trữ chuẩn hóa trên Amazon S3, bước tiếp theo trong quy trình MLOps là tiến hành Huấn luyện mô hình (Model Training). 

Đối với các bài toán phân tích hình ảnh y tế như X-quang/CT phổi, việc huấn luyện các mạng nơ-ron tích chập (CNN) thường đòi hỏi cấu hình phần cứng mạnh mẽ (đặc biệt là GPU). Nếu tự xây dựng máy chủ, chúng ta sẽ tốn rất nhiều chi phí đầu tư và bảo trì.

### 1. Cơ chế Huấn luyện trên Amazon SageMaker
**Amazon SageMaker Training** cung cấp một giải pháp hạ tầng quản lý hoàn toàn (fully-managed). Cơ chế hoạt động của nó diễn ra như sau:
1. SageMaker tự động cấp phát các máy ảo (EC2 Instances) có hiệu năng cao dựa trên cấu hình chúng ta yêu cầu.
2. Tải mã nguồn huấn luyện của chúng ta (file `src/train.py`) và tập dữ liệu từ S3 xuống máy ảo.
3. Thực thi quá trình huấn luyện mô hình.
4. Ngay khi hoàn thành, hệ thống sẽ đóng gói mô hình (Model Artifacts) và tự động tải ngược lên lại Amazon S3.
5. Cuối cùng, SageMaker lập tức dọn dẹp và tắt máy ảo, giúp chúng ta **chỉ phải trả tiền cho số giây thực tế mà máy ảo chạy**.

### 2. Kích hoạt Training Pipeline từ CloudShell
Thay vì thao tác thủ công trên giao diện web, chúng ta sẽ tự động hóa việc khởi tạo luồng huấn luyện này bằng script `run_training_job.py`.

Hãy quay trở lại màn hình terminal của **AWS CloudShell** và chạy lệnh sau:

```bash
python pipelines/run_training_job.py
```

Khi kịch bản được kích hoạt, SageMaker sẽ bắt đầu khởi tạo tài nguyên và quá trình huấn luyện sẽ được bắt đầu.
Sau khi quá trình huấn luyện hoàn tất, bạn sẽ thấy thông báo kết thúc và mô hình huấn luyện sẽ được lưu trữ trên S3.

![Thông báo huấn luyện mô hình thành công](/images/5-Workshop/5.4-Model-training/run-training-job.png)

*(Lưu ý: Quá trình huấn luyện mô hình AI có thể tốn từ vài phút đến vài chục phút tùy thuộc vào lượng dữ liệu (toy_data) và loại instance bạn sử dụng. Nhưng ở đây chúng ta để tiết kiệm thời gian nên chỉ training 120 ảnh tiêu biểu).*

### 3. Kiểm tra tiến trình và kết quả trên AWS Console
Trong quá trình đợi lệnh trên CloudShell hoàn tất, bạn có thể kiểm tra trực tiếp tiến trình trên giao diện AWS.

* **Theo dõi SageMaker Training Job:**
Từ AWS Console, mở dịch vụ Amazon SageMaker. Ở menu bên trái, chọn Training -> Training jobs. Bạn sẽ thấy danh sách các tác vụ huấn luyện.

Khi tác vụ hoàn tất, trạng thái của nó sẽ chuyển sang Completed.

* **Kiểm tra Model Artifact trên S3:**
Mô hình sau khi huấn luyện xong không nằm lại trên máy ảo mà đã được nén lại thành một file .tar.gz an toàn trên S3.
Tiếp tục truy cập vào dịch vụ Amazon S3, tìm đến bucket của dự án và mở thư mục đầu ra của quá trình huấn luyện (thường là folder output/). Bạn sẽ thấy file model.tar.gz. Đây chính là thành quả của chúng ta!

![Thông báo huấn luyện mô hình trên SageMaker trên S3](/images/5-Workshop/5.4-Model-training/aws-run-training-job.png)

*Mô hình học sâu chẩn đoán phổi của bạn giờ đây đã sẵn sàng để được đăng ký (Model Registry) và triển khai thành API (Deployment)!*
