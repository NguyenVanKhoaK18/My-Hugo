---
title: "Worklog Tuần 5"
date: "2025-09-09"
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---

### Mục tiêu tuần 5:

* Hiểu toàn diện về EC2 và các compute services
* Nắm vững các dịch vụ Storage trên AWS
* Thực hành Auto Scaling và tối ưu chi phí

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                                            | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Học EC2 & Storage cơ bản: <br>&emsp; + Instance Types (Intel, AMD, Graviton) <br>&emsp; + AMI và Golden Image <br>&emsp; + Hypervisor (Nitro) <br>&emsp; + User Data vs Metadata <br>&emsp; + EBS & Instance Store | 06/10/2025   | 06/10/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 3   | - Học File System & Lightsail: <br>&emsp; + EFS (NFSv4) <br>&emsp; + FSx (SMB, Deduplication) <br>&emsp; + Lightsail use cases <br>&emsp; + So sánh Lightsail vs EC2                                                 | 07/10/2025   | 07/10/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 4   | - **Thực hành Storage:** <br>&emsp; + Tạo Custom AMI <br>&emsp; + Config EBS và snapshot <br>&emsp; + Setup EFS share <br>&emsp; + Test Lightsail instance                                                           | 08/10/2025   | 08/10/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 5   | - Học Auto Scaling & Pricing: <br>&emsp; + Auto Scaling Group <br>&emsp; + Launch Template <br>&emsp; + Scaling Policy <br>&emsp; + 4 mô hình giá EC2 <br>&emsp; + Migration với MGN                                 | 09/10/2025   | 09/10/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 6   | - **Thực hành & Tổng kết:** <br>&emsp; + Setup Auto Scaling với ALB <br>&emsp; + Test Scale Out/In <br>&emsp; + Tính toán chi phí <br>&emsp; + Review toàn bộ Module 03 <br>&emsp; + Thiết kế kiến trúc hoàn chỉnh   | 10/10/2025   | 10/10/2025      | <https://cloudjourney.awsstudygroup.com/> |

### Kết quả đạt được tuần 5:

* **EC2 & Compute:**
  * Hiểu các Instance Types và chip (Graviton tiết kiệm 40%)
  * Nắm được cách tạo và dùng AMI/Golden Image
  * Phân biệt User Data và Metadata
  * Hiểu Hypervisor và ưu điểm Nitro

* **Storage:**
  * Nắm kiến trúc EBS và cơ chế replicate
  * Phân biệt SSD vs HDD
  * Hiểu Instance Store và rủi ro
  * Biết EFS (Linux) và FSx (Windows/Linux)
  * Hiểu deduplication tiết kiệm 30-50%

* **Lightsail:**
  * Hiểu use cases và pricing
  * So sánh với EC2
  * Biết VPC Peering với EC2

* **Auto Scaling & Pricing:**
  * Nắm vững ASG và Elasticity
  * Hiểu Launch Template
  * Phân biệt 4 mô hình giá
  * Biết tối ưu chi phí

* **Migration:**
  * Hiểu AWS MGN
  * Nắm quy trình Disaster Recovery

* **Thực hành:**
  * Tạo được Custom AMI
  * Config EBS, EFS
  * Setup Auto Scaling hoàn chỉnh
  * Thiết kế kiến trúc compute tối ưu

* Hoàn thành Module 03 - Compute Services


