---
title: Discover Inactive Console Users
parent: iam
grand_parent: Permissions
layout: default
permalink: /aws/permissions/iam/discover_inactive_console_users
---

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "iam:ListUsers",
        "iam:GetUser",
        "iam:GetLoginProfile"
      ],
      "Resource": "*"
    }
  ]
}
```