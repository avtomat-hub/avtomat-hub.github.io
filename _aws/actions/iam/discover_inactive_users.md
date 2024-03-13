---
title: Discover Inactive Users
parent: iam
grand_parent: Actions
layout: default
permalink: /aws/actions/iam/discover_inactive_users
---

# Discover Inactive Users

Discover IAM users who haven't used the console and any access keys over a certain period.<br/>

<p align="center">
   <a href="https://github.com/avtomat-hub/avtomat-aws/tree/main/avtomat_aws/iam/discover_inactive_users.py">Source code</a> •
   <a href="/aws/permissions/iam/discover_inactive_users">Permissions</a>
</p>

## Usage

### Input

Parameters are used for both programmatic input and command-line arguments.<br/>

- The `Applicable` column indicates whether the parameter is accepted in Programmatic (P), Command-Line (C), or Both (
  B).<br/>
- For Command-Line execution, type `list` parameters are passed as space-separated strings.

| Parameter        | Description                                         | Type     | Applicable | Required | Default value   |
|------------------|-----------------------------------------------------|----------|------------|----------|-----------------|
| `threshold_days` | Get users with no activity over this number of days | `int`    | B          | Yes      | None            |
| `region`         | Region for operation                                | `string` | B          | No       | Session default |
| `debug`          | Log verbosity                                       | `bool`   | B          | No       | None            |
| `session`        | Established session                                 | `object` | P          | No       | None            |

### Output

Returns a `list` of discovered users:

```python
['user1', 'user2']
```

## Examples

Discover users with no activity over 30 days:

```bash
aaws iam discover_inactive_users --threshold_days 30
```

Programmatic usage:

```python
from avtomat_aws import iam

response = iam.discover_inactive_users(threshold_days=30)
```