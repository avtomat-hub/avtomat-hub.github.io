---
title: Discover Old Access Keys
parent: iam
grand_parent: Permissions
layout: default
permalink: /aws/permissions/iam/discover_old_access_keys
---

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "iam:ListUsers",
        "iam:ListAccessKeys"
      ],
      "Resource": "*"
    }
  ]
}
```
