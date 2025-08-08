---
title: "Giới thiệu"
date: "`r Sys.Date()`"
weight: 1
chapter: false
pre: "<b> 1. </b>"
---

Trong thời đại công nghệ số, việc quản lý thông tin cá nhân mọi lúc mọi nơi đã trở thành nhu cầu thiết yếu. Workshop này hướng dẫn bạn xây dựng một **Hệ thống Ghi Chú Cá Nhân** đơn giản, triển khai trên nền **kiến trúc không máy chủ (Serverless)** sử dụng dịch vụ của **Amazon Web Services (AWS)**.

###  Mục tiêu

- Tạo ứng dụng ghi chú với tính năng CRUD (Create, Read, Update, Delete).
- Triển khai ứng dụng hoàn toàn trên dịch vụ AWS, không cần máy chủ vật lý.
- Sử dụng **DynamoDB** làm nơi lưu trữ dữ liệu ghi chú.
- Tạo và xử lý API qua **AWS Lambda** kết hợp **API Gateway**.
- Kiểm tra và gửi yêu cầu API bằng **Postman**.
- Giám sát log và lỗi thông qua **CloudWatch Logs**.

###  Lý do chọn kiến trúc Serverless

- Không cần quản lý hạ tầng vật lý hay EC2.
- Tự động mở rộng linh hoạt.
- Tối ưu chi phí – chỉ trả tiền khi có yêu cầu.
- Triển khai nhanh chóng, dễ tích hợp với hệ sinh thái AWS.

###  Công nghệ sử dụng

| Dịch vụ AWS   | Vai trò chính                                   |
|---------------|--------------------------------------------------|
| DynamoDB      | Lưu trữ dữ liệu ghi chú dưới dạng NoSQL          |
| Lambda        | Xử lý nghiệp vụ thêm/xem/sửa/xoá ghi chú         |
| API Gateway   | Nhận request HTTP và chuyển tiếp đến Lambda      |
| CloudWatch    | Theo dõi log, debug và giám sát hệ thống         |
| IAM           | Quản lý quyền truy cập đến các dịch vụ AWS       |

---

👉 Sau khi hoàn thành workshop, bạn sẽ nắm được quy trình xây dựng một ứng dụng serverless cơ bản và có thể tùy biến thêm nhiều tính năng cho hệ thống ghi chú của riêng mình.
