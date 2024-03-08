---
title: Quarantine User
parent: iam
grand_parent: Permissions
layout: default
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
        },
        {
            "Effect": "Allow",
            "Action": "sts:AssumeRole",
            "Resource": "arn:aws:iam::123456789012:role/ExampleRole"
        }
    ]
}
```