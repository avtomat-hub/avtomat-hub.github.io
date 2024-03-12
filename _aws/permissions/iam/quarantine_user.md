---
title: Quarantine User
parent: iam
grand_parent: Permissions
layout: default
permalink: /aws/permissions/iam/quarantine_user
---

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "iam:GetUser",
        "iam:ListAccessKeys",
        "iam:UpdateAccessKey",
        "iam:DeleteLoginProfile",
        "iam:AttachUserPolicy"
      ],
      "Resource": "*"
    }
  ]
}
```