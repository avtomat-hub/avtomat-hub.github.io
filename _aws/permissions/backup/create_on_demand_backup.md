---
title: Create On Demand Backup
parent: backup
grand_parent: Permissions
layout: default
permalink: /aws/permissions/iam/create_on_demand_backup
---

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "backup:StartBackupJob"
            ],
            "Resource": [
                "arn:aws:backup:*:*:backup-vault:*"
            ]
        },
        {
            "Effect": "Allow",
            "Action": [
                "sts:GetCallerIdentity"
            ],
            "Resource": "*"
        }
    ]
}

```