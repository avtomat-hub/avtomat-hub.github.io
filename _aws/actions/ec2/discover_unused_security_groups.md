---
title: Discover Unused Security Groups
parent: ec2
grand_parent: Actions
layout: default
permalink: /aws/actions/ec2/discover_unused_security_groups
---

# Discover Unused Security Groups

Discover unused security groups.<br/>
Resources checked:
- ENI
- EC2
- RDS
- ELB
- ELBv2
- Lambda
- Redshift
- ElastiCache
- EMR
- ECS
- Neptune
- OpenSearch
- MSK

<p align="center">
   <a href="https://github.com/avtomat-hub/avtomat-aws/tree/main/avtomat_aws/ec2/discover_unused_security_groups.py">Source code</a> •
   <a href="/aws/permissions/ec2/discover_unused_security_groups">Permissions</a>
</p>

## Usage

### Input

Parameters are used for both programmatic input and command-line arguments.<br/>

- The `Applicable` column indicates whether the parameter is accepted in Programmatic (P), Command-Line (C), or Both (B).<br/>
- For Command-Line execution, type `list` parameters are passed as space-separated strings.

| Parameter      | Description                       | Type           | Applicable | Required             | Default value                              |
|----------------|-----------------------------------|----------------|------------|----------------------|--------------------------------------------|
| `region`       | Region for operation              | `string`       | B          | No                   | Session default                            |
| `debug`        | Log verbosity                     | `bool`         | B          | No                   | None                                       |
| `session`      | Established session               | `object`       | P          | No                   | None                                       |

### Output

Returns a `list` of discovered security group IDs:

```python
['sg-1234567890abcdef0', 'sg-abcdef1234567890']
```

## Examples

Discover unused security groups:

```bash
aaws ec2 discover_unused_security_groups --region us-east-1
```

Programmatic usage:

```python
from avtomat_aws import ec2

response = ec2.discover_unused_security_groups(region='us-east-1')
```