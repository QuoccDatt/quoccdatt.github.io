---
title: "Tạo bảng DynamoDB"
slug: "2.1-Create-DynamoDB"
date: "`r Sys.Date()`"
weight: 1
chapter: false
pre: " <b> 2.1 </b> "
---

## Các bước thực hiện

### Bước 1 - Mở bảng điều khiển DynamoDB
- Truy cập **AWS Management Console**
- Trên thanh tìm kiếm, nhập **DynamoDB** và chọn
![Connect](/images/3.connect/2.png)

---

### Bước 2 - Tạo bảng mới
- Nhấn **Tạo bảng**
![Connect](/images/3.connect/6.png)

---

### Bước 3 - Cấu hình bảng
Nhập thông tin sau:
- **Tên bảng:** `NotesTable`
![Connect](/images/3.connect/7.png)
- **Khóa phân vùng:** `noteId` (kiểu: `String`)

> ✅ **Mẹo:** Mỗi ghi chú sẽ được định danh duy nhất bằng `noteId`. Khóa chính này giúp DynamoDB tìm kiếm dữ liệu ghi chú nhanh chóng.

---

### Bước 4 - Tùy chọn bổ sung
- Giữ nguyên cài đặt mặc định:
  - Không dùng khóa sắp xếp
  - Không bật TTL
  - Kích hoạt chế độ **theo yêu cầu** (không cần cấu hình RCU/WCU)

---

### Bước 5 - Tạo bảng
- Nhấn **Tạo bảng** để hoàn tất
- Chờ vài giây để bảng được khởi tạo
![Connect](/images/3.connect/8.png)

> ℹ️ Sau khi tạo xong, bạn sẽ thấy bảng `NotesTable` xuất hiện trong danh sách bảng DynamoDB.