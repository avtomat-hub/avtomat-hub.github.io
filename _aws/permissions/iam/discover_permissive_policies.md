---
title: Discover Permissive Policies
parent: iam
grand_parent: Permissions
layout: default
permalink: /aws/permissions/iam/discover_permissive_policies
---

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "iam:ListPolicies",
        "iam:GetPolicy",
        "iam:GetPolicyVersion"
      ],
      "Resource": "*"
    }
  ]
}
```