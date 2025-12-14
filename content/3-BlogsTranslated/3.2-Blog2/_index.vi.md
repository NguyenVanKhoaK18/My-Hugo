---
title: "Thông báo kết thúc hỗ trợ AWS SDK for .NET v3"
date: "2025-08-19"
weight: 2
chapter: false
pre: " <b> 3.2. </b> "
---



*Bởi Ed McLaughlin | ngày 19 tháng 8 năm 2025*

Chúng tôi đang thông báo việc kết thúc hỗ trợ cho AWS SDK for .NET v3.x bắt đầu vào ngày 1 tháng 3 năm 2026, theo SDK and Tools maintenance policy. Vào ngày 28 tháng 4 năm 2025, phiên bản chính tiếp theo của AWS SDK for .NET, phiên bản 4.x, đã trở nên khả dụng rộng rãi. Phiên bản 4.x của SDK bao gồm các bản sửa lỗi, cải tiến hiệu suất, và hiện đại hóa cho .NET. Chúng tôi mạnh mẽ khuyến khích bạn nâng cấp để tận dụng những cải tiến này.

## Tác động đến ứng dụng hiện tại

Các ứng dụng hiện có mà sử dụng AWS SDK cho .NET v3.x sẽ tiếp tục hoạt động như dự định trừ khi có một thay đổi cơ bản về cách một dịch vụ AWS hoạt động. Điều này không phổ biến, và chúng tôi sẽ thông báo rộng rãi nếu nó xảy ra. 

Bắt đầu từ ngày 1 tháng 3 năm 2026, AWS SDK cho .NET v3.x sẽ chỉ nhận các bản sửa lỗi nghiêm trọng và các bản cập nhật bảo mật, và chúng tôi sẽ không cập nhật nó để hỗ trợ các dịch vụ AWS mới, các tính năng dịch vụ mới, hoặc các thay đổi đối với các dịch vụ hiện có. Sau ngày 1 tháng 6 năm 2026, khi AWS SDK cho .NET v3.x đạt đến trạng thái kết thúc hỗ trợ, nó sẽ không còn nhận được các bản cập nhật hay các bản phát hành nữa.

## Lộ trình kết thúc hỗ trợ cho phiên bản 3

Lộ trình kết thúc hỗ trợ như sau, được định nghĩa bởi vòng đời phiên bản chính của SDK:

| Giai đoạn | Ngày bắt đầu | Ngày kết thúc | Mức độ hỗ trợ |
|-----------|--------------|---------------|---------------|
| Phát hành rộng rãi | 28 tháng 7, 2015 | 1 tháng 6, 2026 | Trong giai đoạn này, SDK được hỗ trợ đầy đủ. AWS sẽ cung cấp các bản phát hành SDK thường xuyên, bao gồm hỗ trợ cho các dịch vụ mới, các bản cập nhật API cho các dịch vụ hiện có, cũng như các bản vá lỗi và bảo mật. |
| Chế độ bảo trì | 1 tháng 3, 2026 | 1 tháng 6, 2026 | Trong chế độ bảo trì, AWS giới hạn các bản phát hành SDK chỉ để giải quyết các lỗi nghiêm trọng và các vấn đề bảo mật. SDK sẽ không nhận được các bản cập nhật API cho các dịch vụ mới hoặc hiện có, hoặc được cập nhật để hỗ trợ các region mới. |
| Kết thúc hỗ trợ | 1 tháng 6, 2026 | N/A | Khi một SDK đạt đến trạng thái kết thúc hỗ trợ, nó sẽ không còn nhận được các bản cập nhật hay bản phát hành nữa. Các bản phát hành đã được công bố trước đây sẽ tiếp tục có sẵn thông qua các trình quản lý gói công khai và mã nguồn sẽ vẫn còn trên GitHub. Kho lưu trữ GitHub có thể sẽ được lưu trữ. |

## Tài liệu tham khảo cho AWS SDK for .NET phiên bản 4

Sử dụng các tài liệu tham khảo sau để tìm hiểu thêm về AWS SDK for .NET v4.x cùng với hỗ trợ di chuyển:

- **Migrating to version 4 of the AWS SDK for .NET** - Hướng dẫn di chuyển các ứng dụng AWS SDK for .NET v3.x của bạn lên AWS SDK for .NET v4.x.
- **Development Tracker** - Một công cụ theo dõi quá trình phát triển v4.x, chứa các chi tiết bổ sung về một số thay đổi trong SDK. Điều này có thể hữu ích để hiểu thêm về những thay đổi đã được triển khai.
- **.NET v4.x Code Examples** - Các ví dụ mã nguồn để giúp bạn sử dụng v4.x.

## Kết luận

Chúng tôi khuyên bạn nên nâng cấp lên phiên bản chính mới nhất của AWS SDK for .NET v4.x bằng cách sử dụng migration guide. Phiên bản chính này bao gồm, nhưng không giới hạn ở, các cải tiến hiệu suất, bản sửa lỗi, các thư viện và framework .NET hiện đại, và các bản cập nhật dịch vụ AWS mới nhất. 

Để tìm hiểu thêm, vui lòng tham khảo bài đăng blog về việc phát hành rộng rãi của AWS SDK for .NET.

Nếu bạn cần hỗ trợ hoặc có phản hồi, hãy liên hệ với các đầu mối hỗ trợ AWS thông thường của bạn. Bạn cũng có thể mở một cuộc thảo luận hoặc một vấn đề trên GitHub. Cảm ơn bạn đã sử dụng AWS SDK for .NET.

---

## Về tác giả

| <img src="/images/3-BlogsTranslated/3.2-Blog2/ed-mclaughlin.jpg" alt="Ed McLaughlin" width="400"> | **Ed McLaughlin** là giám đốc phát triển phần mềm cho AWS SDK for .NET, các sản phẩm .NET Developer Experience, và AWS Tools for PowerShell. Anh ấy thích làm việc trên các dự án, công cụ và tính năng giúp nâng cao trải nghiệm của khách hàng. Bạn có thể tìm thấy anh ấy trên LinkedIn tại [@ejm3](https://linkedin.com/in/ejm3). |
|---|---|