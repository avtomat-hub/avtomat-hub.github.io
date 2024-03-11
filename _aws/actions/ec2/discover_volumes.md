---
title: Discover Volumes
parent: ec2
grand_parent: Actions
layout: default
permalink: /aws/actions/ec2/discover_volumes
---

# Discover Volumes

Discover EBS volumes based on specified criteria such as unencrypted status, volume types,
volumes of specific instances or simply all volumes.

<p align="center">
   <a href="https://github.com/avtomat-hub/avtomat-aws/tree/main/avtomat_aws/ec2/discover_volumes.py">Source code</a> •
   <a href="/aws/permissions/ec2/discover_volumes">Permissions</a>
</p>

## Usage

### Input

Parameters are used for both programmatic input and command-line arguments.<br/>

- The `Applicable` column indicates whether the parameter is accepted in Programmatic (P), Command-Line (C), or Both (
  B).<br/>
- For Command-Line execution, type `list` parameters are passed as space-separated strings.

| Parameter      | Description                                           | Type           | Applicable | Required | Default Value   |
|----------------|-------------------------------------------------------|----------------|------------|----------|-----------------|
| `instance_ids` | Instance IDs to check                                 | `list(string)` | B          | No       | All Instances   |
| `unencrypted`  | Get only unencrypted volumes                          | `bool`         | B          | No       | False           |
| `detached`     | Get only detached volumes                             | `bool`         | B          | No       | False           |
| `types`        | Get only specific type volumes                        | `list(string)` | B          | No       | None            |
| `region`       | Region for operation. Leave blank for session default | `string`       | B          | No       | Session Default |
| `debug`        | Increase log verbosity                                | `bool`         | B          | No       | False           |
| `session`      | Established session                                   | `object`       | P          | No       | None            |

### Output

Returns a `list` of discovered volume IDs:

```python
['vol-1234567890abcdef0', 'vol-abcdef1234567890']
```

## Examples

Fetch all volumes for specified instances:

```bash
aws_ec2_discover_volumes --instance_ids i-1234567890abcdef0 i-0987654321fedcba0
```

Fetch all detached and unencrypted volumes of type gp2 or gp3:

```bash
aws_ec2_discover_volumes --unencrypted --detached --types gp2 gp3
```

Programmatic usage:

```python
from avtomat_aws import ec2

response = ec2.discover_volumes(unencrypted=True,
                                detached=True,
                                types=['gp2', 'gp3'])
```
