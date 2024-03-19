---
title: Discover Snapshots
parent: ec2
grand_parent: Actions
layout: default
permalink: /aws/actions/ec2/discover_snapshots
---

# Discover Snapshots

Discover snapshots of EBS volumes based on specified criteria.

<p align="center">
   <a href="https://github.com/avtomat-hub/avtomat-aws/tree/main/avtomat_aws/ec2/discover_snapshots.py">Source code</a> •
   <a href="/aws/permissions/ec2/discover_snapshots">Permissions</a>
</p>

{: .note}
Only snapshots owned by the account are returned.

## Usage

### Input

| Parameter            | Description                                           | Type           | Required | Default Value   |
|----------------------|-------------------------------------------------------|----------------|----------|-----------------|
| `volume_ids`         | Get snapshots that originate from specific volumes    | `list(string)` | No       | None            |
| `unencrypted`        | Get only unencrypted snapshots                        | `bool`         | No       | False           |
| `exclude_aws_backup` | Exclude snapshots managed by AWS Backup               | `bool`         | No       | False           |
| `created_before`     | Get snapshots created before date (YYYY/MM//DD)       | `string`       | No       | None            |
| `created_after`      | Get snapshots created after date (YYYY/MM//DD)        | `string`       | No       | None            |
| `region`             | Region for operation. Leave blank for session default | `string`       | No       | Session Default |
| `debug`              | Increase log verbosity                                | `bool`         | No       | False           |
| `session`            | Established session                                   | `object`       | No       | None            |

### Output

Returns a `list` of discovered snapshot IDs:

```python
['snap-1234567890abcdef0', 'snap-abcdef1234567890']
```

## Examples

Fetch all snapshots in eu-west-2:

```bash
aaws ec2 discover_snapshots --region eu-west-2
```

Fetch snapshots created before 2024/01/01 and not managed by AWS Backup:

```bash
aaws ec2 discover_snapshots --exclude__aws_backup --created_before 2024/01/01
```

Programmatic usage:

```python
from avtomat_aws import ec2

response = ec2.discover_snapshots(exclude_aws_backup=True,
                                  created_before="2024/01/01")
```
