---
title: Discover Tags
parent: ec2
grand_parent: Actions
layout: default
permalink: /aws/actions/ec2/discover_tags
---

# Discover Tags

Discover EC2 resources based on existing or missing tag.

Supported resource types:

- Image
- Instance
- Internet Gateway
- Key Pair
- Network ACL
- Route Table
- Security Group
- Snapshot
- Subnet
- Volume
- VPC

<p align="center">
   <a href="https://github.com/avtomat-hub/avtomat-aws/tree/main/avtomat_aws/ec2/discover_tags.py">Source code</a> •
   <a href="/aws/permissions/ec2/discover_tags">Permissions</a>
</p>

## Usage

### Input

| Parameter        | Description                                           | Type           | Required          | Default Value   |
|------------------|-------------------------------------------------------|----------------|-------------------|-----------------|
| `resource_types` | EC2 resource types to search through                  | `list(string)` | Yes               | None            |
| `tags`           | Tags in 'Key=Value' or 'Key' format to search for     | `list(string)` | Yes               | None            |
| `existing`       | Search for resources that have the tags               | `bool`         | If not `missing`  | None            |
| `missing`        | Search for resources that don't have the tags         | `bool`         | If not `existing` | None            |
| `region`         | Region for operation. Leave blank for session default | `string`       | No                | Session Default |
| `debug`          | Increase log verbosity                                | `bool`         | No                | False           |
| `session`        | Established session                                   | `object`       | No                | None            |

### Output

Returns a `list` of EC2 resource IDs:

```python
['vol-1234567890abcdef0', 'i-abcdef1234567890', 'snap-abcdef1234567890']
```

## Examples

Find security groups missing the 'Name' tag:

```bash
aaws ec2 discover_tags --resource_types security_group --tags Name --missing
```

Find instances and volumes with the 'Owner=Acme' tag:

```bash
aaws ec2 discover_tags --resource_types instance volume --tags Owner=Acme --existing
```

Programmatic usage:

```python
from avtomat_aws import ec2

response = ec2.discover_tags(resource_types=["instance", "volume"],
                             tags=["Owner=Acme"],
                             existing=True)
```
