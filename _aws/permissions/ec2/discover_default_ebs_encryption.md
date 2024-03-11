---
title: Discover Default EBS Encryption
parent: ec2
grand_parent: Permissions
layout: default
permalink: /aws/permissions/ec2/discover_default_ebs_encryption
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
        }
    ]
}
```