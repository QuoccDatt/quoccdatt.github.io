---
title : "Create API Gateway NotesAPI"
date : "`r Sys.Date()`"
weight : 3
chapter : false
pre : " <b> 2.3 </b> "
---

### 📌 Overview

In this section, we will create an API Gateway named **NotesAPI** with RESTful endpoints to manage notes, connecting to the previously created Lambda Function `NotesFunction`.

---

### 🔧 Steps to Perform

#### Step 1: Create a New API Gateway

1. Go to AWS Management Console  
2. Search for and select the **API Gateway** service  
3. Click the **Create API** button  
4. Choose the API type as **REST API** (under "Build") → Click **Build**  
   ![Connect](/images/3.connect/16.png)
5. Configure basic information:
   - API name: `NotesAPI`
   - Description: `API for managing notes`
   - Endpoint Type: Keep default `Regional`
6. Click **Create API**

![Connect](/images/3.connect/17.png)

---

#### Step 2: Create Resources and Methods

1. On the newly created API management page, in the left panel:

   - Create the main resource:
     - Select **Actions** → **Create Resource**
     - Resource Name: `/`
     - Resource Path: `notes`
     - Click **Create Resource**

   - Create a child resource for individual notes:
     - Select resource `/notes`
     - Select **Actions** → **Create Resource**
     - Resource Name: `/notes`
     - Resource Path: `{id}`
     - Click **Create Resource**

2. Create methods for each resource:

   - For resource `/notes`:
     - Select the resource → **Create Method**
     - Choose `POST` → click the checkmark (✓)
     - Configuration:
       - Integration type: `Lambda Function`
       - Lambda Region: Select your region
       - Lambda Function: `createNote`
     - Click **Save** → Confirm when asked about permission

   - For resource `/notes/{id}`:
     - Repeat the method creation process for:
       - `GET` corresponding to lambda function getNote
       - `PUT` corresponding to lambda function updateNote
       - `DELETE` corresponding to lambda function deleteNote
     Result after creating resource methods:
     ![Connect](/images/3.connect/20.png)

#### Step 3: Deploy the API

1.  **Deploy API**  
2. Deployment Configuration:
   - Deployment stage: `[New Stage]`
   - Stage name: `dev`
   - Stage description: `Production environment`
   - Deployment description: `Initial deployment`
3. Click **Deploy**

![Connect](/images/3.connect/18.png)

---

#### Step 4: Test API Endpoints

After deployment, you will see the **Invoke URL** (e.g., `https://abc123.execute-api.region.amazonaws.com/prod`)

The complete endpoints will be:

- `POST`: `https://[your-invoke-url]/prod/notes`
- `GET`: `https://[your-invoke-url]/prod/notes/{id}`
- `PUT`: `https://[your-invoke-url]/prod/notes/{id}`
- `DELETE`: `https://[your-invoke-url]/prod/notes/{id}`
