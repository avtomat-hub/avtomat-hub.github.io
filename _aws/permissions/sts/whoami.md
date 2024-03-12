---
title: Who Am I
parent: sts
grand_parent: Permissions
layout: default
permalink: /aws/permissions/sts/whoami
---

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": "sts:GetCallerIdentity",
      "Resource": "*"
    }
  ]
}
```