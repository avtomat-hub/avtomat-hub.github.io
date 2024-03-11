---
title: Share Snapshots
parent: ec2
grand_parent: Permissions
layout: default
permalink: /aws/permissions/ec2/share_snapshots
---

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "ec2:ModifySnapshotAttribute"
            ],
            "Resource": "*"
        }
    ]
}
```