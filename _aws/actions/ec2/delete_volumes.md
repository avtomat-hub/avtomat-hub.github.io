---
title: Delete Volumes
parent: ec2
grand_parent: Actions
layout: default
permalink: /aws/actions/ec2/delete_volumes
---

# Delete Volumes

Delete EBS volumes with optional pre-deletion snapshots.<br/>

{: .note}
Volumes must be in <b>available</b> state to be deleted.

{: .note}
Snapshots can be created before deletion if <b>snapshot</b> is supplied.

<p align="center">
   <a href="https://github.com/avtomat-hub/avtomat-aws/tree/main/avtomat_aws/ec2/delete_volumes.py">Source code</a> •
   <a href="/aws/permissions/ec2/delete_volumes">Permissions</a>
</p>

## Usage

### Input

Parameters are used for both programmatic input and command-line arguments.<br/>

- The `Applicable` column indicates whether the parameter is accepted in Programmatic (P), Command-Line (C), or Both (
  B).<br/>
- For Command-Line execution, type `list` parameters are passed as space-separated strings.

| Parameter    | Description                                           | Type           | Applicable | Required | Default Value   |
|--------------|-------------------------------------------------------|----------------|------------|----------|-----------------|
| `volume_ids` | List of Volume IDs to delete                          | `list(string)` | B          | Yes      | None            |
| `snapshot`   | Create snapshots before deletion                      | `bool`         | B          | No       | False           |
| `region`     | Region for operation. Leave blank for session default | `string`       | B          | No       | Session Default |
| `debug`      | Increase log verbosity                                | `bool`         | B          | No       | False           |
| `session`    | Established session                                   | `object`       | P          | No       | None            |                           |

### Output

Returns a `list` of deleted volume IDs:

```python
['vol-1234567890abcdef0', 'vol-abcdef1234567890']
```

## Examples

Delete volumes with pre-deletion snapshots:

```bash
aws_ec2_delete_volumes --volume_ids vol-1234567890abcdef0 vol-abcdef1234567890 --snapshot
```

Programmatic usage:

```python
from avtomat_aws import ec2

response = ec2.delete_volumes(volume_ids=["vol-1234567890abcdef0", "vol-abcdef1234567890"],
                              snapshot=True)
```
