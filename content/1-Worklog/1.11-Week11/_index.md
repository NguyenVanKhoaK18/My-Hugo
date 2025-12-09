---
title: "Week 11 Worklog"
date: "2025-09-09"
weight: 11
chapter: false
pre: " <b> 1.11. </b> "
---

### Week 11 Objectives:

* Integrate AWS Cognito into Authentication system
* Setup Google OAuth 2.0 with Cognito
* Migrate from custom JWT to Cognito tokens
* Test login flow with Google

### Project Phase: Authentication Enhancement

### Tasks to be carried out this week:
| Day | Task                                                                                                                                                                                                   | Start Date | Completion Date | Reference Material                        |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- | --------------- | ----------------------------------------- |
| 2   | - **Setup AWS Cognito:** <br>&emsp; + Create User Pool <br>&emsp; + Configure password policies <br>&emsp; + Setup email verification <br>&emsp; + Create App Client <br>&emsp; + Configure callback URLs | 17/11/2025 | 17/11/2025      | |
| 3   | - **Setup Google OAuth:** <br>&emsp; + Create Google Cloud Project <br>&emsp; + Configure OAuth consent screen <br>&emsp; + Create OAuth 2.0 credentials <br>&emsp; + Add Google Identity Provider to Cognito | 18/11/2025 | 18/11/2025      | |
| 4   | - **Update Backend APIs:** <br>&emsp; + Replace custom JWT with Cognito <br>&emsp; + Update Register API <br>&emsp; + Update Login API <br>&emsp; + Implement token verification <br>&emsp; + Update middleware | 19/11/2025 | 19/11/2025      | |
| 5   | - **Implement Social Login:** <br>&emsp; + Hosted UI integration <br>&emsp; + Google login flow <br>&emsp; + Handle callback <br>&emsp; + Store user info in DynamoDB | 20/11/2025 | 20/11/2025      | |
| 6   | - **Testing & Documentation:** <br>&emsp; + Test register flow <br>&emsp; + Test login with email <br>&emsp; + Test login with Google <br>&emsp; + Update API docs | 21/11/2025 | 21/11/2025      | |

### Week 11 Achievements:

* Setup Cognito User Pool with password policy and email verification
* Created App Client and configured Hosted UI domain
* Integrated Google OAuth 2.0 as Identity Provider
* Replaced custom JWT with Cognito tokens
* Updated Register/Login APIs using Cognito SDK
* Implemented token verification middleware
* Built complete Google login flow
* Synced user data between Cognito and DynamoDB
* Successfully tested authentication flows (email + Google)
* Understood OAuth 2.0 flow and Social Identity Providers