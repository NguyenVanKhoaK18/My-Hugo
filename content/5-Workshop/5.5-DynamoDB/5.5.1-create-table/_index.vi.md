---
title: "Tạo bảng DynamoDB"
date: "2025-09-09"
weight: 1
chapter: false
pre: " <b> 5.5.1. </b> "
---

#### Tạo bảng DynamoDB

Trong bước này, bạn sẽ tạo một bảng DynamoDB để lưu trữ dữ liệu quản lý công việc.

1. Điều hướng đến dịch vụ **DynamoDB** trong AWS Console
2. Nhấp **Create table**

![Create Table](/images/5-Workshop/5.5-DynamoDB/create-table.png)

#### Cấu hình cài đặt bảng

**Chi tiết bảng:**
- Tên bảng: **TaskManagement**
- Partition key: **TaskId** (String)
- Sort key: **UserId** (String)

![Table Settings](/images/5-Workshop/5.5-DynamoDB/table-settings.png)

**Cài đặt bảng:**
- Sử dụng cài đặt mặc định cho:
  - Capacity mode: **On-demand**
  - Encryption: **Owned by Amazon DynamoDB**

![Default Settings](/images/5-Workshop/5.5-DynamoDB/default-settings.png)

#### Tạo bảng

1. Xem lại cấu hình của bạn
2. Nhấp **Create table**

![Create Table Button](/images/5-Workshop/5.5-DynamoDB/create-table-button.png)

#### Xác minh việc tạo bảng

Đợi bảng được tạo (trạng thái: **Active**):

![Table Created](/images/5-Workshop/5.5-DynamoDB/table-created.png)

**Thông tin bảng:**
- Tên bảng: **TaskManagement**
- Partition key: **TaskId**
- Sort key: **UserId**
- Trạng thái: **Active**

Bảng DynamoDB của bạn hiện đã sẵn sàng để lưu trữ dữ liệu!