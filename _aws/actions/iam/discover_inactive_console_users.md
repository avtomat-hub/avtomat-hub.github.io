---
title: Discover Inactive Console Users
parent: iam
grand_parent: Actions
layout: default
permalink: /aws/actions/iam/discover_inactive_console_users
---

# Discover Inactive Console Users

Discover IAM users who haven't used the console over a certain period.<br/>

{: .note }
Users who have never used the console but have console access enabled are also returned.

{: .note }
This action only checks console activity. If you are looking to check console and programmatic (access key) activity, use <a href="/actions/iam/discover_inactive_users">discover_inactive_users</a> instead.

<p align="center">
   <a href="https://github.com/avtomat-hub/avtomat-aws/tree/main/avtomat_aws/iam/discover_inactive_console_users.py">Source code</a> •
   <a href="/aws/permissions/iam/discover_inactive_console_users">Permissions</a>
</p>

## Usage

### Input

| Parameter        | Description                                                  | Type     | Required | Default value   |
|------------------|--------------------------------------------------------------|----------|----------|-----------------|
| `threshold_days` | Get users with last console sign-in over this number of days | `int`    | Yes      | None            |
| `region`         | Region for operation                                         | `string` | No       | Session default |
| `debug`          | Log verbosity                                                | `bool`   | No       | False           |
| `session`        | Established session                                          | `object` | No       | None            |

### Output

Returns a `list` of discovered users:

```python
['user1', 'user2']
```

## Examples

Discover users who haven't used the console for more than 30 days:

```bash
aaws iam discover_inactive_console_users --threshold_days 30
```

Programmatic usage:

```python
from avtomat_aws import iam

response = iam.discover_inactive_console_users(threshold_days=30)
```