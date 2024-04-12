---
title: Discover Permissive Inline Policies
parent: iam
grand_parent: Permissions
layout: default
permalink: /aws/permissions/iam/discover_permissive_inline_policies
---

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "iam:ListUsers",
        "iam:ListUserPolicies",
        "iam:GetUserPolicy",
        "iam:ListGroups",
        "iam:ListGroupPolicies",
        "iam:GetGroupPolicy",
        "iam:ListRoles",
        "iam:ListRolePolicies",
        "iam:GetRolePolicy"
      ],
      "Resource": "*"
    }
  ]
}
```