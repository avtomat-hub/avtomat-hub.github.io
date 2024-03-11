---
title: Delete Security Groups
parent: ec2
grand_parent: Permissions
layout: default
permalink: /aws/permissions/ec2/delete_security_groups
---

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "ec2:DeleteSecurityGroup"
            ],
            "Resource": "*"
        }
    ]
}
```
