---
title: "Worklog Tuần 11"
date: "2025-09-09"
weight: 11
chapter: false
pre: " <b> 1.11. </b> "
---

### Mục tiêu tuần 11:

* Tích hợp AWS Cognito vào hệ thống Authentication
* Setup Google OAuth 2.0 với Cognito
* Migrate từ custom JWT sang Cognito tokens
* Test flow đăng nhập với Google

### Project Phase: Authentication Enhancement

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                                      | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                         |
| --- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | -------------------------------------- |
| 2   | - **Setup AWS Cognito:** <br>&emsp; + Tạo User Pool <br>&emsp; + Config password policies <br>&emsp; + Setup email verification <br>&emsp; + Tạo App Client <br>&emsp; + Config callback URLs                  | 17/11/2025   | 17/11/2025      | |
| 3   | - **Setup Google OAuth:** <br>&emsp; + Tạo Google Cloud Project <br>&emsp; + Config OAuth consent screen <br>&emsp; + Tạo OAuth 2.0 credentials <br>&emsp; + Add Google Identity Provider vào Cognito          | 18/11/2025   | 18/11/2025      | |
| 4   | - **Update Backend APIs:** <br>&emsp; + Replace custom JWT với Cognito <br>&emsp; + Update Register API <br>&emsp; + Update Login API <br>&emsp; + Implement token verification <br>&emsp; + Update middleware | 19/11/2025   | 19/11/2025      |                                        |
| 5   | - **Implement Social Login:** <br>&emsp; + Hosted UI integration <br>&emsp; + Google login flow <br>&emsp; + Handle callback <br>&emsp; + Store user info in DynamoDB                                          | 20/11/2025   | 20/11/2025      |                                        |
| 6   | - **Testing & Documentation:** <br>&emsp; + Test register flow <br>&emsp; + Test login với email <br>&emsp; + Test login với Google <br>&emsp; + Update API docs <br>&emsp;        | 21/11/2025   | 21/11/2025      |                                        |

### Kết quả đạt được tuần 11:

* Setup Cognito User Pool với password policy và email verification
* Tạo App Client và config Hosted UI domain
* Tích hợp Google OAuth 2.0 làm Identity Provider
* Thay thế custom JWT bằng Cognito tokens
* Update Register/Login APIs sử dụng Cognito SDK
* Implement token verification middleware
* Xây dựng Google login flow hoàn chỉnh
* Sync user data giữa Cognito và DynamoDB
* Test authentication flows thành công (email + Google)
* Hiểu OAuth 2.0 flow và Social Identity Providers


