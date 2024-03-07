---
title: Modify User Console Access
parent: Identity and Access Management (IAM)
layout: default
---

# Modify User Console Access

Enable or disable AWS Management Console access for an IAM user.<br/>

{: .note }
When enabling console access the password provided is temporary. The user will be prompted to change it upon first login.<br/> 
The user will have the `IAMUserChangePassword` policy attached to allow the password change.

<p align="center">
   <a href="/avtomat_aws/iam/modify_user_console_access.py">Source code</a> •
   <a href="/permissions/iam/modify_user_console_access">Permissions</a>
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
| `role_arn` | AWS Role ARN for session creation     | `string` | B          | No               | None            |
| `region`   | Region for operation                  | `string` | B          | No               | Session default |
| `debug`    | Log verbosity                         | `bool`   | B          | No               | None            |
| `session`  | Established session                   | `object` | P          | No               | None            |

### Output

Returns a `bool` indicating success or failure:

```python
True | False
```

## Examples

Enable console access for a user:

```bash
aws_iam_modify_console_access --user acme-user --enable --password 'P@ssw0rd'
```

Programmatic usage:

```python
from avtomat_aws import iam

response = iam.modify_console_access(user='acme-user',
                                     enable=True,
                                     password='P@ssw0rd')
```