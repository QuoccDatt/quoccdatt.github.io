---
title: "Create DynamoDB Table"
date: "`r Sys.Date()`"
weight: 1
chapter: false
pre: " <b> 2.1 </b> "
---

## Steps to Perform

### Step 1 – Open DynamoDB Console
- Go to the **AWS Management Console**.
- In the search bar, type **DynamoDB**, then select **DynamoDB**.
![Connect](/images/3.connect/2.png)

---

### Step 2 – Create a New Table
- Click **Create table**.
![Connect](/images/3.connect/6.png)
---

### Step 3 – Configure the Table
Enter the following information:

- **Table name:**  
  `NotesTable`
![Connect](/images/3.connect/7.png)
- **Partition key:**  
  `noteId` (type: `String`)

> ✅ **Tip:** Each note will be uniquely identified by `noteId`. This is the primary key that allows DynamoDB to quickly search for note data.

---

### Step 4 – Other Options
- Keep the default settings:
  - Do not enable sort key
  - Do not enable TTL
  - Enable **on-demand** mode (no need to configure RCU/WCU)

---

### Step 5 – Create the Table
- Click **Create table** to finish.
- Wait a few seconds for the table to be created.
![Connect](/images/3.connect/8.png)
> ℹ️ After creation, you will see the `NotesTable` listed in the DynamoDB table list.
