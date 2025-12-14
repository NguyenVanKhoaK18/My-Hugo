---
title: "AWS SDK for .NET v3 End-of-Support Announcement"
date: "2025-08-19"
weight: 2
chapter: false
pre: " <b> 3.2. </b> "
---

# Announcing end-of-support for AWS SDK for .NET v3

*By Ed McLaughlin | August 19, 2025*

We are announcing end-of-support for AWS SDK for .NET v3.x beginning March 1, 2026, per the SDK and Tools maintenance policy. On April 28, 2025, the next major version of AWS SDK for .NET, version 4.x, became generally available. Version 4.x of the SDK includes bug fixes, performance improvements, and modernization for .NET. We strongly encourage you to upgrade to take advantage of these improvements.

## Impact on existing applications

Existing applications using AWS SDK for .NET v3.x will continue to work as intended unless there is a fundamental change in how an AWS service operates. This is uncommon, and we will communicate broadly if it occurs. 

Beginning March 1, 2026, AWS SDK for .NET v3.x will only receive critical bug fixes and security updates, and we will not update it to support new AWS services, new service features, or changes to existing services. After June 1, 2026, when AWS SDK for .NET v3.x reaches end-of-support status, it will no longer receive updates or releases.

## End-of-support roadmap for version 3

The end-of-support roadmap is as follows, defined by the SDK major version lifecycle:

| Phase | Start Date | End Date | Support Level |
|-------|------------|----------|---------------|
| General Availability | July 28, 2015 | June 1, 2026 | During this phase, the SDK is fully supported. AWS will provide regular SDK releases, including support for new services, API updates for existing services, as well as bug fixes and security patches. |
| Maintenance Mode | March 1, 2026 | June 1, 2026 | In maintenance mode, AWS limits SDK releases to address only critical bugs and security issues. The SDK will not receive API updates for new or existing services, or be updated to support new regions. |
| End-of-Support | June 1, 2026 | N/A | When an SDK reaches end-of-support status, it will no longer receive updates or releases. Previously published releases will continue to be available through public package managers and source code will remain on GitHub. The GitHub repository may be archived. |

## Reference documentation for AWS SDK for .NET version 4

Use the following reference documentation to learn more about AWS SDK for .NET v4.x along with migration support:

- **Migrating to version 4 of the AWS SDK for .NET** - Migration guide for your AWS SDK for .NET v3.x applications to AWS SDK for .NET v4.x.
- **Development Tracker** - A development tracking tool for v4.x, containing additional details about some changes in the SDK. This can be useful for understanding more about the changes that have been implemented.
- **.NET v4.x Code Examples** - Code examples to help you use v4.x.

## Conclusion

We recommend upgrading to the latest major version of AWS SDK for .NET v4.x using the migration guide. This major version includes, but is not limited to, performance improvements, bug fixes, modern .NET libraries and frameworks, and the latest AWS service updates. 

To learn more, please refer to the blog post about the general availability release of AWS SDK for .NET.

If you need support or have feedback, please contact your usual AWS support contacts. You can also open a discussion or an issue on GitHub. Thank you for using AWS SDK for .NET.

---

## About the author

| <img src="/images/3-BlogsTranslated/3.2-Blog2/ed-mclaughlin.jpg" alt="Ed McLaughlin" width="80"> | **Ed McLaughlin** is a software development manager for the AWS SDK for .NET, .NET Developer Experience products, and AWS Tools for PowerShell. He enjoys working on projects, tools, and features that help improve the customer experience. You can find him on LinkedIn at [@ejm3](https://linkedin.com/in/ejm3). |
|---|---|