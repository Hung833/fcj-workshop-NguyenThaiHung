---
title : "Giao diện Web Frontend"
date : 2026-07-27
weight : 7
chapter : false
pre : " <b> 5.7. </b> "
---

Trong các hệ thống y tế thực tế, bác sĩ và nhân viên y tế không tương tác trực tiếp với các dòng lệnh hay API. Họ cần một giao diện trực quan, thân thiện để tải ảnh lên và xem kết quả. Đó là lý do chúng ta cần kết nối API vừa tạo với một ứng dụng Web Frontend.

### 1. Ứng dụng Web chẩn đoán (Diagnostic Web App)
Trong dự án này, giao diện người dùng được xây dựng gọn nhẹ bằng Python thông qua file mã nguồn `app.py`. Ứng dụng này sẽ cung cấp một trang web cho phép:
*   Tải lên hình ảnh X-quang hoặc CT của bệnh nhân.
*   Gửi dữ liệu ảnh qua API Gateway tới SageMaker Endpoint để xử lý.
*   Nhận kết quả từ AI và hiển thị trực quan đánh giá bệnh lý phổi lên màn hình.

### 2. Chạy ứng dụng từ AWS CloudShell
Để khởi chạy giao diện web, chúng ta sẽ thực thi file `app.py`. Tùy thuộc vào thư viện giao diện được sử dụng (như Streamlit hay Gradio), hệ thống sẽ tạo ra một máy chủ web cục bộ.

Hãy quay lại terminal của **AWS CloudShell** và chạy lệnh khởi động ứng dụng:

```bash
streamlit run app.py    
```

Sau khi chạy lệnh, bạn sẽ thấy một URL được in ra trên terminal. Đây là đường dẫn để truy cập vào giao diện web chẩn đoán AI.

![URL Streamlit](/images/5-Workshop/5.7-Frontend/url-streamlit.png)

### 3. Trải nghiệm tính năng chẩn đoán
Sau khi ứng dụng đã chạy, bạn có thể truy cập vào đường link web được cung cấp, giao diện chẩn đoán AI sẽ hiện ra.

Các bước thử nghiệm:

* Chuẩn bị một bức ảnh X-quang mẫu (ví dụ: tải file NORMAL2-IM-1252-0001.jpeg hoặc NORMAL2-IM-1116-0001-0002.jpeg từ thư mục toy_data/NORMAL/ về máy tính cá nhân của bạn). 

* Click vào nút Upload Image (Tải ảnh lên) trên giao diện web và chọn bức ảnh vừa tải về.

* Nhấn nút Chẩn đoán ngay (Serverless) để hệ thống gửi ảnh qua API.

* Chờ trong giây lát, kết quả dự đoán (Ví dụ: "Bình thường" hoặc "Dấu hiệu bệnh viêm phổi") cùng với độ tin cậy (Confidence Score) sẽ được hiển thị ngay trên màn hình.

![Màn hình chẩn đoán](/images/5-Workshop/5.7-Frontend/web1.png)
![Gửi yêu cầu tới AWS Serverless API](/images/5-Workshop/5.7-Frontend/web2.png)
![Hiển thị kết quả dự đoán](/images/5-Workshop/5.7-Frontend/web3.png)

*Như vậy, chúng ta đã hoàn thiện toàn bộ quy trình xây dựng hệ thống AI Pulmonary Diagnostic Suite từ khâu tiền xử lý dữ liệu, huấn luyện mô hình cho đến khi hình thành một sản phẩm Web App hoàn chỉnh có thể tương tác được trong thực tế!*

**Cảm ơn các bạn đã tham gia workshop và chúc các bạn thành công trong việc triển khai các dự án AI của riêng mình!**