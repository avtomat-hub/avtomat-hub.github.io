---
title: Discover No SSM Instances
parent: ec2
grand_parent: Actions
layout: default
permalink: /aws/actions/ec2/discover_no_ssm_instances
---

# Discover No SSM Instances

Discover EC2 instances without SSM enabled.

<p align="center">
   <a href="https://github.com/avtomat-hub/avtomat-aws/tree/main/avtomat_aws/ec2/discover_no_ssm_instances.py">Source code</a> •
   <a href="/aws/permissions/ec2/discover_no_ssm_instances">Permissions</a>
</p>

## Usage

### Input

| Parameter      | Description              | Type           | Required | Default value   |
|----------------|--------------------------|----------------|----------|-----------------|
| `instance_ids` | Instance IDs to focus on | `list(string)` | No       | None            |
| `region`       | Region for operation     | `string`       | No       | Session default |
| `debug`        | Log verbosity            | `bool`         | No       | None            |
| `session`      | Established session      | `object`       | No       | None            |

### Output

Returns a `list` of discovered instance IDs:

```python
['i-1234567890abcdef0', 'i-abcdef1234567890']
```

## Examples

Discover instances without SSM enabled in eu-west-2:

```bash
aaws ec2 discover_no_ssm_instances --region eu-west-2
```

Discover if specific instances don't have SSM enabled:
```bash
aaws ec2 discover_no_ssm_instances --instance_ids i-1234567890abcdef0 i-abcdef1234567890
```

Programmatic usage:

```python
from avtomat_aws import ec2

response = ec2.discover_no_ssm_instances(instance_ids=['i-1234567890abcdef0', 'i-abcdef1234567890'])
```