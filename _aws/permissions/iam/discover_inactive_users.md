---
title: Discover Inactive Users
parent: iam
grand_parent: Permissions
layout: default
permalink: /aws/permissions/iam/discover_inactive_users
---

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "iam:ListUsers",
                "iam:ListAccessKeys",
                "iam:GetUser",
                "iam:GetAccessKeyLastUsed"
            ],
            "Resource": "*"
        }
    ]
}
```