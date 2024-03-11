---
title: Discover Active Regions
parent: ec2
grand_parent: Permissions
layout: default
permalink: /aws/permissions/ec2/discover_active_regions
---

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "ec2:DescribeRegions"
            ],
            "Resource": "*"
        }
    ]
}
```