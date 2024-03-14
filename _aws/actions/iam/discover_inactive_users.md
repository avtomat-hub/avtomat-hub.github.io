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

| Parameter        | Description                                         | Type     | Required | Default value   |
|------------------|-----------------------------------------------------|----------|----------|-----------------|
| `threshold_days` | Get users with no activity over this number of days | `int`    | Yes      | None            |
| `region`         | Region for operation                                | `string` | No       | Session default |
| `debug`          | Log verbosity                                       | `bool`   | No       | False           |
| `session`        | Established session                                 | `object` | No       | None            |

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