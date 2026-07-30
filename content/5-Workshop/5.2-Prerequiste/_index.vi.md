---
title : "Các bước chuẩn bị"
date : 2026-06-08 
weight : 2
chapter : false
pre : " <b> 5.2. </b> "
---

Để bắt đầu triển khai hệ thống **AI Pulmonary Diagnostic Suite**, chúng ta cần chuẩn bị môi trường làm việc trên AWS, bao gồm việc cấp quyền (IAM Permissions) cần thiết và khởi tạo dữ liệu mẫu thông qua AWS CloudShell. 

Trong workshop này, chúng ta sẽ sử dụng region **N. Virginia (us-east-1)**.

### 1. Cấu hình IAM Permissions
Gắn IAM permission policy sau vào tài khoản AWS User hoặc Role của bạn để có đủ quyền triển khai (deploy) và dọn dẹp (clean-up) các tài nguyên MLOps trong workshop này.

*(Lưu ý: Trong môi trường thực tế, bạn nên áp dụng nguyên tắc đặc quyền tối thiểu (Least Privilege). Policy dưới đây được nới lỏng một chút để thuận tiện cho quá trình thực hành lab).*

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "MLOpsWorkshopPermissions",
            "Effect": "Allow",
            "Action": [
                "sagemaker:*",
                "s3:*",
                "lambda:*",
                "apigateway:*",
                "cloudwatch:*",
                "logs:*",
                "iam:PassRole",
                "iam:CreateRole",
                "iam:AttachRolePolicy",
                "iam:PutRolePolicy"
            ],
            "Resource": "*"
        }
    ]
}
```

Sau khi gắn policy này, bạn có thể kiểm tra quyền của mình bằng cách truy cập vào **IAM Console** -> **Users** -> chọn user của bạn -> **Permissions**. Bạn sẽ thấy policy mới được gắn vào.

![Kiểm tra IAM Permissions](/images/5-Workshop/5.2-Prerequisite/iam-policy.png)

### 2. Thiết lập môi trường làm việc với AWS CloudShell
Thay vì phải cài đặt AWS CLI và Python trên máy cá nhân, chúng ta sẽ sử dụng **AWS CloudShell** – một môi trường terminal trên trình duyệt đã được AWS cấu hình sẵn.

**Bước 1:** Từ màn hình AWS Management Console, nhấn vào biểu tượng **CloudShell** ở góc trên cùng bên phải.

![Mở AWS CloudShell](/images/5-Workshop/5.2-Prerequisite/open-cloudshell.png)

**Bước 2:** Đợi khoảng 1-2 phút để CloudShell khởi tạo môi trường. Sau khi dấu nhắc lệnh hiện ra, ở góc trên cùng bên phải của CloudShell, bạn nhấn vào **Actions** -> **Upload file** và tải lên file nén mã nguồn của dự án (ví dụ: `AI-Pulmonary-Diagnostic-Suite.zip`).

**Bước 3:** Tiến hành giải nén mã nguồn và di chuyển vào thư mục dự án (vì đây là dự án mà mình đã làm từ trước nhưng chưa deploy lên AWS, nên cần giải nén và di chuyển vào thư mục dự án để tiếp tục triển khai).:

```bash
unzip AI-Pulmonary-Diagnostic-Suite.zip
cd AI-Pulmonary-Diagnostic-Suite-main
```
**Bước 4:** Cài đặt các thư viện Python cần thiết cho quá trình tiền xử lý và MLOps từ file requirements.txt:

```bash
pip install -r requirements.txt
```
Sau khi cài đặt xong, bạn sẽ được kết quả:

![Cài đặt thư viện Python](/images/5-Workshop/5.2-Prerequisite/install-reqs.png)

### 3. Khởi tạo kho dữ liệu (Data Lake) và Dữ liệu mẫu (Toy Data)
Để huấn luyện mô hình chẩn đoán phổi, chúng ta cần hình ảnh X-quang/CT. Dự án đã chuẩn bị sẵn một kịch bản (script) để tự động tạo Amazon S3 Bucket và tải dữ liệu mẫu lên Cloud.

Thực thi lệnh sau trong CloudShell:

```bash
python src/data/create_toy_dataset.py
```

Sau khi script chạy xong, hệ thống sẽ tự động khởi tạo Bucket và tải lên các thư mục ảnh y tế (ví dụ: NORMAL, PNEUMONIA).

Để kiểm tra chắc chắn, bạn có thể truy cập vào dịch vụ Amazon S3 trên console. Bạn sẽ thấy một Bucket mới vừa được tạo ra chứa các hình ảnh phục vụ cho bước huấn luyện mô hình tiếp theo.

![Kiểm tra Bucket S3](/images/5-Workshop/5.2-Prerequisite/create-toy-dataset.png)

Đến đây, môi trường của bạn đã hoàn toàn sẵn sàng!

*Kết quả cuối cùng của bước chuẩn bị là chuyển từ dataset 5.800 ảnh sang dataset 120 ảnh (toy dataset) để thuận tiện cho việc triển khai mô hình trong workshop. Bạn có thể kiểm tra bằng cách truy cập vào Bucket S3 vừa tạo và xem các thư mục con chứa ảnh.*
