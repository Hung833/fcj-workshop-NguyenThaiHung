---
title: "Các bài blogs đã đăng"
date: 2026-07-27
weight: 3
chapter: false
pre: " <b> 3. </b> "
---

###  [Blog 1 - HÀNH TRÌNH FINOPS: QUẢN LÝ NGÂN SÁCH THÔNG MINH CHO DỰ ÁN AI TRỰC TUYẾN TRÊN AWS](3.1-Blog1/)
Blog này chia sẻ kinh nghiệm ứng dụng thực hành FinOps để quản lý chi phí cho dự án chẩn đoán hình ảnh y tế AI Pulmonary Diagnostic Suite trên AWS. Bài viết hướng dẫn chi tiết cách thiết lập kiến trúc phòng thủ chi phí đa lớp kết hợp giữa AWS Budgets, CloudWatch, SNS và chiến lược Toy Dataset giúp rút ngắn 95% thời gian chạy máy chủ SageMaker, đảm bảo toàn bộ dự án hoàn thành trọn vẹn trong ngân sách $200 credit.

###  [Blog 2 - XÂY DỰNG MLOPS PIPELINE: CHUYỂN DỊCH DỮ LIỆU X-QUANG VỀ S3 VÀ TỐI ƯU SCRIPT HUẤN LUYỆN DENSENET121 TRỰC TIẾP TRÊN AMAZON SAGEMAKER](3.2-Blog2/)
Blog này hướng dẫn cách chuyển dịch dữ liệu X-Quang từ môi trường cục bộ/Kaggle lên Amazon S3 và tái cấu trúc (refactor) Jupyter Notebook thành script huấn luyện độc lập (`train.py`). Thông qua việc sử dụng SageMaker Python SDK và áp dụng tập dữ liệu thu nhỏ (Toy Dataset), quy trình huấn luyện mạng DenseNet121 được tự động hóa hoàn toàn với chi phí chỉ dưới $0.20 credit cho mỗi lượt chạy Training Job.

###  [Blog 3 - TRIỂN KHAI API CHẨN ĐOÁN AI THỜI GIAN THỰC: ĐÓNG GÓI SAGEMAKER REAL-TIME ENDPOINT BẢO MẬT VỚI AWS LAMBDA VÀ AMAZON API GATEWAY](3.3-Blog3/)
Blog này giới thiệu giải pháp đóng gói mô hình AI thành REST API Serverless chuẩn doanh nghiệp để phục vụ suy luận thời gian thực (Real-time Inference). Bằng cách kết hợp SageMaker Real-Time Endpoint, AWS Lambda và Amazon API Gateway, hệ thống không chỉ bảo mật tuyệt đối trọng số mô hình mà còn tách biệt ứng dụng Web Streamlit khỏi hạ tầng AI, tối ưu hóa khả năng mở rộng và kiểm soát cước phí vận hành hiệu quả.
