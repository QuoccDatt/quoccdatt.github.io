---
title: "Introduction"
date: "`r Sys.Date()`"
weight: 1
chapter: false
pre: "<b> 1. </b>"
---

In the digital age, managing personal information anytime, anywhere has become an essential need. This workshop guides you through building a simple **Personal Note-Taking System**, deployed on a **Serverless architecture** using **Amazon Web Services (AWS)**.

### 🎯 Objectives

- Create a note-taking application with CRUD (Create, Read, Update, Delete) functionality.
- Deploy the application entirely on AWS services, without physical servers.
- Use **DynamoDB** to store note data.
- Create and handle APIs via **AWS Lambda** combined with **API Gateway**.
- Test and send API requests using **Postman**.
- Monitor logs and errors through **CloudWatch Logs**.

### ☁️ Why Choose Serverless Architecture

- No need to manage physical infrastructure or EC2.
- Automatically scalable and flexible.
- Cost-efficient – pay only when requests are made.
- Fast deployment, easy integration with the AWS ecosystem.

### 🔧 Technologies Used

| AWS Service   | Main Role                                         |
|---------------|--------------------------------------------------|
| DynamoDB      | Stores note data in NoSQL format                 |
| Lambda        | Handles business logic for adding/viewing/editing/deleting notes |
| API Gateway   | Receives HTTP requests and forwards them to Lambda |
| CloudWatch    | Monitors logs, debugging, and system tracking    |
| IAM           | Manages access permissions to AWS services       |

---

👉 After completing the workshop, you’ll understand the process of building a basic serverless application and be able to customize additional features for your own note-taking system.
