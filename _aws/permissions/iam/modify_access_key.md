---
title: Modify Access Key
parent: iam
grand_parent: Permissions
layout: default
permalink: /aws/permissions/iam/modify_access_key
---

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": "iam:UpdateAccessKey",
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