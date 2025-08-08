---
title: "Postman Installation"
date: "`r Sys.Date()`"
weight: 5
chapter: false
pre: " <b> 2.4</b> "
---

### Postman Installation

In this step, we will download and install Postman - a tool used to test the APIs you have deployed in the workshop.

1. Visit the [Postman homepage](https://www.postman.com/downloads/)
2. Select the version suitable for your operating system:
   - Windows
   - macOS
   - Linux
   
   ![Connect](/images/3.connect/9.png)

3. After downloading, proceed with installation:
   - **On Windows**: Run the `.exe` file and follow the instructions
   - **On macOS**: Drag the Postman icon to the Applications folder

4. Open Postman after successful installation

5. You can:
   - Login with your Postman account
   - Or select **Skip and go to the app** to use it immediately

6. Postman's main interface:

   ![Connect](/images/3.connect/10.png)

---

### API Testing with Postman

After installation, you can start testing the endpoints:

| Method | Endpoint       | Function          |
|--------|---------------|--------------------|
| POST   | `/notes`      | Create new note    |
| GET    | `/notes/{id}` | Get note by ID     |
| PUT    | `/notes/{id}` | Update note        |
| DELETE | `/notes/{id}` | Delete note        |

**Important notes:**
- Add header `Content-Type: application/json`
- For APIs requiring authentication, add `x-api-key` header with API Key from API Gateway

> 💡 Tip: You can save requests as Collections for later reuse

---

Now you're ready to test your personal note system using Postman!