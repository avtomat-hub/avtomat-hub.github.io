---
title: Modify Users Console Access
parent: iam
grand_parent: Permissions
layout: default
permalink: /aws/permissions/iam/modify_users_console_access
---

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "iam:CreateLoginProfile",
        "iam:DeleteLoginProfile",
        "iam:AttachUserPolicy"
      ],
      "Resource": "*"
    }
  ]
}
```