---
title: Discover Instances
parent: ec2
grand_parent: Permissions
layout: default
permalink: /aws/permissions/ec2/discover_instances
---

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "ec2:DescribeInstances"
            ],
            "Resource": "*"
        }
    ]
}
```