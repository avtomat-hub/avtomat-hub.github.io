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

Parameters are used for both programmatic input and command-line arguments.<br/>

- The `Applicable` column indicates whether the parameter is accepted in Programmatic (P), Command-Line (C), or Both (
  B).<br/>
- For Command-Line execution, type `list` parameters are passed as space-separated strings.

| Parameter        | Description                                              | Type     | Applicable | Required | Default value   |
|------------------|----------------------------------------------------------|----------|------------|----------|-----------------|
| `threshold_days` | Get users with a password older than this number of days | `int`    | B          | Yes      | None            |
| `role_arn`       | AWS Role ARN for session creation                        | `string` | B          | No       | None            |
| `region`         | Region for operation                                     | `string` | B          | No       | Session default |
| `debug`          | Log verbosity                                            | `bool`   | B          | No       | None            |
| `session`        | Established session                                      | `object` | P          | No       | None            |

### Output

Returns a `list` of discovered users:

```python
['user1', 'user2']
```

## Examples

Discover users with passwords older than 60 days:

```bash
aws_iam_discover_old_password_users --threshold_days 60
```

Programmatic usage:

```python
from avtomat_aws import iam

response = iam.aws_iam_discover_old_password_users(threshold_days=60)
```