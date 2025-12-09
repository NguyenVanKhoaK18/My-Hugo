---
title: "Query Data"
date: "2025-09-09"
weight: 3
chapter: false
pre: " <b> 5.5.3. </b> "
---

#### Query Data

In this step, you will learn how to query and scan data from your DynamoDB table.

1. Navigate to your **TaskManagement** table
2. Go to **Explore table items** tab

![Explore Items](/images/5-Workshop/5.5-DynamoDB/explore-items.png)

#### Query by Partition Key

**Query for specific user's tasks:**
1. Select **Query** option
2. Enter partition key value: `task-001`
3. Click **Run**

![Query by Partition](/images/5-Workshop/5.5-DynamoDB/query-partition.png)

**Results:**
- Shows items with TaskId = `task-001`

![Query Results](/images/5-Workshop/5.5-DynamoDB/query-results.png)

#### Scan All Items

**View all items in table:**
1. Select **Scan** option
2. Click **Run**

![Scan Table](/images/5-Workshop/5.5-DynamoDB/scan-table.png)

**Results:**
- Shows all items in the table

![Scan Results](/images/5-Workshop/5.5-DynamoDB/scan-results.png)

#### Filter Data

**Filter by Status:**
1. Select **Scan** option
2. Add filter: `Status = "Completed"`
3. Click **Run**

![Filter Data](/images/5-Workshop/5.5-DynamoDB/filter-data.png)

**Results:**
- Shows only completed tasks

![Filter Results](/images/5-Workshop/5.5-DynamoDB/filter-results.png)

#### Summary

You have successfully:
- ✅ Queried data by partition key
- ✅ Scanned all table items
- ✅ Filtered data by attributes

DynamoDB provides flexible ways to retrieve your data efficiently!