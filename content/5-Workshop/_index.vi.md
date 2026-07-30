---
title: "Workshop"
date: 2026-07-30
weight: 5
chapter: false
pre: " <b> 5. </b> "
---

# Triển khai hệ thống AI chẩn đoán bệnh lý phổi với kiến trúc Serverless MLOps

#### Tổng quan

**AI Pulmonary Diagnostic Suite** là một nền tảng trí tuệ nhân tạo (AI) được thiết kế chuyên biệt để hỗ trợ các bác sĩ chẩn đoán hình ảnh phát hiện sớm các bệnh lý về phổi thông qua ảnh chụp X-quang/CT.

Trong bài lab này, chúng ta sẽ thực hành xây dựng một quy trình MLOps hoàn chỉnh (end-to-end) trên AWS, từ khâu chuẩn bị dữ liệu đến khi triển khai một API chẩn đoán thực tế. Khác với các hệ thống truyền thống đòi hỏi máy chủ chạy 24/7 gây lãng phí, dự án này được thiết kế để tối ưu hóa chi phí triệt để.

Chúng ta sẽ kết hợp các dịch vụ cốt lõi của AWS để tạo ra một hệ thống tự động hóa và có khả năng tự động thu phóng (scale-to-zero):
+ **Amazon S3** - Đóng vai trò làm Hồ dữ liệu (Data Lake) an toàn để chứa dữ liệu hình ảnh phổi thô (toy dataset) và lưu trữ các tệp mô hình (Model Artifacts)[cite: 6].
+ **Amazon SageMaker** - Tự động hóa các tác vụ tiền xử lý dữ liệu, cấp phát tài nguyên huấn luyện mô hình (Training), và cung cấp Serverless Endpoint phục vụ suy luận phi máy chủ.
+ **AWS Lambda & Amazon API Gateway** - Đóng vai trò làm lớp API backend trung gian, tiếp nhận hình ảnh từ giao diện Web, xử lý và gọi đến SageMaker Endpoint để trả về kết quả chẩn đoán.

#### Nội dung

1. [Giới thiệu](5.1-Workshop-overview/)
2. [Các bước chuẩn bị](5.2-Prerequisite/)
3. [Tiền xử lý dữ liệu](5.3-Data-preparation/)
4. [Huấn luyện mô hình](5.4-Model-training/)
5. [Triển khai mô hình](5.5-Model-deployment/)
6. [Xây dựng API (API Setup)](5.6-API-setup/)
7. [Giao diện Web Frontend](5.7-Frontend/)