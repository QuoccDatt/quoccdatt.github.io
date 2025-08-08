---
title : "Kiểm thử cập nhật ghi chú (PUT)"
date : "`r Sys.Date()`"
weight : 2
chapter : false
pre : " <b> 3.2</b> "
---

## Các bước thực hiện

### Bước 1 - Tạo request PUT trong Postman
- Chọn method là `PUT`

---

### Bước 2 - Cấu hình request
- **URL:**  
  `https://tg9k4ugn87.execute-api.ap-southeast-1.amazonaws.com/dev/notes/1`

- **Headers:**
  - `Content-Type`: `application/json`

- **Body:**
```json
{
  "noteId": "1",
  "title": "hahaaaa",
  "content": "This is my first note"
}
```
### Bước 3 – Gửi request và kiểm tra kết quả
```json
{
  "message": "Note updated successfully!"
}
```
![Connect](/images/3.connect/24.png)
### Bước 4 – Kiểm tra lại trong DynamoDB
- Vào bảng NotesTable

- Tìm noteId = "1"

- Kiểm tra xem title đã được cập nhật thành "hahaaaa"
![Connect](/images/3.connect/25.png)