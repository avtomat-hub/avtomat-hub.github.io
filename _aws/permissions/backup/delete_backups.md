---
title: Delete Backups
parent: backup
grand_parent: Permissions
layout: default
permalink: /aws/permissions/backup/delete_backups
---

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "backup:DeleteRecoveryPoint"
            ],
            "Resource": "*"
        }
    ]
}

```