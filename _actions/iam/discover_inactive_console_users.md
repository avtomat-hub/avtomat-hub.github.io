---
title: Discover Inactive Console Users
parent: Identity and Access Management (IAM)
layout: default
---

# Discover Inactive Console Users

Discover IAM users who haven't used the console over a certain period.<br/>

{: .note }
Users who have never used the console but have console access enabled are also returned.

{: .note }
This action only checks console activity. If you are looking to check console and programmatic (access key) activity, use <a href="/actions/iam/discover_inactive_users">discover_inactive_users</a> instead.

<p align="center">
   <a href="/avtomat_aws/iam/discover_inactive_console_users.py">Source code</a> •
   <a href="/permissions/iam/discover_inactive_console_users">Permissions</a>
</p>

## Usage

### Input

Parameters are used for both programmatic input and command-line arguments.<br/>

- The `Applicable` column indicates whether the parameter is accepted in Programmatic (P), Command-Line (C), or Both (
  B).<br/>
- For Command-Line execution, type `list` parameters are passed as space-separated strings.

| Parameter        | Description                                                  | Type     | Applicable | Required | Default value   |
|------------------|--------------------------------------------------------------|----------|------------|----------|-----------------|
| `threshold_days` | Get users with last console sign-in over this number of days | `int`    | B          | Yes      | None            |
| `role_arn`       | AWS Role ARN for session creation                            | `string` | B          | No       | None            |
| `region`         | Region for operation                                         | `string` | B          | No       | Session default |
| `debug`          | Log verbosity                                                | `bool`   | B          | No       | None            |
| `session`        | Established session                                          | `object` | P          | No       | None            |

### Output

Returns a `list` of discovered users:

```python
['user1', 'user2']
```

## Examples

Discover users who haven't used the console for more than 30 days:

```bash
aws_iam_discover_inactive_console_users --threshold_days 30
```

Programmatic usage:

```python
from avtomat_aws import iam

response = iam.discover_inactive_console_users(threshold_days=30)
```