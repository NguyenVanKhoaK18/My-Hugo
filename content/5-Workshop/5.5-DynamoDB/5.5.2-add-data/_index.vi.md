---
title: "Thêm dữ liệu vào bảng"
date: "2025-09-09"
weight: 2
chapter: false
pre: " <b> 5.5.2. </b> "
---

#### Thêm dữ liệu vào bảng

Trong bước này, bạn sẽ thêm dữ liệu mẫu vào bảng DynamoDB bằng AWS Console.

1. Điều hướng đến bảng **TaskManagement** của bạn
2. Vào tab **Explore table items**
3. Nhấp **Create item**

![Create Item](/images/5-Workshop/5.5-DynamoDB/create-item.png)

#### Thêm các mục mẫu

**Mục 1:**
- TaskId: `task-001`
- UserId: `user-123`
- TaskTitle: `Complete project proposal`
- Status: `In Progress`
- DueDate: `2025-01-15`

![Item 1](/images/5-Workshop/5.5-DynamoDB/item-1.png)

**Mục 2:**
- TaskId: `task-002`
- UserId: `user-123`
- TaskTitle: `Review code changes`
- Status: `Completed`
- DueDate: `2025-01-10`

![Item 2](/images/5-Workshop/5.5-DynamoDB/item-2.png)

**Mục 3:**
- TaskId: `task-003`
- UserId: `user-456`
- TaskTitle: `Update documentation`
- Status: `Pending`
- DueDate: `2025-01-20`

![Item 3](/images/5-Workshop/5.5-DynamoDB/item-3.png)

#### Tạo các mục

Cho mỗi mục:
1. Nhập các giá trị thuộc tính
2. Nhấp **Create item**

![Create Item Button](/images/5-Workshop/5.5-DynamoDB/create-item-button.png)

#### Xác minh dữ liệu

Sau khi thêm tất cả các mục, bạn sẽ thấy chúng trong bảng:

![Items Added](/images/5-Workshop/5.5-DynamoDB/items-added.png)

Bảng DynamoDB của bạn hiện đã chứa dữ liệu quản lý công việc mẫu!