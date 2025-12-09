---
title: "Add Data to Table"
date: "2025-09-09"
weight: 2
chapter: false
pre: " <b> 5.5.2. </b> "
---

#### Add Data to Table

In this step, you will add sample data to your DynamoDB table using the AWS Console.

1. Navigate to your **TaskManagement** table
2. Go to **Explore table items** tab
3. Click **Create item**

![Create Item](/images/5-Workshop/5.5-DynamoDB/create-item.png)

#### Add Sample Items

**Item 1:**
- TaskId: `task-001`
- UserId: `user-123`
- TaskTitle: `Complete project proposal`
- Status: `In Progress`
- DueDate: `2025-01-15`

![Item 1](/images/5-Workshop/5.5-DynamoDB/item-1.png)

**Item 2:**
- TaskId: `task-002`
- UserId: `user-123`
- TaskTitle: `Review code changes`
- Status: `Completed`
- DueDate: `2025-01-10`

![Item 2](/images/5-Workshop/5.5-DynamoDB/item-2.png)

**Item 3:**
- TaskId: `task-003`
- UserId: `user-456`
- TaskTitle: `Update documentation`
- Status: `Pending`
- DueDate: `2025-01-20`

![Item 3](/images/5-Workshop/5.5-DynamoDB/item-3.png)

#### Create Items

For each item:
1. Enter the attribute values
2. Click **Create item**

![Create Item Button](/images/5-Workshop/5.5-DynamoDB/create-item-button.png)

#### Verify Data

After adding all items, you should see them in the table:

![Items Added](/images/5-Workshop/5.5-DynamoDB/items-added.png)

Your DynamoDB table now contains sample task management data!