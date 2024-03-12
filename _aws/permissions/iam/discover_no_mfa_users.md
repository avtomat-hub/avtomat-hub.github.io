---
title: Discover No MFA Users
parent: iam
grand_parent: Permissions
layout: default
permalink: /aws/permissions/iam/discover_no_mfa_users
---

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "iam:ListUsers",
        "iam:ListMFADevices"
      ],
      "Resource": "*"
    }
  ]
}
```