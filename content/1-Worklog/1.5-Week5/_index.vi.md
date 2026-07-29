---
title: "Worklog Tuần 5"
date: 2026-06-29
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---

### Mục tiêu tuần 5:
* Chạy Hyperparameter Tuning (HPO) để nhờ AWS tự tìm bộ tham số tốt nhất cho mô hình thay vì nhóm phải tự mò bằng tay.

### Các công việc triển khai:
| Thứ | Công việc | Hoàn thành |
| --- | --- | --- |
| 2 (29/06) | Khai báo khoảng tìm kiếm (Search Space): Learning rate từ 1e-5 đến 1e-2, Batch size là 16 hoặc 32. | 29/06/2026 |
| 3 (30/06) | Cấu hình `HyperparameterTuner` trong SageMaker để tối ưu hóa metric Recall. | 30/06/2026 |
| 4 (01/07) | Chạy HPO Job. Set limit chạy 3 jobs song song để tiết kiệm thời gian. | 01/07/2026 |
| 5 (02/07) | Phân tích kết quả các jobs. Team chọn ra mô hình có điểm Recall cao nhất để dùng cho dự án. | 02/07/2026 |
| 6 (03/07) | Viết và submit bài Blog công nghệ số 2 lên hệ thống FCAJ. | 03/07/2026 |

### Kết quả đạt được:
* Tìm được bộ tham số ưng ý nhất mà không tốn công try-and-error. Bài Blog 2 hoàn thành đúng hạn.
