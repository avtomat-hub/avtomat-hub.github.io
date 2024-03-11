---
title: Quarantine User
parent: iam
grand_parent: Actions
layout: default
permalink: /aws/actions/iam/quarantine_user
---

# Quarantine User

Disable console and programmatic access and apply `AWSCompromisedKeyQuarantineV2` policy to an IAM user.<br/>

{: .danger }
Current password of the user will be deleted and will not be recoverable.<br/>
  
{: .note}
Access keys are deactivated but not deleted.

<p align="center">
   <a href="https://github.com/avtomat-hub/avtomat-aws/tree/main/avtomat_aws/iam/quarantine_user.py">Source code</a> •
   <a href="/aws/permissions/iam/quarantine_user">Permissions</a>
</p>

## Usage

### Input

Parameters are used for both programmatic input and command-line arguments.<br/>

- The `Applicable` column indicates whether the parameter is accepted in Programmatic (P), Command-Line (C), or Both (
  B).<br/>
- For Command-Line execution, type `list` parameters are passed as space-separated strings.

| Parameter  | Description                       | Type     | Applicable | Required | Default value   |
|------------|-----------------------------------|----------|------------|----------|-----------------|
| `user`     | User to quarantine                | `string` | B          | Yes      | None            |
| `region`   | Region for operation              | `string` | B          | No       | Session default |
| `debug`    | Log verbosity                     | `bool`   | B          | No       | None            |
| `session`  | Established session               | `object` | P          | No       | None            |

### Output

Returns a `bool` indicating success or failure:

```python
True | False
```

## Examples

Quarantine a user:

```bash
aws_iam_quarantine_user --user acme-user
```

Programmatic usage:

```python
from avtomat_aws import iam

response = iam.quarantine_user(user='acme-user')
```