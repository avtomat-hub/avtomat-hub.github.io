---
title: Delete Instances
parent: ec2
grand_parent: Permissions
layout: default
permalink: /aws/permissions/ec2/delete_instances
---

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "ec2:DescribeInstances",
        "ec2:DescribeVolumes",
        "ec2:DescribeSnapshots",
        "ec2:DescribeImages",
        "ec2:StopInstances",
        "ec2:TerminateInstances",
        "ec2:ModifyInstanceAttribute",
        "ec2:DeleteVolume",
        "ec2:DeleteSnapshot",
        "ec2:DeregisterImage",
        "ec2:CreateImage",
        "ec2:CreateTags"
      ],
      "Resource": "*"
    }
  ]
}
```
