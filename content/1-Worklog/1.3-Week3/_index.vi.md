---
title: "Worklog Tuần 3"
date: "2025-09-09"
weight: 3
chapter: false
pre: " <b> 1.3. </b> "
---

### Mục tiêu tuần 3:

* Hiểu về Amazon VPC và các thành phần mạng cơ bản
* Nắm vững các cơ chế bảo mật trong VPC
* Thực hành tạo và cấu hình VPC

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Học lý thuyết VPC: <br>&emsp; + VPC là gì? <br>&emsp; + Subnet (Public/Private) <br>&emsp; + Route Table <br>&emsp; + Internet Gateway (IGW) <br>&emsp; + NAT Gateway                                     | 22/09/2025   | 22/09/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 3   | - Tiếp tục VPC: <br>&emsp; + VPC Endpoint (Interface & Gateway) <br>&emsp; + Elastic Network Interface (ENI) <br>&emsp; + CIDR và cách tính subnet                                                          | 23/09/2025   | 23/09/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 4   | - **Thực hành VPC cơ bản:** <br>&emsp; + Tạo VPC với CIDR block <br>&emsp; + Tạo Public và Private Subnet <br>&emsp; + Config Route Table <br>&emsp; + Attach Internet Gateway <br>&emsp; + Tạo NAT Gateway | 24/09/2025   | 24/09/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 5   | - Học bảo mật VPC: <br>&emsp; + Security Group (Stateful firewall) <br>&emsp; + NACL (Stateless firewall) <br>&emsp; + So sánh SG vs NACL <br>&emsp; + VPC Flow Logs                                        | 25/09/2025   | 25/09/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 6   | - **Thực hành bảo mật:** <br>&emsp; + Config Security Group cho EC2 <br>&emsp; + Setup NACL rules <br>&emsp; + Enable VPC Flow Logs <br>&emsp; + Test kết nối giữa các subnet                               | 26/09/2025   | 26/09/2025      | <https://cloudjourney.awsstudygroup.com/> |

### Kết quả đạt được tuần 3:

* Hiểu kiến trúc VPC và vai trò của từng thành phần
* Phân biệt được Public và Private Subnet
* Nắm vững cách hoạt động của Route Table, IGW, NAT Gateway
* Hiểu khái niệm VPC Endpoint và cách sử dụng
* Biết cách tính toán và phân chia CIDR block
* Tạo được VPC hoàn chỉnh với Public/Private subnet
* Phân biệt rõ Security Group và NACL
* Config được firewall rules phù hợp
* Sử dụng VPC Flow Logs để troubleshoot
* Hiểu cách bảo mật mạng trong AWS