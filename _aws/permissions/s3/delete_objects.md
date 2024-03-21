---
title: Delete Objects
parent: s3
grand_parent: Permissions
layout: default
permalink: /aws/permissions/s3/delete_objects
---

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "s3:ListBucket",
        "s3:DeleteObject"
      ],
      "Resource": "*"
    }
  ]
}
```