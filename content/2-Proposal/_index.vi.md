---
title: "Bản đề xuất"
date: 2026-06-01
weight: 2
chapter: false
pre: " <b> 2. </b> "
---

# AI Pulmonary Diagnostic Suite  
## Giải pháp AI hỗ trợ chẩn đoán bệnh lý phổi tự động hóa trên nền tảng AWS MLOps  

### 1. Tóm tắt dự án (Executive Summary)
**AI Pulmonary Diagnostic Suite** là một nền tảng trí tuệ nhân tạo (AI) được thiết kế chuyên biệt để hỗ trợ các bác sĩ chẩn đoán hình ảnh phát hiện sớm các bệnh lý về phổi (Pulmonary diseases) thông qua ảnh chụp X-quang/CT. Dự án ứng dụng sức mạnh của học sâu (Deep Learning) kết hợp với kiến trúc **AWS MLOps** hiện đại. Bằng việc sử dụng hoàn toàn các dịch vụ AWS có khả năng mở rộng như Amazon SageMaker, Amazon S3, và AWS Lambda, giải pháp mang lại quy trình tự động hóa từ khâu xử lý dữ liệu, huấn luyện mô hình, tinh chỉnh siêu tham số (HPO) cho đến triển khai suy luận không máy chủ (Serverless Inference), giúp tối ưu hóa chi phí và đảm bảo độ chính xác cao trong y tế.

### 2. Tuyên bố vấn đề (Problem Statement)
**Thực trạng:**  
Việc phân tích số lượng lớn ảnh chụp X-quang/CT phổi hàng ngày đòi hỏi rất nhiều thời gian và công sức của đội ngũ y bác sĩ, đồng thời tiềm ẩn rủi ro sai sót do yếu tố chủ quan hoặc quá tải công việc. Việc triển khai các mô hình AI y tế hiện tại thường thiếu một pipeline chuẩn hóa (CI/CD/CT), dẫn đến khó khăn trong việc cập nhật mô hình, quản lý phiên bản và tốn kém chi phí duy trì máy chủ suy luận (Inference Server) khi không có request.

**Giải pháp đề xuất:**  
Xây dựng một hệ thống MLOps end-to-end trên AWS:
*   Sử dụng **Amazon S3** làm Data Lake lưu trữ tập dữ liệu hình ảnh y tế.
*   Sử dụng **Amazon SageMaker** để thực hiện các luồng: Tiền xử lý dữ liệu, Huấn luyện mô hình (Training), và Tinh chỉnh siêu tham số (Hyperparameter Optimization - HPO).
*   Quản lý vòng đời mô hình thông qua **SageMaker Model Registry**.
*   Triển khai mô hình dưới dạng **SageMaker Serverless Endpoint** để tự động thu phóng (scale-to-zero) giúp tiết kiệm chi phí.
*   Xây dựng API suy luận thông qua **Amazon API Gateway** và **AWS Lambda**.

**Lợi ích mang lại:**  
*   **Tối ưu hóa quy trình y tế:** Hỗ trợ bác sĩ khoanh vùng và chẩn đoán nhanh chóng, giảm thiểu thời gian chờ đợi của bệnh nhân.
*   **Tối ưu chi phí (Cost Optimization):** Áp dụng kiến trúc Serverless Inference, hệ thống chỉ tính phí khi có yêu cầu chẩn đoán hình ảnh thực tế, loại bỏ chi phí duy trì máy chủ 24/7.
*   **Tự động hóa hoàn toàn:** Các pipeline được định nghĩa dưới dạng mã (Pipelines as Code), cho phép dễ dàng tái huấn luyện và triển khai khi có dữ liệu bệnh nhân mới.

### 3. Kiến trúc hệ thống (Solution Architecture)

Hệ thống được thiết kế theo chuẩn AWS Well-Architected Framework, tập trung vào Pillar Machine Learning và Serverless.

![AI Pulmonary Architecture](static/images/2-Proposal/mlops_architecture.png)

**Danh mục AWS Services & Chức năng:**
*   **Amazon S3:** Lưu trữ dữ liệu thô (toy_data), dữ liệu đã qua tiền xử lý, và các Model Artifacts (file `.tar.gz`) sau khi huấn luyện.
*   **Amazon SageMaker Processing:** Chạy các script tiền xử lý hình ảnh (`preprocessing.py`).
*   **Amazon SageMaker Training & HPO:** Quản lý tài nguyên tính toán (EC2 instances) để huấn luyện mô hình (`train.py`) và tìm ra bộ tham số tốt nhất.
*   **SageMaker Model Registry:** Đăng ký và quản lý phiên bản các mô hình đã được xác duyệt.
*   **SageMaker Serverless Inference:** Điểm cuối (Endpoint) cung cấp khả năng dự đoán thời gian thực mà không cần quản lý máy chủ.
*   **AWS Lambda & API Gateway:** Tạo RESTful API nhận hình ảnh từ phía Client, gọi đến SageMaker Endpoint và trả về kết quả chẩn đoán.

### 4. Triển khai kỹ thuật (Technical Implementation)

Quá trình triển khai được module hóa thành các kịch bản (Pipelines) thực thi tuần tự:
*   **Data Pipeline:** Thực thi script `run_processing_job.py` để làm sạch, resize và chuẩn hóa ảnh X-quang/CT.
*   **Training Pipeline:** Thực thi `run_training_job.py` và `run_hpo_job.py` để phân bổ tài nguyên huấn luyện tự động.
*   **Deployment Pipeline:** Script `repack_and_deploy.py` và `deploy_serverless_endpoint.py` tự động đóng gói mô hình và cập nhật lên Serverless Endpoint mà không gây gián đoạn (Zero downtime).
*   **Monitoring:** Thu thập và kiểm tra logs hệ thống qua `fetch_logs_v2.py` và `inspect_logs_all.py` trên Amazon CloudWatch.

### 5. Lộ trình triển khai (Roadmap & Milestones)

*   **Giai đoạn 1:** Phân tích dữ liệu y tế, thiết lập kho lưu trữ S3, xây dựng kịch bản `preprocessing.py` và tạo tập dữ liệu mẫu (`create_toy_dataset.py`).
*   **Giai đoạn 2:** Phát triển mô hình Deep Learning (`train.py`), thiết lập các job huấn luyện và HPO trên Amazon SageMaker.
*   **Giai đoạn 3:** Xây dựng MLOps Pipelines (Đăng ký mô hình, đóng gói artifact, khởi tạo Serverless Endpoint).
*   **Giai đoạn 4:** Thiết lập API Gateway, AWS Lambda kết nối với Endpoint. Kiểm thử toàn trình (End-to-end testing) và đánh giá độ chính xác.

### 6. Ước tính ngân sách (Budget Estimation)

Kiến trúc ứng dụng Serverless Inference và Managed Training Jobs giúp kiểm soát ngân sách rất hiệu quả. Chi phí chủ yếu phát sinh trong quá trình huấn luyện mô hình.

**Chi phí AWS ước tính:**
*   **Amazon S3:** ~$1.00/tháng (Lưu trữ dataset và model artifacts).
*   **SageMaker Training Jobs:** Phụ thuộc vào số giờ chạy thực tế của các máy ảo GPU (VD: `ml.g4dn.xlarge`). Ước tính ~$10 - $20 cho giai đoạn phát triển.
*   **SageMaker Serverless Inference:** Tính phí theo miligiây tính toán và lượng dung lượng RAM cấp phát (Chỉ phát sinh khi gọi API chẩn đoán). ~$1.00 - $3.00/tháng cho môi trường lab.
*   **API Gateway & AWS Lambda:** Nằm trong AWS Free Tier (Rất rẻ).

### 7. Quản trị rủi ro (Risk Management)

| Rủi ro (Risk) | Xác suất | Mức độ ảnh hưởng | Chiến lược giảm thiểu (Mitigation Strategy) |
| :--- | :--- | :--- | :--- |
| **Model Drift (Mô hình giảm độ chính xác)** | Trung bình | Cao | Thiết lập SageMaker Model Monitor. Xây dựng pipeline tự động tái huấn luyện khi có dữ liệu mới. |
| **Bảo mật dữ liệu y tế (PHI)** | Thấp | Nghiêm trọng | Mã hóa dữ liệu At-Rest trên S3 (KMS). Đảm bảo giao tiếp API mã hóa In-Transit (TLS/SSL). Tuân thủ nguyên tắc IAM chặt chẽ. |
| **Thời gian khởi động lạnh (Cold Start) của Endpoint** | Cao | Trung bình | Sử dụng script `warmup_endpoint.py` để giữ endpoint luôn sẵn sàng hoặc Provisioned Concurrency nếu cần độ trễ thấp tuyệt đối. |
| **Chi phí Training vượt kiểm soát** | Thấp | Trung bình | Thiết lập AWS Budgets, cấu hình `MaxRuntimeInSeconds` cho các Training/HPO Jobs để ngắt tự động. |

### 8. Kết quả kỳ vọng (Expected Outcomes)
Hoàn thành một hệ thống chẩn đoán y tế tự động chuẩn Cloud-Native. Dự án không chỉ dừng lại ở một mô hình AI đơn lẻ mà hình thành một **quy trình MLOps hoàn chỉnh**. Kết quả cung cấp một API chẩn đoán phổi có độ sẵn sàng cao, mở ra tiềm năng tích hợp vào các ứng dụng Web/App của các bệnh viện hoặc phòng khám trong thực tế.
