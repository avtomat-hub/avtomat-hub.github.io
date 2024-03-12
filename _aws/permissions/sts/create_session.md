---
title: Create Session
parent: sts
grand_parent: Permissions
layout: default
permalink: /aws/permissions/sts/create_session
---

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": "sts:GetCallerIdentity",
      "Resource": "*"
    },
    {
      "Effect": "Allow",
      "Action": "sts:AssumeRole",
      "Resource": "arn:aws:iam::123456789012:role/ExampleRole"
    }
  ]
}
```