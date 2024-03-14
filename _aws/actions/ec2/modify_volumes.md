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

| Parameter    | Description                                           | Type           | Required | Default Value   |
|--------------|-------------------------------------------------------|----------------|----------|-----------------|
| `volume_ids` | List of Volume IDs to modify                          | `list(string)` | Yes      | None            |
| `snapshot`   | Create snapshots before modification                  | `bool`         | No       | False           |
| `size`       | New size (GB) for volumes                             | `int`          | No       | None            |
| `type`       | New type for volumes                                  | `string`       | No       | None            |
| `iops`       | New IOPS for volumes                                  | `int`          | No       | None            |
| `region`     | Region for operation. Leave blank for session default | `string`       | No       | Session Default |
| `debug`      | Increase log verbosity                                | `bool`         | No       | False           |
| `session`    | Established session                                   | `object`       | No       | None            |                           

### Output

Returns a `list` of modified volume IDs:

```python
['vol-1234567890abcdef0', 'vol-abcdef1234567890']
```

## Examples

Change the size, type and iops of volumes with pre-modification snapshots:

```bash
aaws ec2 modify_volumes --volume_ids vol-1234567890abcdef0 vol-abcdef1234567890 --size 100 --type gp3 --iops 3000
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
