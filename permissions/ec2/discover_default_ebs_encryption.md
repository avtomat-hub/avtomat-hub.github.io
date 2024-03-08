---
title: Discover Default EBS Encryption
parent: ec2
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
                "ec2:GetEbsEncryptionByDefault",
                "ec2:GetEbsDefaultKmsKeyId"
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