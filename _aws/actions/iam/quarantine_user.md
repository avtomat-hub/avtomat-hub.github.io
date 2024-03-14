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

| Parameter | Description          | Type     | Required | Default value   |
|-----------|----------------------|----------|----------|-----------------|
| `user`    | User to quarantine   | `string` | Yes      | None            |
| `region`  | Region for operation | `string` | No       | Session default |
| `debug`   | Log verbosity        | `bool`   | No       | False           |
| `session` | Established session  | `object` | No       | None            |

### Output

This function has no output.

## Examples

Quarantine a user:

```bash
aaws iam quarantine_user --user acme-user
```

Programmatic usage:

```python
from avtomat_aws import iam

response = iam.quarantine_user(user='acme-user')
```