---
title: "Event 1"
date: 2026-06-06
weight: 1
chapter: false
pre: " <b> 4.1. </b> "
---

# BÀI THU HOẠCH "MULTIPLAYER GAME NETWORKING WORKSHOP"

## Mục Đích Của Sự Kiện
* **Chia sẻ các giao thức kiến trúc mạng** trong phát triển game nhiều người chơi (Multiplayer Game).
* **Giới thiệu quy trình** xây dựng hệ thống WebSocket Serverless trên nền tảng AWS.
* **Hướng dẫn lập trình mạng** phía Client sử dụng Game Engine Godot.
* **Giới thiệu giải pháp** đóng gói ứng dụng bằng công nghệ Containerization (Docker).

---

## Nội Dung Nổi Bật

### 1. Phân tích các giao thức mạng trong game Multiplayer
* **HTTP Polling:** 
  * Cơ chế: Client gửi request liên tục để check update từ Server.
  * Nhược điểm: Thời gian phản hồi lâu (High Latency), gây overhead hệ thống.
  * Ứng dụng: Chỉ dùng cho các tính năng đơn giản như Login hoặc Leaderboard.
* **UDP (User Datagram Protocol):**
  * Cơ chế: Giao thức truyền gói tin nhanh, chấp nhận mất gói dữ liệu (Packet loss) để đổi lấy độ trễ cực thấp.
  * Ứng dụng: Tối ưu cho game tốc độ cao (FPS, MOBA, Đua xe).
  * Trong Godot: Được nâng cấp thành thư viện ENet.
* **WebSocket:**
  * Cơ chế: Giao thức kết nối hai chiều liên tục, đảm bảo tính Real-time tốt hơn HTTP Polling và kiểm soát dữ liệu tin cậy hơn.
  * Ứng dụng: Giải pháp tối ưu được chọn để Demo cho game Kéo-Búa-Bao.

### 2. Thiết lập WebSocket Serverless trên AWS
Hệ thống xử lý logic mạng được xây dựng qua 4 dịch vụ cốt lõi:
* **API Gateway:** Điều hướng kết nối qua việc config các tuyến (Routes): `$connect`, `$disconnect` và `$default` (sử dụng định dạng JSON dựa trên `request.body.action`).
* **Lambda Function:** Xử lý logic nghiệp vụ cho từng sự kiện kết nối/ngắt kết nối và truyền nhận message.
* **DynamoDB Table:** Lưu trữ dữ liệu trận đấu và trạng thái người chơi với 5 cột chính: `Connection ID`, `Status` (waiting/playing), `Opponent ID`, `Choice` (kéo/búa/bao) và `Create At` (timestamp).
* **CloudWatch:** Tự động ghi lại log hệ thống giúp theo dõi luồng dữ liệu và phục vụ debug.

### 3. Lập trình Client trên Godot Engine
Đảm nhận 4 nhiệm vụ chính để duy trì kết nối game:
* **Khởi tạo:** Thiết lập kết nối đến URL của API Gateway thông qua đối tượng `WebSocketPeer`.
* **Kiểm tra tin nhắn (Message Polling):** Liên tục kiểm tra dữ liệu trả về từ server giống như check hộp thư nhằm tránh làm quá tải hệ thống.
* **Quản lý kết nối (State Management):** Theo dõi 4 trạng thái của WebSocket gồm `Connecting`, `Open`, `Closing` và `Closed` để đưa ra yêu cầu tìm trận (Matchmaking) phù hợp.
* **Xử lý dữ liệu:** Nhận diện gói tin JSON từ Server gửi về để xử lý kết quả trò chơi.

### 4. Ứng dụng công nghệ Containerization (Docker)
* **Giải quyết xung đột môi trường:** Khắc phục triệt để tình trạng lỗi bất đồng bộ cấu hình ("code chạy được trên máy tôi nhưng lỗi trên máy bạn").
* **So sánh Virtual Machine vs Container:** Máy ảo (VM) chạy rất nặng và tốn tài nguyên vì phải boot hệ điều hành (OS) riêng; Container nhẹ hơn hẳn nhờ dùng chung OS thông qua Container Engine.
* **Cơ chế Docker Cache/Layer:** Build ảnh theo cơ chế xếp tầng giúp lưu lại lịch sử các bước trước đó, chỉ build lại từ layer có sự thay đổi $
ightarrow$ Tối ưu hóa thời gian đóng gói.

---

## Những Gì Học Được

### Tư Duy Thiết Kế
* **Kịch bản lỗi thực tế:** Hiểu cách xử lý ngoại lệ ngắt kết nối đột ngột (lỗi rớt mạng bất khả kháng) để tránh tình trạng "Ghost Connection" trong DynamoDB, khiến người chơi mới bị ghép cặp lỗi.
* **Tối ưu hóa hiệu năng:** Nhận ra việc sử dụng lệnh `Scan Table` trên DynamoDB để tìm trận sẽ gây thắt nút cổ chai (Bottleneck) khi lượng user tăng cao, từ đó cần hướng tới giải pháp quản lý tập trung chuyên biệt.
* **Quản lý tài nguyên hệ thống:** Hiểu đặc tính Stateless của Lambda để thiết kế cấu trúc dữ liệu lưu trữ hợp lý khi cần làm các tính năng khôi phục kết nối (Reconnect).

### Kiến Trúc Kỹ Thuật
* **Lập trình mạng chuyên sâu:** Nắm vững cấu trúc truyền nhận gói tin JSON và cách viết mã nguồn đồng bộ hóa dữ liệu giữa Game Client và Cloud Server.
* **Ứng dụng thực tế của Docker:** Biết cách viết một `Dockerfile` hoàn chỉnh (các lệnh `FROM`, `RUN`, `COPY`, `EXPOSE`...) và hiểu bản chất lệnh `docker run -it` để tạo môi trường sandbox cô lập hoàn toàn, hỗ trợ test bảo mật và cô lập mã độc bảo vệ máy chủ.

### Định Hướng Tương Lai
* **AWS GameLift adoption:** Tiếp cận tư duy host server game trên các cụm EC2 chuyên dụng và tích hợp các thuật toán ghép trận tự động nâng cao (Matchmaking) cho các dự án quy mô lớn.

---

## Ứng Dụng Vào Công Việc

1. **Áp dụng cơ chế WebSocket:** Cải tiến các phần giao tiếp mạng real-time cho các dự án cá nhân hoặc đồ án môn học thay vì dùng HTTP truyền thống.
2. **Xây dựng cụm Serverless trên AWS:** Thử nghiệm triển khai kết hợp API Gateway và Lambda cho các ứng dụng có luồng dữ liệu bất đồng bộ.
3. **Chuẩn hóa quy trình đóng gói ứng dụng:** Sử dụng Docker để đóng gói sản phẩm, tạo môi trường chạy đồng nhất cho tất cả các thành viên trong nhóm dự án, tối ưu hóa workflow phát triển.
4. **Ứng dụng Sandbox Container:** Ứng dụng cơ chế cô lập ứng dụng của Docker để hỗ trợ quá trình kiểm thử phần mềm (Testing) và kiểm tra an ninh (Security Check) an toàn hơn.

---

## Bài Học Rút Ra & Cảm Nhận

Tham gia buổi thuyết trình là một trải nghiệm vô cùng quý giá, mang lại cho tôi những kiến thức chuyên môn sâu sắc về mạng máy tính ứng dụng trong ngành Game và tư duy DevOps hiện đại.

### 1. Học hỏi từ những nội dung chia sẻ thực tế
* Diễn giả đã chia sẻ những bài học xương máu về lỗi hệ thống, tư duy thiết kế và cách quản lý hạ tầng mạng sao cho tối ưu về cả hiệu năng lẫn chi phí khi vận hành thực tế.
* Qua các phần phân tích chuyên sâu về UDP, WebSocket và cơ chế lưu trữ của DynamoDB, tôi hiểu rõ hơn cách xử lý bất đồng bộ dữ liệu trong một hệ thống phân tán.

### 2. Trải nghiệm kỹ thuật thực tế
* Theo dõi trực tiếp phiên demo kết nối thực tế giữa Game Client (Godot) và Server (AWS), quan sát trực quan luồng đi của dữ liệu từ lúc Client gửi request cho đến khi DynamoDB cập nhật trạng thái.
* Nắm bắt được cách debug, theo dõi hệ thống thông qua CloudWatch và các lệnh tương tác sâu bên trong Docker container thông qua cửa sổ terminal.

### 3. Ứng dụng tư duy công nghệ hiện đại
* Hiểu rõ tầm quan trọng của việc ảo hóa và đóng gói ứng dụng bằng Docker để giải phóng lập trình viên khỏi gánh nặng bất đồng bộ môi trường.
* Biết cách ứng dụng Docker Container như một môi trường "Sandbox" an toàn, linh hoạt để phục vụ cho các mục đích kiểm thử và bảo mật hệ thống.

### 4. Kết luận & Bài học cốt lõi
* **Mọi thiết kế hệ thống luôn phải đánh đổi (Trade-offs)** giữa hiệu năng, độ tin cậy và chi phí. Không có giao thức hay công nghệ nào là hoàn hảo nhất, chỉ có công nghệ phù hợp nhất với bài toán của doanh nghiệp.
* **Ý thức tối ưu chi phí Cloud:** Khi làm việc với các hệ thống Cloud, luôn phải có ý thức kiểm tra và tắt các máy chủ/dịch vụ (như cụm EC2, Database) khi không còn sử dụng để tránh phát sinh chi phí ngoài ý muốn trong quá trình phát triển (Bài học hóa đơn Cloud).

> **Tổng kết:** Sự kiện không chỉ cung cấp kiến thức kỹ thuật mạng chuyên sâu mà còn giúp tôi thay đổi cách tư duy về thiết kế kiến trúc hệ thống, tối ưu hóa hạ tầng Cloud và chuẩn hóa quy trình đóng gói phần mềm khi tham gia vào các dự án công nghệ thực tế.

![Event1](/images/4-EventParticipated/event_6-6-26/1.jpg)
![Event1](/images/4-EventParticipated/event_6-6-26/2.jpg)
![Event1](/images/4-EventParticipated/event_6-6-26/3.jpg)
![Event1](/images/4-EventParticipated/event_6-6-26/4.jpg)