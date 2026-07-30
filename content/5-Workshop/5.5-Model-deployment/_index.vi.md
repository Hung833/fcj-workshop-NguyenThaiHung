---
title : "Triển khai mô hình"
date : 2026-07-13 
weight : 5
chapter : false
pre : " <b> 5.5. </b> "
---

Thành quả của quá trình huấn luyện là một tệp mô hình (Model Artifacts) đã được nén lại (`model.tar.gz`) và lưu trữ an toàn trên Amazon S3. Tuy nhiên, để các ứng dụng Web hoặc App của bác sĩ có thể gửi ảnh chụp X-quang/CT mới lên và nhận về kết quả chẩn đoán, chúng ta cần triển khai (deploy) mô hình này thành một API điểm cuối (Endpoint).

### 1. Tại sao lại chọn Amazon SageMaker Serverless Inference?

Thông thường, việc duy trì một máy chủ dự đoán (Real-time Inference Instance) chạy 24/7 sẽ rất tốn kém, đặc biệt là khi phòng khám không có bệnh nhân liên tục. 

Trong dự án này, chúng ta ứng dụng **SageMaker Serverless Inference**. Cơ chế tuyệt vời của Serverless mang lại các lợi ích:
*   **Tự động thu phóng (Auto-scaling):** Tự động cấp phát tài nguyên tính toán khi có request gửi đến và scale về 0 (ngủ đông) khi không có ai sử dụng.
*   **Tối ưu chi phí:** Bạn chỉ phải trả tiền cho thời gian (tính bằng mili-giây) và dung lượng bộ nhớ mà hệ thống thực sự xử lý để đưa ra kết quả chẩn đoán.

### 2. Triển khai từ AWS CloudShell

Dự án đã chuẩn bị sẵn các kịch bản MLOps để tự động hóa khâu triển khai này. Hãy quay lại terminal của **AWS CloudShell** và chạy lệnh sau để thiết lập Serverless Endpoint:

```bash
python pipelines/deploy_serverless_endpoint.py
```

Hệ thống sẽ tự động thực hiện 3 việc:

1. Đăng ký mô hình (Tạo SageMaker Model trỏ đến file .tar.gz trên S3).

2. Tạo cấu hình điểm cuối (Endpoint Configuration) với loại Serverless (quy định dung lượng RAM tối đa và số lượng request đồng thời).

3. Triển khai Endpoint thực tế.

*Lưu ý: Quá trình triển khai Endpoint có thể mất khoảng 3 đến 5 phút để AWS cấu hình tài nguyên ngầm.*

Sau khi kịch bản hoàn tất, bạn sẽ thấy thông báo thành công và tên Endpoint được tạo ra. Hãy ghi nhớ tên này để sử dụng trong bước kiểm tra API.

![Thông báo triển khai Endpoint thành công](/images/5-Workshop/5.5-Model-deployment/run-deploy-endpoint.png)

### 3. Kiểm tra Endpoint trên AWS Console
Để đảm bảo Endpoint của chúng ta đã sẵn sàng phục vụ:

* **Bước 1:** Từ AWS Console, mở dịch vụ Amazon SageMaker.
* **Bước 2:** Ở menu bên trái, cuộn xuống mục Inference và chọn Endpoints.
* **Bước 3:** Bạn sẽ thấy tên Endpoint của dự án vừa được tạo ra. Khi cột Status chuyển sang trạng thái InService (màu xanh lá), điều đó có nghĩa là API chẩn đoán phổi của bạn đã hoàn toàn sẵn sàng nhận request!

![Kiểm tra trạng thái Endpoint trên AWS Console](/images/5-Workshop/5.5-Model-deployment/sagemaker-endpoint-inservice.png)

*Mô hình AI đã được đưa lên môi trường Đám mây thành công với chi phí tối ưu nhất.*