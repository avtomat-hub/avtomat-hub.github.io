---
title: Delete Images
parent: ec2
grand_parent: Permissions
layout: default
permalink: /aws/permissions/ec2/delete_images
---

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "ec2:DescribeImages",
        "ec2:DeregisterImage",
        "ec2:DeleteSnapshot"
      ],
      "Resource": "*"
    }
  ]
}
```
