---
title: Modify User Console Access
parent: Identity and Access Management (IAM)
layout: default
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
        },
        {
            "Effect": "Allow",
            "Action": "sts:AssumeRole",
            "Resource": "arn:aws:iam::123456789012:role/ExampleRole"
        }
    ]
}
```