---
title : "Kiểm thử xoá ghi chú (DELETE)"
date : "`r Sys.Date()`"
weight : 3
chapter : false
pre : " <b> 3.3</b> "
---
### </b> 3.3 – Kiểm thử xoá ghi chú (DELETE)

---

**Bước 1 – Tạo request DELETE trong Postman**  
Chọn method là `DELETE`.

---

**Bước 2 – Cấu hình request**  
URL:  
`https://tg9k4ugn87.execute-api.ap-southeast-1.amazonaws.com/dev/notes/1`

---

**Bước 3 – Gửi request và kiểm tra phản hồi**

```json
{
  "message": "Note deleted successfully!"
}
```
![Connect](/images/3.connect/27.png)
**Bước 4 - Kiểm tra lại trong DynamoDB**  
- Vào bảng NotesTable.

- Tìm noteId = "1".

- Nếu không còn dữ liệu, ghi chú đã được xóa thành công.
![Connect](/images/3.connect/28.png)