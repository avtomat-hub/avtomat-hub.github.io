---
title: Discover Inactive Users
parent: Identity and Access Management (IAM)
layout: default
---

# Discover Inactive Users

Discover IAM users who haven't used the console and any access keys over a certain period.<br/>

<p align="center">
   <a href="/avtomat_aws/iam/discover_inactive_users.py">Source code</a> •
   <a href="/permissions/iam/discover_inactive_users">Permissions</a>
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
| `role_arn`       | AWS Role ARN for session creation                   | `string` | B          | No       | None            |
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
aws_iam_discover_inactive_users --threshold_days 30
```

Programmatic usage:

```python
from avtomat_aws import iam

response = iam.discover_inactive_users(threshold_days=30)
```