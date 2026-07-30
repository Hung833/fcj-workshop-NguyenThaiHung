---
title: "Tuần 7"
date: 2026-07-13
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---

### Mục tiêu tuần 7
* Deploy mô hình lên Serverless Endpoint để tối ưu chi phí.
* Dựng tầng kết nối Backend bằng API Gateway và Lambda.

### Tiến độ công việc
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Mình nén lại model kèm file `requirements.txt` (bổ sung Pillow, numpy) để lúc deploy server cài đủ thư viện. | 13/07/2026 | 13/07/2026 | [Python PIP Packaging](https://packaging.python.org/en/latest/) |
| 3 | - Chạy code deploy tạo SageMaker Serverless Endpoint V2. Cấu hình RAM 2GB. | 14/07/2026 | 14/07/2026 | [SageMaker Serverless Inference](https://docs.aws.amazon.com/sagemaker/latest/dg/serverless-endpoints.html) |
| 4 | - Cả nhóm code hàm AWS Lambda. Mình gắn biến môi trường `ENDPOINT_NAME` và cấp quyền IAM Role cho Lambda. | 15/07/2026 | 15/07/2026 | [AWS Lambda Env Vars](https://docs.aws.amazon.com/lambda/latest/dg/configuration-envvars.html) |
| 5 | - Setup API Gateway, map với hàm Lambda, cấu hình POST method `/predict`. | 16/07/2026 | 16/07/2026 | [API Gateway REST APIs](https://docs.aws.amazon.com/apigateway/latest/developerguide/apigateway-rest-api.html) |
| 6 | - Team dùng cURL bắn ảnh test thử vào API. Kết quả trả về JSON mượt mà. | 17/07/2026 | 17/07/2026 | [cURL Documentation](https://curl.se/docs/) |

### Thành tựu đạt được
* Dựng xong Backend Serverless hoàn chỉnh. Khi không có request, máy chủ tự tắt, hóa đơn AWS = $0.00.
