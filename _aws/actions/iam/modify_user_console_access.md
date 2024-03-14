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
When enabling console access the password provided is temporary. The user will be prompted to change it upon first login.<br/> 
The user will have the `IAMUserChangePassword` policy attached to allow the password change.

<p align="center">
   <a href="https://github.com/avtomat-hub/avtomat-aws/tree/main/avtomat_aws/iam/modify_user_console_access.py">Source code</a> •
   <a href="/aws/permissions/iam/modify_user_console_access">Permissions</a>
</p>

## Usage

### Input

Parameters are used for both programmatic input and command-line arguments.<br/>

- The `Applicable` column indicates whether the parameter is accepted in Programmatic (P), Command-Line (C), or Both (
  B).<br/>
- For Command-Line execution, type `list` parameters are passed as space-separated strings.

| Parameter  | Description                           | Type     | Applicable | Required         | Default value   |
|------------|---------------------------------------|----------|------------|------------------|-----------------|
| `user`     | Username to modify console access for | `string` | B          | Yes              | None            |
| `enable`   | Enable console access                 | `bool`   | B          | If not `disable` | False           |
| `disable`  | Disable console access                | `bool`   | B          | If not `enable`  | False           |
| `password` | New password for the user             | `string` | B          | If `enable`      | None            |
| `region`   | Region for operation                  | `string` | B          | No               | Session default |
| `debug`    | Log verbosity                         | `bool`   | B          | No               | None            |
| `session`  | Established session                   | `object` | P          | No               | None            |

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