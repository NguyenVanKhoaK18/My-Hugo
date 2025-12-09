---
title: "Worklog Tuần 7"
date: "2025-09-09"
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---

### Mục tiêu tuần 7:

* Hiểu về Glacier và Cold Storage
* Tìm hiểu Snow Family cho data transfer
* Nắm vững Storage Gateway và DR strategies

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                                           | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                               |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | -------------------------------------------- |
| 2   | - Học Glacier: <br>&emsp; + Glacier vs Glacier Deep Archive <br>&emsp; + Retrieve options (1-5 phút, 3-5 giờ, 5-12 giờ) <br>&emsp; + Object Lock <br>&emsp; + Compliance use cases                                | 27/10/2025   | 27/10/2025      | <https://cloudjourney.awsstudygroup.com/>    |
| 3   | - Học Snow Family: <br>&emsp; + Cold Data Transfer concept <br>&emsp; + Snowball (80TB) <br>&emsp; + Snowball Edge (100TB + compute) <br>&emsp; + Snowmobile (PB-EB scale)                                        | 28/10/2025   | 28/10/2025      | <https://cloudjourney.awsstudygroup.com/>    |
| 4   | - **Thực hành Archive:** <br>&emsp; + Config Glacier lifecycle <br>&emsp; + Test retrieve từ Glacier <br>&emsp; + Setup Object Lock <br>&emsp; + Tính toán chi phí archive                                         | 29/10/2025   | 29/10/2025      | <https://cloudjourney.awsstudygroup.com/>    |
| 5   | - Học Storage Gateway & DR: <br>&emsp; + File Gateway (NFS/SMB) <br>&emsp; + Volume Gateway (iSCSI) <br>&emsp; + Tape Gateway (VTL) <br>&emsp; + RTO vs RPO <br>&emsp; + 4 DR strategies                          | 30/10/2025   | 30/10/2025      | <https://cloudjourney.awsstudygroup.com/>    |
| 6   | - **Thực hành & Review:** <br>&emsp; + Setup File Gateway <br>&emsp; + Config AWS Backup <br>&emsp; + Thiết kế DR strategy <br>&emsp; + Review Module 04 <br>&emsp; + So sánh các storage services                | 31/10/2025   | 31/10/2025      | <https://cloudjourney.awsstudygroup.com/>    |

### Kết quả đạt được tuần 8:

* **Glacier & Archive:**
  * Hiểu use case cho long-term storage
  * Phân biệt Glacier và Glacier Deep Archive
  * Nắm được các retrieve options và chi phí
  * Biết cách dùng Object Lock cho compliance

* **Snow Family:**
  * Hiểu Cold Data Transfer concept
  * Phân biệt Snowball, Snowball Edge, Snowmobile
  * Biết khi nào nên dùng Snow Family
  * Hiểu pre-processing với Snowball Edge

* **Storage Gateway:**
  * Nắm được Hybrid Storage concept
  * Phân biệt 3 loại Gateway (File, Volume, Tape)
  * Hiểu use case của từng loại
  * Biết cách kết nối on-premise với AWS

* **Disaster Recovery:**
  * Hiểu khái niệm RTO và RPO
  * Nắm được 4 DR strategies:
    - Backup and Restore
    - Pilot Light
    - Warm Standby
    - Multi-site Active-Active
  * Biết cách chọn strategy phù hợp
  * Hiểu trade-off giữa chi phí và RTO/RPO

* **AWS Backup:**
  * Hiểu vai trò của centralized backup
  * Biết cách config backup policies
  * Nắm được retention và ảnh hưởng chi phí

* Hoàn thành Module 04 - Storage Services
* Có khả năng thiết kế giải pháp storage tối ưu