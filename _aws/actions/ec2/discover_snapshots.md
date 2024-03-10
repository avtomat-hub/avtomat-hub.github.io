---
title: Discover Snapshots
parent: ec2
grand_parent: Actions
layout: default
permalink: /aws/actions/ec2/discover_snapshots
---

# Discover Snapshots

Discover snapshots of EBS volumes based on specified criteria such as unencrypted status, source
volumes,
created before/after dates, or simply all snapshots.

<p align="center">
   <a href="https://github.com/avtomat-hub/avtomat-aws/tree/main/avtomat_aws/ec2/discover_snapshots.py">Source code</a> •
   <a href="/aws/permissions/ec2/discover_snapshots">Permissions</a>
</p>

## Usage

### Input

Parameters are used for both programmatic input and command-line arguments.<br/>

- The `Applicable` column indicates whether the parameter is accepted in Programmatic (P), Command-Line (C), or Both (
  B).<br/>
- For Command-Line execution, type `list` parameters are passed as space-separated strings.

| Parameter            | Description                                           | Type           | Applicable | Required | Default Value   |
|----------------------|-------------------------------------------------------|----------------|------------|----------|-----------------|
| `volume_ids`         | Get snapshots that originate from specific volumes    | `list(string)` | B          | No       | None            |
| `unencrypted`        | Get only unencrypted snapshots                        | `bool`         | B          | No       | False           |
| `exclude_aws_backup` | Exclude snapshots managed by AWS Backup               | `bool`         | B          | No       | False           |
| `created_before`     | Get snapshots created before date(YYYY/MM//DD)        | `string`       | B          | No       | None            |
| `created_after`      | Get snapshots created after date(YYYY/MM//DD)           | `string`       | B          | No       | None            |
| `role_arn`           | AWS Role ARN for session creation                     | `string`       | B          | No       | None            |
| `region`             | Region for operation. Leave blank for session default | `string`       | B          | No       | Session Default |
| `debug`              | Increase log verbosity                                | `bool`         | B          | No       | False           |
| `session`            | Established session                                   | `object`       | P          | No       | None            |

### Output

Returns a `list` of discovered snapshot IDs:

```python
['snap-1234567890abcdef0', 'snap-abcdef1234567890']
```

## Examples

Fetch all snapshots in eu-west-2:

```bash
aws_ec2_discover_snapshots --region eu-west-2
```

Fetch snapshots created before 2024/01/01 and not managed by AWS Backup:

```bash
aws_ec2_discover_snapshots --exclude__aws_backup --created_before 2024/01/01
```

Programmatic usage:

```python
from avtomat_aws import ec2

response = ec2.discover_snapshots(exclude_aws_backup=True,
                                  created_before="2024/01/01")
```
