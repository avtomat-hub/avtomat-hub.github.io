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

Parameters are used for both programmatic input and command-line arguments.<br/>

- The `Applicable` column indicates whether the parameter is accepted in Programmatic (P), Command-Line (C), or Both (
  B).<br/>
- For Command-Line execution, type `list` parameters are passed as space-separated strings.

| Parameter        | Description                                          | Type     | Applicable | Required | Default value   |
|------------------|------------------------------------------------------|----------|------------|----------|-----------------|
| `threshold_days` | Get roles not used for more than this number of days | `int`    | B          | Yes      | None            |
| `region`         | Region for operation                                 | `string` | B          | No       | Session default |
| `debug`          | Log verbosity                                        | `bool`   | B          | No       | None            |
| `session`        | Established session                                  | `object` | P          | No       | None            |

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