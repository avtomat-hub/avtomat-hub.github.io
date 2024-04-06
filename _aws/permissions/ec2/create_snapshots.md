---
title: Create Snapshots
parent: ec2
grand_parent: Permissions
layout: default
permalink: /aws/permissions/ec2/create_snapshots
---

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "ec2:CreateSnapshot",
        "ec2:CreateTags",
        "ec2:DescribeSnapshots"
      ],
      "Resource": "*"
    }
  ]
}
```