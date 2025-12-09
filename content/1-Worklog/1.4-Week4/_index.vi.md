---
title: "Worklog Tuần 4"
date: "2025-09-09"
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---

### Mục tiêu tuần 4:

* Hiểu cách kết nối nhiều VPC và môi trường Hybrid
* Nắm vững các loại Load Balancer
* Thực hành kết nối VPC và setup Load Balancer

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                                           | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                               |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | -------------------------------------------- |
| 2   | - Học kết nối Multi-VPC: <br>&emsp; + VPC Peering <br>&emsp; + Transit Gateway (TGW) <br>&emsp; + So sánh VPC Peering vs TGW <br>&emsp; + Transitive routing                                                      | 29/09/2025   | 29/09/2025      | <https://cloudjourney.awsstudygroup.com/>    |
| 3   | - Học Hybrid Connection: <br>&emsp; + VPN Site-to-Site <br>&emsp; + Virtual Private Gateway (VGW) <br>&emsp; + Customer Gateway (CGW) <br>&emsp; + AWS Direct Connect (DX)                                          | 30/09/2025   | 30/09/2025      | <https://cloudjourney.awsstudygroup.com/>    |
| 4   | - **Thực hành kết nối VPC:** <br>&emsp; + Tạo 2 VPC khác nhau <br>&emsp; + Setup VPC Peering <br>&emsp; + Config Route Table cho Peering <br>&emsp; + Test kết nối giữa các VPC                                    | 01/10/2025   | 01/10/2025      | <https://cloudjourney.awsstudygroup.com/>    |
| 5   | - Học Elastic Load Balancer: <br>&emsp; + Application Load Balancer (ALB) - Layer 7 <br>&emsp; + Network Load Balancer (NLB) - Layer 4 <br>&emsp; + Gateway Load Balancer (GLB) - Layer 3 <br>&emsp; + Sticky Session | 02/10/2025   | 02/10/2025      | <https://cloudjourney.awsstudygroup.com/>    |
| 6   | - **Thực hành Load Balancer:** <br>&emsp; + Tạo ALB cho web application <br>&emsp; + Config Target Groups <br>&emsp; + Setup Path-based routing <br>&emsp; + Test health check <br>&emsp; + Enable Sticky Session  | 03/10/2025   | 03/10/2025      | <https://cloudjourney.awsstudygroup.com/>    |

### Kết quả đạt được tuần 4:

* Hiểu cách kết nối nhiều VPC với nhau
* Phân biệt VPC Peering và Transit Gateway
* Nắm được các phương thức kết nối Hybrid (VPN, Direct Connect)
* Biết khi nào nên dùng VPN Site-to-Site hay Direct Connect
* Setup được VPC Peering và config routing
* Hiểu vai trò và cách hoạt động của các loại Load Balancer
* Phân biệt Layer 3, 4, 7 load balancing
* Tạo và config được ALB với Target Groups
* Biết setup Path-based routing
* Hiểu khái niệm Sticky Session và khi nào cần dùng
* Hoàn thành Module 02 về Networking trên AWS