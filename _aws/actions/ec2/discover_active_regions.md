---
title: Discover Active Regions
parent: ec2
grand_parent: Actions
layout: default
permalink: /aws/actions/ec2/discover_active_regions
---

# Discover Active Regions

Discover all active AWS regions for an account, which can be useful for dynamically targeting operations
across multiple regions.

<p align="center">
   <a href="https://github.com/avtomat-hub/avtomat-aws/tree/main/avtomat_aws/ec2/discover_active_regions.py">Source code</a> •
   <a href="/aws/permissions/ec2/discover_active_regions">Permissions</a>
</p>

## Usage

### Input

Parameters are used for both programmatic input and command-line arguments.

- The `Applicable` column indicates whether the parameter is accepted in Programmatic (P), Command-Line (C), or Both (B).

| Parameter  | Description                       | Type     | Applicable | Required | Default value |
|------------|-----------------------------------|----------|------------|----------|---------------|
| `debug`    | Log verbosity                     | `bool`   | B          | No       | None          |
| `session`  | Established session               | `object` | P          | No       | None          |

### Output

Returns a `list` of discovered regions:

```python
['us-east-1', 'us-west-2', 'eu-west-1']
```

## Examples

Discover active regions:

```bash
aws_ec2_discover_active_regions
```

Programmatic usage:

```python
from avtomat_aws import ec2

response = ec2.discover_active_regions()
```
