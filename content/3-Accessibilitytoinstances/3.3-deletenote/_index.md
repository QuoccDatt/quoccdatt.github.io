---
title: "Note Deletion Testing (DELETE)"
date: "`r Sys.Date()`"
weight: 3
chapter: false
pre: " <b> 3.3</b> "
---
### </b> 3.3 – Note Deletion Testing (DELETE)

---

**Step 1 – Create DELETE request in Postman**  
Select method as `DELETE`.

---

**Step 2 – Configure request**  
URL:  
`https://tg9k4ugn87.execute-api.ap-southeast-1.amazonaws.com/dev/notes/1`

---

**Step 3 – Send request and check response**

```json
{
  "message": "Note deleted successfully!"
}
```
![Connect](/images/3.connect/27.png)
## Step 4 - Verify in DynamoDB

- Go to NotesTable.

- Find noteId = "1".

- If no data remains, the note has been successfully deleted.
![Connect](/images/3.connect/28.png)