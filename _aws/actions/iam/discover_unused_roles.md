---
title: Discover Unused Roles
parent: iam
grand_parent: Actions
layout: default
permalink: /aws/actions/iam/discover_unused_roles
---

# Discover Unused Roles

Discover IAM roles not used over a certain amount of days.<br/>

<p align="center">
   <a href="https://github.com/avtomat-hub/avtomat-aws/tree/main/avtomat_aws/iam/discover_unused_roles.py">Source code</a> •
   <a href="/aws/permissions/iam/discover_unused_roles">Permissions</a>
</p>

## Usage

### Input

| Parameter        | Description                                          | Type     | Required | Default value   |
|------------------|------------------------------------------------------|----------|----------|-----------------|
| `threshold_days` | Get roles not used for more than this number of days | `int`    | Yes      | None            |
| `region`         | Region for operation                                 | `string` | No       | Session default |
| `debug`          | Log verbosity                                        | `bool`   | No       | False           |
| `session`        | Established session                                  | `object` | No       | None            |

### Output

Returns a `list` of discovered roles:

```python
['role1', 'role2']
```

## Examples

Discover roles not used for more than 100 days:

```bash
aaws iam discover_unused_roles --threshold_days 100
```

Programmatic usage:

```python
from avtomat_aws import iam

response = iam.discover_unused_roles(threshold_days=100)
```