---
title: "TỔNG QUAN" 
date: "`r Sys.Date()`" 
weight: 1 
chapter: false 
pre: "<b> 1. </b>" 
---

## Tổng quan

Trong bài lab này, bạn sẽ tìm hiểu cách triển khai một **hệ thống ghi chú cá nhân** sử dụng kiến trúc **serverless trên nền tảng AWS**. Ứng dụng cho phép người dùng tạo, chỉnh sửa, xem và xoá các ghi chú cá nhân thông qua các API được triển khai bằng AWS Lambda và quản lý dữ liệu với DynamoDB.

Người dùng có thể tương tác với hệ thống thông qua công cụ Postman hoặc các công cụ HTTP client khác. Toàn bộ hạ tầng không cần máy chủ, giúp tiết kiệm chi phí và dễ dàng mở rộng.

## Kiến trúc tổng thể

![Connect](/images/3.connect/11.png)

## Nội dung

1. [Giới thiệu hệ thống và kiến trúc](../1-Introduce/)  
2. [Các bước chuẩn bị](../2-Prerequiste/)  
3. [Kiểm thử với postman](../3-Accessibilitytoinstances/)  
4. [Dọn dẹp tài nguyên](../4-cleanup/)