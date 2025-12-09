---
title: "Create DynamoDB Table"
date: "2025-09-09"
weight: 1
chapter: false
pre: " <b> 5.5.1. </b> "
---

#### Create DynamoDB Table

In this step, you will create a DynamoDB table to store task management data.

1. Navigate to **DynamoDB** service in the AWS Console
2. Click **Create table**

![Create Table](/images/5-Workshop/5.5-DynamoDB/create-table.png)

#### Configure Table Settings

**Table details:**
- Table name: **TaskManagement**
- Partition key: **TaskId** (String)
- Sort key: **UserId** (String)

![Table Settings](/images/5-Workshop/5.5-DynamoDB/table-settings.png)

**Table settings:**
- Use default settings for:
  - Capacity mode: **On-demand**
  - Encryption: **Owned by Amazon DynamoDB**

![Default Settings](/images/5-Workshop/5.5-DynamoDB/default-settings.png)

#### Create Table

1. Review your configuration
2. Click **Create table**

![Create Table Button](/images/5-Workshop/5.5-DynamoDB/create-table-button.png)

#### Verify Table Creation

Wait for the table to be created (status: **Active**):

![Table Created](/images/5-Workshop/5.5-DynamoDB/table-created.png)

**Table Information:**
- Table name: **TaskManagement**
- Partition key: **TaskId**
- Sort key: **UserId**
- Status: **Active**

Your DynamoDB table is now ready to store data!