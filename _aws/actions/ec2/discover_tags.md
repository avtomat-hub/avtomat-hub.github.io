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

{: .note}
Multiple resource types can be specified, however only one tag key/value is supported.

<p align="center">
   <a href="https://github.com/avtomat-hub/avtomat-aws/tree/main/avtomat_aws/ec2/discover_tags.py">Source code</a> •
   <a href="/aws/permissions/ec2/discover_tags">Permissions</a>
</p>

## Usage

### Input

Parameters are used for both programmatic input and command-line arguments.<br/>

- The `Applicable` column indicates whether the parameter is accepted in Programmatic (P), Command-Line (C), or Both (
  B).<br/>
- For Command-Line execution, type `list` parameters are passed as space-separated strings.

| Parameter        | Description                                           | Type           | Applicable | Required          | Default Value   |
|------------------|-------------------------------------------------------|----------------|------------|-------------------|-----------------|
| `resource_types` | EC2 resource types to search through                  | `list(string)` | B          | Yes               | None            |
| `key`            | Tag key to search for                                 | `string`       | B          | Yes               | None            |
| `value`          | Tag value to search for                               | `string`       | B          | No                | None            |
| `existing`       | Search for resources that have the tag                | `bool`         | B          | If not `missing`  | None            |
| `missing`        | Search for resources that don't have the tag          | `bool`         | B          | If not `existing` | None            |
| `role_arn`       | AWS Role ARN for session creation                     | `string`       | B          | No                | None            |
| `region`         | Region for operation. Leave blank for session default | `string`       | B          | No                | Session Default |
| `debug`          | Increase log verbosity                                | `bool`         | B          | No                | False           |
| `session`        | Established session                                   | `object`       | P          | No                | None            |

### Output

Returns a `list` of EC2 resource IDs:

```python
['vol-1234567890abcdef0', 'i-abcdef1234567890', 'snap-abcdef1234567890']
```

## Examples

Find security groups missing the 'Name' tag:

```bash
aws_ec2_discover_tags --resource_types security_group --key Name --missing
```

Find instances and volumes with the 'Owner:Acme' tag:

```bash
aws_ec2_discover_tags --resource_types instance volume --key Owner --value Acme --existing
```

Programmatic usage:

```python
from avtomat_aws import ec2

response = ec2.discover_tags(resource_types=["instance", "volume"],
                             key="Owner",
                             value="Acme",
                             existing=True)
```
