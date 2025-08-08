---
title: "Cài đặt Postman"
date: "`r Sys.Date()`"
weight: 5
chapter: false
pre: " <b> 2.4</b> "
---

### Cài đặt Postman

Trong bước này, chúng ta sẽ tiến hành tải và cài đặt Postman - công cụ dùng để kiểm thử các API mà bạn đã triển khai trong workshop.

1. Truy cập vào [trang chủ Postman](https://www.postman.com/downloads/)
2. Chọn phiên bản phù hợp với hệ điều hành của bạn:
   - Windows
   - macOS
   - Linux
   
   ![Connect](/images/3.connect/9.png)

3. Sau khi tải về, tiến hành cài đặt:
   - **Trên Windows**: Chạy file `.exe` và làm theo hướng dẫn
   - **Trên macOS**: Kéo biểu tượng Postman vào thư mục Applications

4. Mở Postman sau khi cài đặt thành công

5. Bạn có thể:
   - Đăng nhập bằng tài khoản Postman
   - Hoặc chọn **Skip and go to the app** để sử dụng ngay

6. Giao diện chính của Postman:

   ![Connect](/images/3.connect/10.png)

---

### Kiểm thử API với Postman

Sau khi cài đặt, bạn có thể bắt đầu kiểm thử các endpoint:

| Method | Endpoint       | Chức năng          |
|--------|---------------|--------------------|
| POST   | `/notes`      | Tạo ghi chú mới    |
| GET    | `/notes/{id}` | Lấy ghi chú theo ID|
| PUT    | `/notes/{id}` | Cập nhật ghi chú   |
| DELETE | `/notes/{id}` | Xóa ghi chú        |

**Lưu ý quan trọng:**
- Thêm header `Content-Type: application/json`
- Đối với API cần xác thực, thêm header `x-api-key` với API Key từ API Gateway

> 💡 Mẹo: Bạn có thể lưu các request thành Collection để sử dụng lại sau này

---

Bây giờ bạn đã sẵn sàng để kiểm thử hệ thống ghi chú cá nhân của mình bằng Postman!