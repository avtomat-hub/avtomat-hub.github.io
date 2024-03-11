---
title: Modify Volumes
parent: ec2
grand_parent: Actions
layout: default
permalink: /aws/actions/ec2/modify_volumes
---

# Modify Volumes

Change the Size, Type or IOPS of EBS volumes.<br/>

{: .note}
You must wait 6 hours after modifying a volume before you can modify it again.

{: .note}
Snapshots can be created before modification if <b>snapshot</b> is supplied.

{: .warning}
If increasing the size of a volume ensure to extend the server file system. <br/>
  <a href="https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/recognize-expanded-volume-linux.html" target="_blank">Linux</a> | <a href="https://docs.aws.amazon.com/AWSEC2/latest/WindowsGuide/recognize-expanded-volume-windows.html" target="_blank">Windows</a>

<p align="center">
   <a href="https://github.com/avtomat-hub/avtomat-aws/tree/main/avtomat_aws/ec2/modify_volumes.py">Source code</a> •
   <a href="/aws/permissions/ec2/modify_volumes">Permissions</a>
</p>

## Usage

### Input

Parameters are used for both programmatic input and command-line arguments.<br/>

- The `Applicable` column indicates whether the parameter is accepted in Programmatic (P), Command-Line (C), or Both (
  B).<br/>
- For Command-Line execution, type `list` parameters are passed as space-separated strings.

| Parameter    | Description                                           | Type           | Applicable | Required | Default Value   |
|--------------|-------------------------------------------------------|----------------|------------|----------|-----------------|
| `volume_ids` | List of Volume IDs to modify                          | `list(string)` | B          | Yes      | None            |
| `snapshot`   | Create snapshots before modification                  | `bool`         | B          | No       | False           |
| `size`       | New size (GB) for volumes                             | `int`          | B          | No       | None            |
| `type`       | New type for volumes                                  | `string`       | B          | No       | None            |
| `iops`       | New IOPS for volumes                                  | `int`          | B          | No       | None            |
| `region`     | Region for operation. Leave blank for session default | `string`       | B          | No       | Session Default |
| `debug`      | Increase log verbosity                                | `bool`         | B          | No       | False           |
| `session`    | Established session                                   | `object`       | P          | No       | None            |                           |

### Output

Returns a `list` of modified volume IDs:

```python
['vol-1234567890abcdef0', 'vol-abcdef1234567890']
```

## Examples

Change the size, type and iops of volumes with pre-modification snapshots:

```bash
aws_ec2_modify_volumes --volume_ids vol-1234567890abcdef0 vol-abcdef1234567890 --size 100 --type gp3 --iops 3000
```

Programmatic usage:

```python
from avtomat_aws import ec2

response = ec2.modify_volumes(volume_ids=["vol-1234567890abcdef0", "vol-abcdef1234567890"],
                              size=100,
                              type="gp3",
                              iops=3000,
                              snapshot=True)
```
