---
title: Delete Snapshots
parent: ec2
grand_parent: Actions
layout: default
permalink: /aws/actions/ec2/delete_snapshots
---

# Delete Snapshots

Delete EBS snapshots.<br/>

<p align="center">
   <a href="https://github.com/avtomat-hub/avtomat-aws/tree/main/avtomat_aws/ec2/delete_snapshots.py">Source code</a> •
   <a href="/aws/permissions/ec2/delete_snapshots">Permissions</a>
</p>

## Usage

### Input

Parameters are used for both programmatic input and command-line arguments.<br/>

- The `Applicable` column indicates whether the parameter is accepted in Programmatic (P), Command-Line (C), or Both (
  B).<br/>
- For Command-Line execution, type `list` parameters are passed as space-separated strings.

| Parameter      | Description                                           | Type           | Applicable | Required | Default Value   |
|----------------|-------------------------------------------------------|----------------|------------|----------|-----------------|
| `snapshot_ids` | List of Snapshot IDs to delete                        | `list(string)` | B          | Yes      | None            |
| `region`       | Region for operation. Leave blank for session default | `string`       | B          | No       | Session Default |
| `debug`        | Increase log verbosity                                | `bool`         | B          | No       | False           |
| `session`      | Established session                                   | `object`       | P          | No       | None            |                           

### Output

Returns a `list` of deleted snapshot IDs:

```python
['snap-1234567890abcdef0', 'snap-abcdef1234567890']
```

## Examples

Delete snapshots in eu-west-2:

```bash
aws_ec2_delete_snapshots --snapshot_ids snap-1234567890abcdef0 snap-abcdef1234567890 --region eu-west-2
```

Programmatic usage:

```python
from avtomat_aws import ec2

response = ec2.delete_snapshots(volume_ids=["snap-1234567890abcdef0", "snap-abcdef1234567890"],
                                region="eu-west-2")
```
