---
title: Modify Volumes
parent: ec2
grand_parent: Permissions
layout: default
permalink: /aws/permissions/ec2/modify_volumes
---

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "ec2:DescribeVolumes",
                "ec2:ModifyVolume",
                "ec2:CreateSnapshot",
                "ec2:DescribeSnapshots",
                "ec2:CreateTags"
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