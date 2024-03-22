---
title: Discover Old Password Users
parent: iam
grand_parent: Actions
layout: default
permalink: /aws/actions/iam/discover_old_password_users
---

# Discover Old Password Users

Discover IAM users with passwords older than a certain age.<br/>

<p align="center">
   <a href="https://github.com/avtomat-hub/avtomat-aws/tree/main/avtomat_aws/iam/discover_old_password_users.py">Source code</a> •
   <a href="/aws/permissions/iam/discover_old_password_users">Permissions</a>
</p>

## Usage

### Input

| Parameter        | Description                                              | Type     | Required | Default value   |
|------------------|----------------------------------------------------------|----------|----------|-----------------|
| `threshold_days` | Get users with a password older than this number of days | `int`    | Yes      | None            |
| `region`         | Region for operation                                     | `string` | No       | Session default |
| `debug`          | Log verbosity                                            | `bool`   | No       | False           |
| `session`        | Established session                                      | `object` | No       | None            |

### Output

Returns a `list of dictionaries` of discovered users:

```python
[
    {
        "UserName": "string"
    }
]
```

## Examples

Discover users with passwords older than 60 days:

```bash
aaws iam discover_old_password_users --threshold_days 60
```

Programmatic usage:

```python
from avtomat_aws import iam

response = iam.aws_iam_discover_old_password_users(threshold_days=60)
```