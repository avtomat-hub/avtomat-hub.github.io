---
title: Delete Volumes
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
                "ec2:DeleteVolume",
                "ec2:CreateTags",
                "ec2:DescribeVolumes",
                "ec2:CreateSnapshot",
                "ec2:DescribeSnapshots"
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