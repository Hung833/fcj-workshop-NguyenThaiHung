---
title: "Worklog Tuần 3"
date: 2026-06-15
weight: 3
chapter: false
pre: " <b> 1.3. </b> "
---

### Mục tiêu tuần 3:
* Mang code xử lý ảnh từ máy cá nhân lên chạy trên Amazon SageMaker Processing Job.

### Các công việc triển khai:
| Thứ | Công việc | Hoàn thành |
| --- | --- | --- |
| 2 (15/06) | Gom các logic resize ảnh, chuẩn hóa màu vào một file `preprocessing.py` riêng biệt. | 15/06/2026 |
| 3 (16/06) | Tạo IAM Role cấp quyền cho SageMaker được phép đọc/ghi vào bucket S3 của dự án. Mở SageMaker Studio. | 16/06/2026 |
| 4 (17/06) | Code kịch bản chạy Processing Job. Chọn máy `ml.m5.xlarge` để chạy cho rẻ và đủ dùng. | 17/06/2026 |
| 5 (18/06) | Chạy thử Job. Theo dõi trên AWS Console xem data có được chia đúng vào các folder `/train`, `/test` trên S3 không. | 18/06/2026 |
| 6 (19/06) | Check lại AWS Cost Explorer để đảm bảo Job chạy không bị lố tiền. Lên dàn ý cho bài Blog số 2. | 19/06/2026 |

### Kết quả đạt được:
* Không còn phải tiền xử lý data bằng máy cá nhân nữa. SageMaker đã tự động kéo ảnh từ S3, chuẩn hóa và đẩy ngược kết quả lên S3 sạch sẽ trong vòng 3 phút.
