---
title: Create On Demand Backup
parent: backup
grand_parent: Actions
layout: default
permalink: /aws/actions/ec2/create_on_demand_backup
---

# Create On Demand Backup

Create on-demand backups for specified resources.<br/>

<p align="center">
   <a href="https://github.com/avtomat-hub/avtomat-aws/tree/main/avtomat_aws/backup/create_on_demand_backup.py">Source code</a> •
   <a href="/aws/permissions/backup/create_on_demand_backup">Permissions</a>
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
| `region`            | Region for operation. Leave blank for session default | `string`       | No       | Session Default             |
| `debug`             | Increase log verbosity                                | `bool`         | No       | False                       |
| `session`           | Established session                                   | `object`       | No       | None                        |                           |

### Output

Returns a `list` of resources that failed backup initiation:

```python
['i-1234567890abcdef0', 'i-abcdef1234567890']
```

## Examples

Create backups for EC2 instances:

```bash
aaws backup create_on_demand_backup --service ec2 --resource_ids i-1234567890abcdef0 i-abcdef1234567890
```

Programmatic usage:

```python
from avtomat_aws import backup

response = backup.create_on_demand_backup(service="ec2",
                                          resource_ids=["i-1234567890abcdef0", "i-abcdef1234567890"])
```
