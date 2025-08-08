---
title: "Tạo Lambda Function"
date: "`r Sys.Date()`"
weight: 2
chapter: false
pre: " <b> 2.2 </b> "
---

## Hướng Dẫn Tạo Các Hàm Lambda Xử Lý Ghi Chú

### Bước 1 – Khởi Tạo Lambda Function
1. Đăng nhập **AWS Management Console**
2. Tìm kiếm và chọn dịch vụ **Lambda**
3. Nhấn **Tạo hàm (Create function)**
![Giao diện Lambda Console](/images/3.connect/13.png)

---

### Bước 2 – Thiết Lập Thông Số Cơ Bản
- Chọn phương thức **Author from scratch**
- Điền thông tin:
  - **Tên hàm:** `getNote`
  - **Runtime:** `Node.js 18.x`
  - **Quyền hạn:** Giữ nguyên cấu hình mặc định (tự động tạo IAM role cơ bản)
![Cấu hình Lambda](/images/3.connect/15.png)

---

### Bước 3 – Triển Khai Mã Xử Lý
1. Trong tab **Code source**, thay thế mã mặc định bằng đoạn mã sau:

#### Mã nguồn mẫu (Node.js )
- createNote :
``` javascript
const { DynamoDBClient } = require("@aws-sdk/client-dynamodb");
const { DynamoDBDocumentClient, PutCommand } = require("@aws-sdk/lib-dynamodb");

const client = new DynamoDBClient({});
const dynamo = DynamoDBDocumentClient.from(client);

exports.handler = async (event) => {
  console.log("Received event:", JSON.stringify(event));

  try {
    const body = JSON.parse(event.body);
    const { noteId, title, content } = body;

    if (!noteId || !title || !content) {
      return {
        statusCode: 400,
        body: JSON.stringify({ error: "Missing noteId, title or content" })
      };
    }

    const params = {
      TableName: "NotesTable",
      Item: { noteId, title, content }
    };

    await dynamo.send(new PutCommand(params));

    return {
      statusCode: 200,
      body: JSON.stringify({ message: "Note created successfully", noteId }),
    };

  } catch (err) {
    console.error("Error:", err);
    return {
      statusCode: 500,
      body: JSON.stringify({ error: 'Failed to create note', details: err.message }),
    };
  }
};
```
- getNote :

```javascript
const { DynamoDBClient } = require("@aws-sdk/client-dynamodb");
const { DynamoDBDocumentClient, GetCommand } = require("@aws-sdk/lib-dynamodb");

const client = new DynamoDBClient({});
const dynamo = DynamoDBDocumentClient.from(client);

exports.handler = async (event) => {
  console.log("Received event:", JSON.stringify(event));

  try {
    const noteId = event.pathParameters?.id;

    if (!noteId) {
      return { statusCode: 400, body: JSON.stringify({ error: "Missing noteId in pathParameters" }) };
    }

    const params = {
      TableName: "NotesTable",
      Key: { noteId }
    };

    const result = await dynamo.send(new GetCommand(params));

    if (!result.Item) {
      return { statusCode: 404, body: JSON.stringify({ message: "Note not found" }) };
    }

    return { statusCode: 200, body: JSON.stringify(result.Item) };

  } catch (err) {
    console.error("Error getting note:", err);
    return { statusCode: 500, body: JSON.stringify({ error: err.message }) };
  }
};

```
- updateNote :

```javascript
const { DynamoDBClient } = require("@aws-sdk/client-dynamodb");
const { DynamoDBDocumentClient, UpdateCommand } = require("@aws-sdk/lib-dynamodb");

const client = new DynamoDBClient({});
const dynamo = DynamoDBDocumentClient.from(client);

exports.handler = async (event) => {
  console.log("Received event:", JSON.stringify(event));

  try {
    const noteId = event.pathParameters?.id;

    if (!noteId) {
      return { statusCode: 400, body: JSON.stringify({ error: "Missing noteId in pathParameters" }) };
    }

    const { title, content } = JSON.parse(event.body);

    if (!title || !content) {
      return { statusCode: 400, body: JSON.stringify({ error: "Missing title or content" }) };
    }

    const params = {
      TableName: "NotesTable",
      Key: { noteId },
      UpdateExpression: "SET title = :title, content = :content",
      ExpressionAttributeValues: {
        ":title": title,
        ":content": content
      },
      ReturnValues: "ALL_NEW"
    };

    const result = await dynamo.send(new UpdateCommand(params));

    return { statusCode: 200, body: JSON.stringify(result.Attributes) };

  } catch (err) {
    console.error("Error updating note:", err);
    return { statusCode: 500, body: JSON.stringify({ error: err.message }) };
  }
};
```
- deleteNote :

```javascript
const { DynamoDBClient } = require("@aws-sdk/client-dynamodb");
const { DynamoDBDocumentClient, DeleteCommand } = require("@aws-sdk/lib-dynamodb");

const client = new DynamoDBClient({});
const dynamo = DynamoDBDocumentClient.from(client);

exports.handler = async (event) => {
  console.log("Received event:", JSON.stringify(event));

  try {
    const noteId = event.pathParameters?.id;

    if (!noteId) {
      return { statusCode: 400, body: JSON.stringify({ error: "Missing noteId in pathParameters" }) };
    }

    const params = {
      TableName: "NotesTable",
      Key: { noteId }
    };

    await dynamo.send(new DeleteCommand(params));

    return { statusCode: 200, body: JSON.stringify({ message: "Note deleted" }) };

  } catch (err) {
    console.error("Error deleting note:", err);
    return { statusCode: 500, body: JSON.stringify({ error: err.message }) };
  }
};
```