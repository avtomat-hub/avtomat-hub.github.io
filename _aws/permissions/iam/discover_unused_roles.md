---
title: Discover Unused Roles
parent: iam
grand_parent: Permissions
layout: default
permalink: /aws/permissions/iam/discover_unused_roles
---

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "iam:ListRoles",
                "iam:GetRole"
            ],
            "Resource": "*"
        }
    ]
}
```