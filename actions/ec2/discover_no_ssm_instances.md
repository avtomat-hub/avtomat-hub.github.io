---
title: Discover No SSM Instances
parent: ec2
grand_parent: Actions
layout: default
---

# Discover No SSM Instances

Discover EC2 instances without SSM enabled.

<p align="center">
   <a href="/avtomat_aws/ec2/discover_no_ssm_instances.py">Source code</a> •
   <a href="/permissions/ec2/discover_no_ssm_instances">Permissions</a>
</p>

## Usage

### Input

Parameters are used for both programmatic input and command-line arguments.<br/>

- The `Applicable` column indicates whether the parameter is accepted in Programmatic (P), Command-Line (C), or Both (
  B).<br/>
- For Command-Line execution, type `list` parameters are passed as space-separated strings.

| Parameter  | Description                       | Type     | Applicable | Required | Default value   |
|------------|-----------------------------------|----------|------------|----------|-----------------|
| `role_arn` | AWS Role ARN for session creation | `string` | B          | No       | None            |
| `region`   | Region for operation              | `string` | B          | No       | Session default |
| `debug`    | Log verbosity                     | `bool`   | B          | No       | None            |
| `session`  | Established session               | `object` | P          | No       | None            |

### Output

Returns a `list` of discovered instance IDs:

```python
['i-1234567890abcdef0', 'i-abcdef1234567890']
```

## Examples

Discover instances without SSM enabled in eu-west-2:

```bash
aws_ec2_discover_no_ssm_instances --region eu-west-2
```

Programmatic usage:

```python
from avtomat_aws import ec2

response = ec2.discover_no_ssm_instances(region='eu-west-2')
```