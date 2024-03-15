---
title: Modify Access Keys
parent: iam
grand_parent: Actions
layout: default
permalink: /aws/actions/iam/modify_access_key
---

# Modify Access Keys

Enable or disable an IAM access key.<br/>

<p align="center">
   <a href="https://github.com/avtomat-hub/avtomat-aws/tree/main/avtomat_aws/iam/modify_access_key.py">Source code</a> •
   <a href="/aws/permissions/iam/modify_access_key">Permissions</a>
</p>

## Usage

### Input

| Parameter       | Description             | Type     | Required         | Default value   |
|-----------------|-------------------------|----------|------------------|-----------------|
| `access_key_id` | Access Key ID to modify | `string` | Yes              | None            |
| `username`      | User that owns the key  | `string` | Yes              | None            |
| `enable`        | Enable access keys      | `bool`   | If not `disable` | False           |
| `disable`       | Disable access keys     | `bool`   | If not `enable`  | False           |
| `region`        | Region for operation    | `string` | No               | Session default |
| `debug`         | Log verbosity           | `bool`   | No               | False           |
| `session`       | Established session     | `object` | No               | None            |

### Output

This function has no output.

## Examples

Disable an access key for user:

```bash
aaws iam modify_access_key --access_key_id AKIA12ZAWVSH44WXASKY --username acme-user --disable
```

Programmatic usage:

```python
from avtomat_aws import iam

response = iam.modify_access_key(access_key_id='AKIA12ZAWVSH44WXASKY',
                                 username='acme-user',
                                 disable=True)
```