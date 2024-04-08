---
title: Create Images
parent: ec2
grand_parent: Permissions
layout: default
permalink: /aws/permissions/ec2/create_images
---

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "ec2:CreateImage",
        "ec2:DescribeInstances",
        "ec2:DescribeImages",
        "ec2:CreateTags"
      ],
      "Resource": "*"
    }
  ]
}
```