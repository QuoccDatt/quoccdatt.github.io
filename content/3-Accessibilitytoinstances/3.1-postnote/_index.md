---
title: "Test note creation (POST)"
date: "`r Sys.Date()`"
weight: 1
chapter: false
pre: " <b> 3.1</b> "
---

## Implementation steps
---
### Step 1 - Open Postman and create new request
- Open **Postman** application
- Click **New → HTTP Request**
- Select method as `POST`
---
### Step 2 - Configure request
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

## Step 3 - Send request and check result
- Click Send
- Check response:
``` json
{
  "message": "Note created successfully!"
}
```
## Step 4 - Check note in DynamoDB
- Access AWS Management Console

- Find DynamoDB service

- Select NotesTable

- Go to Explore table items tab

- Find noteId = "1"

![Connect](/images/3.connect/22.png)

✅ If the note displays correctly, you have created successfully!