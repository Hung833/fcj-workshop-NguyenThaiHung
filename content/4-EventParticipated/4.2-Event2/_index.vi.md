---
title: "Event 2"
date: 2026-06-11
weight: 1
chapter: false
pre: " <b> 4.2. </b> "
---

# BÁO CÁO TỔNG HỢP SỰ KIỆN CLOUD ARCHITECT & TECH TALK (11/06)

## 1. Mô Tả Ngắn Gọn Nội Dung Và Hoạt Động Chính Trong Sự Kiện
Sự kiện diễn ra với hai phần hoạt động chính: Trận Chung kết Cuộc thi Cloud Architect và Chuỗi bài thuyết trình chuyên sâu (Tech Talk) từ 3 speaker đại diện các doanh nghiệp công nghệ.

### A. Hoạt động 1: Chung kết Cuộc thi Cloud Architect (Giải Ao làng)
- **Hình thức:** Đấu trí trắc nghiệm tình huống kiến trúc đám mây giữa các đội thi xuất sắc nhất (nhóm KLK AST và nhóm Ngũ Đại Hiệp).
- **Nội dung xoay quanh:** Các bài toán thực tế trên AWS bao gồm:
  - Lựa chọn mô hình IaaS (EC2) và quy trình decommission/phế hủy thiết bị lưu trữ tuân thủ chuẩn an toàn.
  - Nguyên tắc phân quyền tối thiểu (Least Privilege) khi truy cập S3.
  - Giải pháp cân bằng tải lưu lượng UDP cho Game đa người chơi kết hợp cơ sở dữ liệu key-value (NLB + DynamoDB).
  - Tự động hóa khắc phục lỗi EC2 bằng CloudWatch Logs, Metric Filters & Alarms.
  - Phân phối nội dung bảo mật từ S3 qua CloudFront bằng Origin Access Control (OAC).
  - Thiết kế kết nối hybrid độ trễ thấp, băng thông cao giữa On-premises và nhiều VPC ở các vùng địa lý khác nhau (Direct Connect Gateway).
  - Di chuyển cơ sở dữ liệu MySQL dung lượng lớn (25TB) từ On-premises lên AWS với downtime tối thiểu (AWS DMS / DataSync / Aurora Replication).
  - Tự động hóa cập nhật AMI/EC2 bằng CloudFormation kết hợp Systems Manager Parameter Store.

### B. Hoạt động 2: Chuỗi chia sẻ chuyên môn từ các Speaker

#### Topic 1: Ứng dụng AI trong Bảo mật Đám mây với AWS Security Agent
*(Speaker: Anh Thịnh - DevOps/DevSecOps Engineer)*
- Phân tích hạn chế của hoạt động Pentest truyền thống (chi phí cao $5,000–$20,000/lần, phụ thuộc con người, tốn thời gian).
- Giới thiệu AWS Security Agent ứng dụng Multi-agent AI / Bedrock để tự động hóa: Design Security Review (đánh giá tài liệu theo chuẩn PCI-DSS, Well-Architected Framework), Code Review (tích hợp CI/CD, Pull Request trên GitHub/GitLab), và Pentest hệ thống.
- Chỉ ra giới hạn thực tế của công cụ: Chưa hỗ trợ tự động xử lý các luồng xác thực MFA phức tạp (SSO, OTP qua Email) hay các giao thức đặc thù như mTLS.

#### Topic 2: Quản trị SLA & Hệ thống Monitoring trong Thực tế Doanh nghiệp
*(Speaker: Anh Nam - Infrastructure/Reliability Engineer)*
- Giải thích tầm quan trọng của SLA (Service Level Agreement) và trách nhiệm đảm bảo cam kết với khách hàng.
- Làm rõ góc nhìn: Hạ tầng khỏe (Healthy Infrastructure) chưa chắc đã đem lại trải nghiệm người dùng tốt (Healthy UX) nếu ứng dụng lỗi kết nối logic.
- Chu trình quản trị rủi ro: Identify Risk → Monitor Signal → Response (SOP/SNS) → Log & Improve.
- Demo thực tế: Dựng Dashboard CloudWatch và cấu hình cảnh báo mất kết nối giữa EC2 (Back-end) và RDS PostgreSQL qua AWS SNS.

#### Topic 3: Lộ trình & Bí quyết Ôn luyện Chứng chỉ AWS Certified Cloud Practitioner (CLF-C02)
*(Speaker: Anh Huy)*
- Tổng quan hệ thống chứng chỉ AWS (Foundational, Associate, Professional, Specialty).
- Cấu trúc đề thi CLF-C02: 65 câu trắc nghiệm, 120 phút (bao gồm 30 phút bổ sung cho thí sinh không dùng tiếng Anh bản ngữ), điểm đạt 700/1000, giá trị 3 năm ($100 lệ phí).
- Tỷ trọng 4 miền kiến thức: Cloud Concepts (24%), Security & Compliance (30%), Cloud Technology & Services (34%), Billing & Pricing (12%).
- Mẹo thi thực tế: Phương pháp loại trừ (Elimination), Mapped Keywords, thực hành trên AWS Free Tier và kỹ thuật đánh dấu câu hỏi (Flag for Review).

## 2. Kết Quả Và Giá Trị Đạt Được

### A. Kiến thức & Bài học chuyên môn
- **Kiến trúc & Hạ tầng Cloud:** Hiểu rõ cách phối hợp các dịch vụ nâng cao của AWS (Direct Connect, CloudFront OAC, Auto Scaling, SQS, DMS) để giải quyết các bài toán hạ tầng quy mô lớn, tính sẵn sàng cao (HA) và chi phí tối ưu.
- **Tự động hóa Bảo mật (DevSecOps):** Tiếp cận xu hướng ứng dụng Generative AI / Multi-agent vào việc rà soát lỗ hổng mã nguồn và thiết kế hệ thống ngay từ giai đoạn lập kế hoạch (Design phase).
- **Tư duy Vận hành Doanh nghiệp (SRE/Reliability):** Nhận thức sâu sắc rằng mục tiêu của Monitoring không chỉ là giữ cho Server "xanh" mà là đảm bảo tính liên tục của luồng nghiệp vụ người dùng (Customer Journey) và tuân thủ cam kết SLA.

### B. Kỹ năng mới tích lũy
- **Thực hành Cấu hình Giám sát:** Biết cách tự custom Metric Alarms trên CloudWatch, thiết lập ma trận cảnh báo qua AWS SNS và liên kết kiểm tra kết nối giữa các tầng EC2 – RDS.
- **Kỹ năng Ôn thi Chứng chỉ Quốc tế:** Nắm vững chiến thuật phân tích từ khóa (Keywords), phương pháp loại trừ phương án sai và cách phân bổ thời gian hiệu quả cho kỳ thi AWS Practitioner/Associate.

## 3. Tổng Kết Sự Tham Gia Thực Tế & Kinh Nghiệm Tích Lũy
- **Thẩm thấu trải nghiệm thực tế:** Việc tham dự trực tiếp giúp đối chiếu giữa lý thuyết học thuật với các bài toán sự cố thực tế tại doanh nghiệp (như việc sập kết nối giữa Back-end và Database, sự cố do script chạy lỗi, hay nguy cơ đền bù hợp đồng khi vi phạm SLA).
- **Rèn luyện kỹ năng mềm:** Tích lũy kỹ năng quan sát, tư duy phản biện khi phân tích các đáp án kiến trúc đám mây trong phần thi trắc nghiệm; đồng thời học hỏi phong cách truyền đạt, demo xử lý sự cố trực tiếp (live troubleshooting) từ các kỹ sư giàu kinh nghiệm.
- **Định hướng phát triển bản thân:** Định hình rõ đường lối học tập công nghệ Cloud/DevOps, chuẩn bị lộ trình chinh phục các chứng chỉ AWS để làm đẹp hồ sơ chuyên môn và gia tăng lợi thế cạnh tranh nghề nghiệp.

![Event2](/images/4-EventParticipated/event_11-6-26/1.jpg)
![Event2](/images/4-EventParticipated/event_11-6-26/2.jpg)
![Event2](/images/4-EventParticipated/event_11-6-26/3.jpg)
![Event2](/images/4-EventParticipated/event_11-6-26/4.jpg)
![Event2](/images/4-EventParticipated/event_11-6-26/5.jpg)
![Event2](/images/4-EventParticipated/event_11-6-26/6.jpg)
![Event2](/images/4-EventParticipated/event_11-6-26/7.jpg)
![Event2](/images/4-EventParticipated/event_11-6-26/8.jpg)