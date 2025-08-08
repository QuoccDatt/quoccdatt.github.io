---
title: "Note Update Testing (PUT)"
date: "`r Sys.Date()`"
weight: 2
chapter: false
pre: " <b> 3.2</b> "
---

## Steps to perform

### Step 1 - Create PUT request in Postman
- Select method as `PUT`

---

### Step 2 - Configure request
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
## Step 3 – Send request and check result
```json
{
  "message": "Note updated successfully!"
}
```
![Connect](/images/3.connect/24.png)

## Step 4 – Verify in DynamoDB
- Go to NotesTable

- Find noteId = "1"

- Check if title has been updated to "hahaaaa"
![Connect](/images/3.connect/25.png)