---
title: Create Objects
parent: s3
grand_parent: Permissions
layout: default
permalink: /aws/permissions/s3/create_objects
---

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "s3:PutObject"
      ],
      "Resource": "*"
    }
  ]
}
```