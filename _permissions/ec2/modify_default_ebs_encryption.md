---
title: Modify Default EBS Encryption
parent: Elastic Compute Cloud (EC2)
layout: default
---

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "ec2:EnableEbsEncryptionByDefault",
                "ec2:DisableEbsEncryptionByDefault",
                "ec2:ModifyEbsDefaultKmsKeyId",
                "ec2:ResetEbsDefaultKmsKeyId"
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