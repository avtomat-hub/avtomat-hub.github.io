---
title: Discover No SSM Instances
parent: ec2
grand_parent: Permissions
layout: default
permalink: /aws/permissions/ec2/discover_no_ssm_instances
---

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "ec2:DescribeInstances",
        "ssm:DescribeInstanceInformation"
      ],
      "Resource": "*"
    }
  ]
}
```