---
title: "Dọn dẹp tài nguyên AWS"
date: "`r Sys.Date()`"
weight: 5
chapter: false
pre: "<b>4.</b>"
---

## Các bước thọn dẹp tài nguyên

### Bước 1 - Xóa API Gateway
1. Truy cập **AWS Management Console**
2. Tìm dịch vụ **API Gateway**
3. Chọn API **note-api**
4. Nhấn **Actions** → **Delete**
5. Xác nhận xóa

---

### Bước 2 - Xóa Lambda Functions
1. Truy cập dịch vụ **Lambda**
2. Chọn từng function:
   - createNote
   - getNote
   - updateNote
   - deleteNote
3. Nhấn **Actions** → **Delete**
4. Xác nhận xóa từng function

---

### Bước 3 - Xóa bảng DynamoDB
1. Truy cập dịch vụ **DynamoDB**
2. Chọn bảng **NotesTable**
3. Nhấn **Delete table**
4. Nhập `NotesTable` để xác nhận
5. Nhấn **Delete**

---

### Bước 4 - Xóa CloudWatch Logs
1. Truy cập dịch vụ **CloudWatch**
2. Chọn **Log groups**
3. ![Connect](/images/3.connect/29.png)
4. Tìm và xóa các log group liên quan:
   - `/aws/lambda/createNote`
   - `/aws/lambda/getNote`
   - `/aws/lambda/updateNote`
   - `/aws/lambda/deleteNote`
5. Nhấn **Actions** → **Delete log group(s)**

---

### Bước 5 - Xóa IAM Roles (nếu có)
1. Truy cập dịch vụ **IAM**
2. Chọn **Roles**
3. Tìm và xóa các role:
   - `LambdaExecutionRole`
   - `APIGatewayToLambdaRole`
4. Nhấn **Delete role**

> ⚠️ **Lưu ý quan trọng:**  
> - Đảm bảo đã sao lưu dữ liệu quan trọng trước khi xóa
> - Các tài nguyên đã xóa không thể khôi phục
> - Kiểm tra kỹ trước khi xác nhận xóa