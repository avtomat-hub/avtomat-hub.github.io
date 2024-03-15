---
title: Create Backups
parent: backup
grand_parent: Actions
layout: default
permalink: /aws/actions/ec2/create_backups
---

# Create On Demand Backup

Start an on-demand backup job for the specified resources.<br/>

<p align="center">
   <a href="https://github.com/avtomat-hub/avtomat-aws/tree/main/avtomat_aws/backup/create_backups.py">Source code</a> •
   <a href="/aws/permissions/backup/create_backups">Permissions</a>
</p>

## Usage

### Input

| Parameter           | Description                                           | Type           | Required | Default Value               |
|---------------------|-------------------------------------------------------|----------------|----------|-----------------------------|
| `resource_ids`      | Resource IDs to create backups for                    | `list(string)` | Yes      | None                        |
| `service`           | Service to which the resource IDs belong              | `string`       | Yes      | None                        |
| `backup_vault_name` | Backup vault in which to store the backups            | `string`       | No       | Default                     |
| `retention_days`    | Number of days to retain the backups                  | `int`          | No       | 14                          |
| `iam_role`          | Role ARN used to create the backup                    | `string`       | No       | AWSBackupDefaultServiceRole |
| `wait`              | Wait for backups to complete before proceeding        | `bool`         | No       | False                       |
| `region`            | Region for operation. Leave blank for session default | `string`       | No       | Session Default             |
| `debug`             | Increase log verbosity                                | `bool`         | No       | False                       |
| `session`           | Established session                                   | `object`       | No       | None                        |                           

### Output

Returns a `list` of resources that failed the backups:

```python
['i-1234567890abcdef0', 'i-abcdef1234567890']
```

## Examples

Create backups for EC2 instances and wait for completion:

```bash
aaws backup create_backups --service ec2 --resource_ids i-1234567890abcdef0 i-abcdef1234567890 --wait
```

Programmatic usage:

```python
from avtomat_aws import backup

response = backup.create_backups(service="ec2",
                                 resource_ids=["i-1234567890abcdef0", "i-abcdef1234567890"],
                                 wait=True)
```
