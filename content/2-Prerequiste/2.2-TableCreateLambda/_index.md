---
title: "Create Lambda Function"
date: "`r Sys.Date()`"
weight: 2
chapter: false
pre: " <b> 2.2 </b> "
---

## Steps: Create Logic Handling Function

### Step 1 – Start Creating a Lambda Function
- Go to the **AWS Management Console**.
- In the search bar, type **Lambda**, then select the **Lambda** service.
- On the Lambda management page, click the **Create function** button.
![Connect](/images/3.connect/13.png)

---

### Step 2 – Configure Basic Information
- Make sure the **Author from scratch** option is selected.
- Fill in the following details:
  - **Function name:**
    `getNote`
  - **Runtime:**
    `Node.js 18.x`
  - **Permissions:**
    Keep the default option **Create a new role with basic Lambda permissions**. This will automatically create a basic IAM role that allows your function to write logs to Amazon CloudWatch.

- Finally, click **Create function**.
![Configure Lambda Details]![Connect](/images/3.connect/15.png)

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