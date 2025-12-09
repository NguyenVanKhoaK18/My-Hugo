---
title: "Truy vấn dữ liệu"
date: "2025-09-09"
weight: 3
chapter: false
pre: " <b> 5.5.3. </b> "
---

#### Truy vấn dữ liệu

Trong bước này, bạn sẽ học cách truy vấn và quét dữ liệu từ bảng DynamoDB.

1. Điều hướng đến bảng **TaskManagement** của bạn
2. Vào tab **Explore table items**

![Explore Items](/images/5-Workshop/5.5-DynamoDB/explore-items.png)

#### Truy vấn theo Partition Key

**Truy vấn công việc của người dùng cụ thể:**
1. Chọn tùy chọn **Query**
2. Nhập giá trị partition key: `task-001`
3. Nhấp **Run**

![Query by Partition](/images/5-Workshop/5.5-DynamoDB/query-partition.png)

**Kết quả:**
- Hiển thị các mục với TaskId = `task-001`

![Query Results](/images/5-Workshop/5.5-DynamoDB/query-results.png)

#### Quét tất cả các mục

**Xem tất cả các mục trong bảng:**
1. Chọn tùy chọn **Scan**
2. Nhấp **Run**

![Scan Table](/images/5-Workshop/5.5-DynamoDB/scan-table.png)

**Kết quả:**
- Hiển thị tất cả các mục trong bảng

![Scan Results](/images/5-Workshop/5.5-DynamoDB/scan-results.png)

#### Lọc dữ liệu

**Lọc theo Status:**
1. Chọn tùy chọn **Scan**
2. Thêm bộ lọc: `Status = "Completed"`
3. Nhấp **Run**

![Filter Data](/images/5-Workshop/5.5-DynamoDB/filter-data.png)

**Kết quả:**
- Chỉ hiển thị các công việc đã hoàn thành

![Filter Results](/images/5-Workshop/5.5-DynamoDB/filter-results.png)

#### Tóm tắt

Bạn đã thành công:
- ✅ Truy vấn dữ liệu theo partition key
- ✅ Quét tất cả các mục trong bảng
- ✅ Lọc dữ liệu theo thuộc tính

DynamoDB cung cấp các cách linh hoạt để truy xuất dữ liệu một cách hiệu quả!