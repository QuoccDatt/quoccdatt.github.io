---
title: "Clean Up AWS Resources"
date: "`r Sys.Date()`"
weight: 5
chapter: false
pre: "<b>4.</b>"
---

## Steps to Clean Up Resources

### Step 1 – Delete API Gateway
1. Go to the **AWS Management Console**
2. Search for the **API Gateway** service
3. Select the **note-api** API
4. Click **Actions** → **Delete**
5. Confirm deletion

---

### Step 2 – Delete Lambda Functions
1. Go to the **Lambda** service
2. Select each function:
   - createNote
   - getNote
   - updateNote
   - deleteNote
3. Click **Actions** → **Delete**
4. Confirm deletion for each function

---

### Step 3 – Delete DynamoDB Table
1. Go to the **DynamoDB** service
2. Select the **NotesTable** table
3. Click **Delete table**
4. Enter `NotesTable` to confirm
5. Click **Delete**

---

### Step 4 – Delete CloudWatch Logs
1. Go to the **CloudWatch** service
2. Select **Log groups**
![Connect](/images/3.connect/29.png)
3. Find and delete the related log groups:
   - `/aws/lambda/createNote`
   - `/aws/lambda/getNote`
   - `/aws/lambda/updateNote`
   - `/aws/lambda/deleteNote`
4. Click **Actions** → **Delete log group(s)**

---

### Step 5 – Delete IAM Roles (if any)
1. Go to the **IAM** service
2. Select **Roles**
3. Find and delete the roles:
   - `LambdaExecutionRole`
   - `APIGatewayToLambdaRole`
4. Click **Delete role**

> ⚠️ **Important Notes:**  
> - Make sure to back up any important data before deletion  
> - Deleted resources cannot be recovered  
> - Double-check before confirming deletion
