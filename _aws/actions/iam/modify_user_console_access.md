---
title: Modify User Console Access
parent: iam
grand_parent: Actions
layout: default
permalink: /aws/actions/iam/modify_user_console_access
---

# Modify User Console Access

Enable or disable AWS Management Console access for an IAM user.<br/>

{: .note }
When enabling console access the password provided is temporary. The user will be prompted to change it upon first
login.<br/>
The user will have the `IAMUserChangePassword` policy attached to allow the password change.

<p align="center">
   <a href="https://github.com/avtomat-hub/avtomat-aws/tree/main/avtomat_aws/iam/modify_user_console_access.py">Source code</a> •
   <a href="/aws/permissions/iam/modify_user_console_access">Permissions</a>
</p>

## Usage

### Input

| Parameter  | Description                           | Type     | Required         | Default value   |
|------------|---------------------------------------|----------|------------------|-----------------|
| `user`     | Username to modify console access for | `string` | Yes              | None            |
| `enable`   | Enable console access                 | `bool`   | If not `disable` | False           |
| `disable`  | Disable console access                | `bool`   | If not `enable`  | False           |
| `password` | New password for the user             | `string` | If `enable`      | None            |
| `region`   | Region for operation                  | `string` | No               | Session default |
| `debug`    | Log verbosity                         | `bool`   | No               | False           |
| `session`  | Established session                   | `object` | No               | None            |

### Output

This function has no output.

## Examples

Enable console access for a user:

```bash
aaws iam modify_console_access --user acme-user --enable --password 'P@ssw0rd'
```

Programmatic usage:

```python
from avtomat_aws import iam

response = iam.modify_console_access(user='acme-user',
                                     enable=True,
                                     password='P@ssw0rd')
```