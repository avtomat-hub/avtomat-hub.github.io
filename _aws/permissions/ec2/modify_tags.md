---
title: Modify Tags
parent: ec2
grand_parent: Permissions
layout: default
permalink: /aws/permissions/ec2/modify_tags
---

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "ec2:CreateTags",
                "ec2:DeleteTags"
            ],
            "Resource": "*"
        }
    ]
}
```