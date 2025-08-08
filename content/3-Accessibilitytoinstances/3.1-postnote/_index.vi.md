---
title : "Kiểm thử tạo ghi chú (POST)"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
pre : " <b> 3.1</b> "
---

##  Các bước thực hiện

### Bước 1 – Mở Postman và tạo request mới
- Mở ứng dụng **Postman**.
- Nhấn **New → HTTP Request**.
- Chọn method là `POST`.

### Bước 2 – Cấu hình request
- **URL:**  
  `https://tg9k4ugn87.execute-api.ap-southeast-1.amazonaws.com/dev/notes`
- **Headers:**
  - `Content-Type`: `application/json`

- **Body (raw → JSON):**
```json
{
  "noteId": "1",
  "title": "First Note",
  "content": "This is my first note"
}
```
![Connect](/images/3.connect/21.png)
### Bước 3 – Gửi request và kiểm tra kết quả
- Nhấn Send.
- Kiểm tra phản hồi:
 ```json
{
  "message": "Note created successfully!"
}
```
### Bước 4 - Kiểm tra ghi chú trong DynamoDB

- Truy cập AWS Management Console

- Tìm dịch vụ DynamoDB

- Chọn bảng NotesTable

- Vào tab Explore table items

- Tìm noteId = "1"
- ![Connect](/images/3.connect/22.png)

✅ Nếu ghi chú hiển thị đúng, bạn đã tạo thành công!