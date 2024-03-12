---
title: Encrypt Instance Volumes
parent: ec2
grand_parent: Permissions
layout: default
permalink: /aws/permissions/ec2/encrypt_instance_volumes
---

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "ec2:DescribeVolumes",
        "ec2:CreateSnapshot",
        "ec2:CreateVolume",
        "ec2:CreateTags",
        "ec2:AttachVolume",
        "ec2:DetachVolume",
        "ec2:DeleteSnapshot",
        "ec2:StopInstances",
        "ec2:StartInstances",
        "ec2:DescribeSnapshots",
        "ec2:DescribeInstances",
        "kms:Encrypt",
        "kms:Decrypt",
        "kms:ReEncrypt*",
        "kms:GenerateDataKey*",
        "kms:DescribeKey"
      ],
      "Resource": "*"
    }
  ]
}
```