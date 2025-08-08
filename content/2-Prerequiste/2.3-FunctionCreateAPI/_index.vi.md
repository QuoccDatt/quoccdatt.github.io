---
title: "Tạo API Gateway NotesAPI"
date: "`r Sys.Date()`"
weight: 3
chapter: false
pre: " <b> 2.3 </b> "
---

### 🌟 Tổng quan
Phần này hướng dẫn tạo **API Gateway** tên **NotesAPI** với các endpoint RESTful để quản lý ghi chú, tích hợp với các Lambda Function đã tạo trước đó.

---

### 🛠️ Các bước triển khai

#### Bước 1: Khởi tạo API Gateway
1. Đăng nhập **AWS Management Console**
2. Tìm và chọn dịch vụ **API Gateway**
3. Nhấn **Create API**
4. Chọn:
   - Loại API: **REST API** (mục "Build") 
   - Nhấn **Build**
![Giao diện tạo API](/images/3.connect/16.png)

5. Nhập thông tin:
   - **Tên API:** `NotesAPI`
   - **Mô tả:** `API quản lý ghi chú`
   - **Endpoint Type:** Giữ nguyên `Regional`
6. Nhấn **Create API**
![Cấu hình API](/images/3.connect/17.png)

---

#### Bước 2: Tạo Resource và Method
1. **Tạo Resource chính**:
   - Chọn **Actions** → **Create Resource**
   - Thiết lập:
     - Resource Name: `notes`
     - Resource Path: `/notes`
   - Nhấn **Create Resource**

2. **Tạo Resource con**:
   - Chọn resource `/notes` vừa tạo
   - Chọn **Actions** → **Create Resource**
   - Thiết lập:
     - Resource Name: `{id}`
     - Resource Path: `/{id}`
   - Nhấn **Create Resource**

3. **Tạo Methods**:
   - **POST** (tạo ghi chú):
     - Chọn resource `/notes` → **Create Method** → chọn `POST`
     - Cấu hình:
       - Integration type: `Lambda Function`
       - Lambda Region: Chọn region của bạn
       - Lambda Function: `createNote`
     - Nhấn **Save** → Xác nhận cấp quyền

   - **GET/PUT/DELETE** (xem/cập nhật/xóa ghi chú):
     - Lặp lại quy trình cho resource `/{id}` với:
       - `GET` → `getNote`
       - `PUT` → `updateNote` 
       - `DELETE` → `deleteNote`

![Kết quả tạo Method](/images/3.connect/20.png)

---

#### Bước 3: Triển khai API
1. Chọn **Actions** → **Deploy API**
2. Cấu hình:
   - Deployment stage: `[New Stage]`
   - Stage name: `dev`
   - Mô tả: `Môi trường production`
3. Nhấn **Deploy**
![Triển khai API](/images/3.connect/18.png)

---

#### Bước 4: Kiểm tra Endpoint
Sau khi triển khai, bạn sẽ nhận được **Invoke URL** có dạng:
`https://abc123.execute-api.region.amazonaws.com/dev`

Các endpoint hoàn chỉnh:

  `POST https://[your-url]/dev/notes`
 
  `GET https://[your-url]/dev/notes/{id}`

  `PUT https://[your-url]/dev/notes/{id}`
 
  `DELETE https://[your-url]/dev/notes/{id}`
