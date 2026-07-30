---
title : "Xây dựng API (API Setup)"
date : 2026-07-20
weight : 6
chapter : false
pre : " <b> 5.6. </b> "
---

Mặc dù mô hình của chúng ta đã được triển khai thành công trên SageMaker Serverless Endpoint, nhưng điểm cuối này mặc định chỉ có thể giao tiếp bên trong mạng nội bộ của AWS. Để ứng dụng phía người dùng (Frontend) có thể gửi ảnh lên chẩn đoán một cách bảo mật qua môi trường Internet, chúng ta cần xây dựng một lớp API trung gian.

### 1. Vai trò của AWS Lambda và Amazon API Gateway

Trong kiến trúc của dự án, chúng ta sử dụng bộ đôi dịch vụ Serverless kinh điển của AWS:
*   **AWS Lambda (Inference Function):** Đóng vai trò là một hàm xử lý logic trung gian. Khi nhận được hình ảnh X-quang/CT từ người dùng, Lambda sẽ tiền xử lý nhanh bức ảnh, định dạng lại payload cho phù hợp và gửi yêu cầu (Invoke) tới SageMaker Endpoint. Sau khi SageMaker trả về kết quả, Lambda sẽ định dạng lại kết quả thành JSON để gửi về cho ứng dụng.
*   **Amazon API Gateway:** Cung cấp một URL RESTful API công khai để Frontend gọi vào. API Gateway cũng đảm nhiệm việc phân luồng (Routing) và có thể tích hợp với Amazon Cognito để chặn các yêu cầu không hợp lệ.

### 2. Khởi tạo API từ AWS CloudShell

Dự án đã tích hợp sẵn mã nguồn tự động hóa việc khởi tạo Lambda Function và API Gateway `setup_serverless_api.py`.

Hãy quay trở lại terminal của **AWS CloudShell** và chạy lệnh sau:

```bash
python pipelines/setup_serverless_api.py
```

Phần này sẽ sử dụng AWS SDK (Boto3) để:

1. Đóng gói mã nguồn của hàm Lambda.

2. Cấp phát quyền (IAM Role) cho phép Lambda được quyền gọi SageMaker Endpoint.

3. Tạo REST API trên API Gateway và thiết lập đường dẫn kết nối với hàm Lambda vừa tạo.

4. Triển khai (Deploy) API và in ra màn hình URL hoàn chỉnh.

Sau khi run lệnh `python pipelines/setup_serverless_api.py` trên CloudShell. Đợi script chạy xong và in ra dòng chứa URL của API Gateway.

![URL API Gateway](/images/5-Workshop/5.6-API-setup/setup-api.png)

### 3. Kiểm tra tài nguyên trên AWS Console
Để chắc chắn mọi thứ đã được thiết lập đúng như kiến trúc, chúng ta sẽ đi kiểm tra 2 dịch vụ này.

* **Kiểm tra AWS Lambda:**
Mở dịch vụ AWS Lambda trên console, chọn Functions. Bạn sẽ thấy một hàm mới vừa được tạo ra (ví dụ: PulmonaryInferenceFunction). Click vào hàm đó, bạn có thể xem phần mã nguồn Python làm nhiệm vụ giao tiếp với SageMaker.

![Kiểm tra Lambda Function](/images/5-Workshop/5.6-API-setup/lambda-function1.png)
![Kiểm tra Lambda Function](/images/5-Workshop/5.6-API-setup/lambda-function2.png)

* **Kiểm tra Amazon API Gateway:**
Mở dịch vụ API Gateway trên console. Bạn sẽ thấy một API mới (ví dụ: PulmonaryDiagnosticAPI). Click vào bên trong, bạn sẽ thấy cấu trúc đường dẫn (Ví dụ: phương thức POST tại resource /diagnose) đã được cấu hình để trỏ thẳng tới hàm Lambda.

![Kiểm tra API Gateway](/images/5-Workshop/5.6-API-setup/api-gateway.png)

*Bây giờ chúng ta đã có một đường dẫn URL API hoàn chỉnh. Bước cuối cùng của dự án là tích hợp URL này vào Giao diện Web Frontend để người dùng trực tiếp trải nghiệm tính năng chẩn đoán AI!*