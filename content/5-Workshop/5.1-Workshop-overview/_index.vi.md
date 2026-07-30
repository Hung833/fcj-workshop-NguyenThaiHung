---
title : "Giới thiệu"
date : 2026-06-01 
weight : 1
chapter : false
pre : " <b> 5.1. </b> "
---

#### Kiến trúc MLOps Serverless là gì?
Trong các dự án AI y tế thông thường, việc duy trì một máy chủ dự đoán (Inference Server như Amazon EC2) chạy 24/7 sẽ gây lãng phí tài nguyên và tốn kém rất nhiều chi phí, đặc biệt là khi lượng yêu cầu chẩn đoán hình ảnh từ các phòng khám không diễn ra liên tục.

Để giải quyết bài toán này, trong dự án **AI Pulmonary Diagnostic Suite**, team mình quyết định sử dụng kiến trúc **Serverless Inference** (Suy luận phi máy chủ) thông qua nền tảng Amazon SageMaker. 
Hiểu đơn giản là: mô hình AI của chúng ta sẽ được "ngủ đông" (scale về 0) khi không có người sử dụng. Chỉ khi nào có bác sĩ tải ảnh X-quang/CT lên hệ thống để yêu cầu chẩn đoán, điểm cuối (endpoint) mới được kích hoạt, thực hiện suy luận và tính phí theo từng mili-giây xử lý. Bằng cách kết hợp **Amazon SageMaker**, **AWS Lambda**, **Amazon API Gateway** và **Amazon S3**, chúng ta có một hệ thống AI linh hoạt, có thể tự động mở rộng theo tải và tối ưu hóa hóa đơn AWS một cách triệt để.

#### Tổng quan về Workshop
Ở bài workshop này, mình sẽ hướng dẫn các bạn cách tự tay build lại hệ thống **AI Pulmonary Diagnostic Suite** từ khâu chuẩn bị dữ liệu đến khi triển khai một API chẩn đoán hoàn chỉnh.

Chúng ta sẽ đi qua các phần chính sau:
+ **Tạo Data Lake & Xử lý dữ liệu:** Tạo Amazon S3 bucket để chứa dữ liệu hình ảnh phổi thô (`toy_data`) và cấu hình các tác vụ tiền xử lý dữ liệu.
+ **Huấn luyện mô hình AI:** Thiết lập các Amazon SageMaker Training Job để huấn luyện mô hình Deep Learning.
+ **Triển khai Serverless Endpoint:** Lưu trữ Model Artifacts và triển khai mô hình tự động lên SageMaker Serverless Endpoint.
+ **Tạo Backend API:** Viết hàm AWS Lambda và móc nối với API Gateway để tạo cổng REST API, làm nhiệm vụ nhận ảnh và trả về kết quả chẩn đoán phổi.
+ **Giao diện Web & Xác thực:** Đưa mã nguồn trang web Next.js lên AWS Amplify cho bác sĩ thao tác, đồng thời sử dụng Amazon Cognito để bảo mật và quản lý quyền truy cập.

*(Lưu ý: Quá trình huấn luyện mô hình trên SageMaker có thể yêu cầu tài nguyên máy ảo GPU/CPU và phát sinh chi phí. Hãy đảm bảo bạn theo dõi ngân sách và nhớ làm tới bước cuối cùng là xóa tài nguyên (Clean-up) để không bị AWS trừ tiền ngoài ý muốn nhé!)*

![Tổng quan kiến trúc dự án](/images/5-Workshop/5.1-Workshop-overview/diagram1.png)
