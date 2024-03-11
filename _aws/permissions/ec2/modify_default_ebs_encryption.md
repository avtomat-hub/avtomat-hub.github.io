---
title: Modify Default EBS Encryption
parent: ec2
grand_parent: Permissions
layout: default
permalink: /aws/permissions/ec2/modify_default_ebs_encryption
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
        }
    ]
}
```