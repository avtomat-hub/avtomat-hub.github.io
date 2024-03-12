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

Parameters are used for both programmatic input and command-line arguments.<br/>

- The `Applicable` column indicates whether the parameter is accepted in Programmatic (P), Command-Line (C), or Both (
  B).<br/>
- For Command-Line execution, type `list` parameters are passed as space-separated strings.

| Parameter       | Description                       | Type     | Applicable | Required         | Default value   |
|-----------------|-----------------------------------|----------|------------|------------------|-----------------|
| `access_key_id` | Access Key ID to delete           | `string` | B          | Yes              | None            |
| `username`      | User that owns the key            | `string` | B          | Yes              | None            |
| `enable`        | Enable access keys                | `bool`   | B          | If not `disable` | False           |
| `disable`       | Disable access keys               | `bool`   | B          | If not `enable`  | False           |
| `region`        | Region for operation              | `string` | B          | No               | Session default |
| `debug`         | Log verbosity                     | `bool`   | B          | No               | None            |
| `session`       | Established session               | `object` | P          | No               | None            |

### Output

Returns a `bool` indicating success or failure:

```python
True | False
```

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