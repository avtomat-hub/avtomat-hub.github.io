---
title: Encrypt Instance Volumes
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
                "ec2:DescribeVolumes",
                "ec2:CreateSnapshot",
                "ec2:CreateVolume",
                "ec2:CreateTags",
                "ec2:AttachVolume",
                "ec2:DetachVolume",
                "ec2:DeleteSnapshot",
                "ec2:StopInstances",
                "ec2:StartInstances",
                "ec2:DescribeSnapshots",
                "ec2:DescribeInstances",
                "kms:Encrypt",
                "kms:Decrypt",
                "kms:ReEncrypt*",
                "kms:GenerateDataKey*",
                "kms:DescribeKey"
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