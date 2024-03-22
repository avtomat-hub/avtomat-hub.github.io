---
title: Discover No MFA Users
parent: iam
grand_parent: Actions
layout: default
permalink: /aws/actions/iam/discover_no_mfa_users
---

# Discover No MFA Users

Discover IAM users without MFA enabled.<br/>

<p align="center">
   <a href="https://github.com/avtomat-hub/avtomat-aws/tree/main/avtomat_aws/iam/discover_no_mfa_users.py">Source code</a> •
   <a href="/aws/permissions/iam/discover_no_mfa_users">Permissions</a>
</p>

## Usage

### Input

| Parameter | Description          | Type     | Required | Default value   |
|-----------|----------------------|----------|----------|-----------------|
| `region`  | Region for operation | `string` | No       | Session default |
| `debug`   | Log verbosity        | `bool`   | No       | False           |
| `session` | Established session  | `object` | No       | None            |

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

Discover users without MFA enabled:

```bash
aaws iam discover_no_mfa_users
```

Programmatic usage:

```python
from avtomat_aws import iam

response = iam.discover_no_mfa_users()
```