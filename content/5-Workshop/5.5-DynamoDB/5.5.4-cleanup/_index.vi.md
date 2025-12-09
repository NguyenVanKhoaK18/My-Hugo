---
title: "Dọn dẹp"
date: "2025-09-09"
weight: 4
chapter: false
pre: " <b> 5.5.4. </b> "
---

#### Dọn dẹp tài nguyên

Chúc mừng bạn đã hoàn thành workshop Thao tác cơ bản với DynamoDB!

Trong workshop này, bạn đã học cách:
- ✅ Tạo bảng DynamoDB
- ✅ Thêm dữ liệu vào bảng
- ✅ Truy vấn dữ liệu theo partition key
- ✅ Quét và lọc dữ liệu bảng

## Các bước dọn dẹp

Để tránh các khoản phí liên tục, hãy xóa bảng DynamoDB:

### Xóa bảng DynamoDB

1. Điều hướng đến **DynamoDB** console
2. Chọn bảng **TaskManagement** của bạn
3. Nhấp **Delete**

![Delete Table](/images/5-Workshop/5.5-DynamoDB/delete-table.png)

4. Gõ **delete** để xác nhận
5. Nhấp **Delete table**

![Confirm Delete](/images/5-Workshop/5.5-DynamoDB/confirm-delete.png)

### Xác minh việc dọn dẹp

Đảm bảo bảng đã được xóa khỏi DynamoDB console:

![Cleanup Verified](/images/5-Workshop/5.5-DynamoDB/cleanup-verified.png)

## Tóm tắt chi phí

Workshop này sử dụng:
- **DynamoDB On-Demand**: Trả tiền theo yêu cầu
- **Không có phí liên tục** sau khi xóa bảng

## Các bước tiếp theo

Bây giờ bạn đã hiểu cơ bản về DynamoDB, hãy xem xét:

### Tính năng nâng cao
- Global Secondary Indexes (GSI)
- DynamoDB Streams
- Auto Scaling
- Backup và Point-in-time Recovery

### Tích hợp
- Sử dụng với AWS Lambda cho ứng dụng serverless
- Tích hợp với API Gateway cho REST APIs
- Kết nối với AWS AppSync cho GraphQL APIs

### Best Practices
- Thiết kế partition keys hiệu quả
- Sử dụng composite sort keys cho truy vấn phức tạp
- Triển khai xử lý lỗi phù hợp
- Giám sát hiệu suất với CloudWatch

## Tài liệu tham khảo

- [DynamoDB Developer Guide](https://docs.aws.amazon.com/dynamodb/)
- [DynamoDB Best Practices](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/best-practices.html)
- [NoSQL Design Patterns](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/bp-general-nosql-design.html)

Cảm ơn bạn đã hoàn thành workshop này! 🎉