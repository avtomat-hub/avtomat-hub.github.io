---
title: Modify Default EBS Encryption
parent: ec2
grand_parent: Actions
layout: default
permalink: /aws/actions/ec2/modify_default_ebs_encryption
---

# Modify Default EBS Encryption

Change the default EBS encryption settings for a region.

<p align="center">
   <a href="https://github.com/avtomat-hub/avtomat-aws/tree/main/avtomat_aws/ec2/modify_default_ebs_encryption.py">Source code</a> •
   <a href="/aws/permissions/ec2/modify_default_ebs_encryption">Permissions</a>
</p>

## Usage

### Input

| Parameter        | Description                                              | Type     | Required            | Default value   |
|------------------|----------------------------------------------------------|----------|---------------------|-----------------|
| `enable`         | Enable default EBS encryption                            | `bool`   | No                  | None            |
| `disable`        | Disable default EBS encryption                           | `bool`   | No                  | None            |
| `change_kms_key` | Change the KMS Key used for encryption                   | `bool`   | No                  | None            |
| `kms_key_id`     | KMS Key ID to use for encryption                         | `string` | If `change_kms_key` | None            |
| `reset_kms_key`  | Reset the KMS Key used for encryption to AWS EBS default | `bool`   | No                  | None            |
| `region`         | Region for operation. Leave blank for session default    | `string` | No                  | Session Default |
| `debug`          | Log verbosity                                            | `bool`   | No                  | None            |
| `session`        | Established session                                      | `object` | No                  | None            |

### Output

This function has no output.

## Examples

Enable the default EBS encryption setting for eu-west-2:

```bash
aaws ec2 modify_default_ebs_encryption --enable --region eu-west-2
```

Programmatic usage:

```python
from avtomat_aws import ec2

response = ec2.modify_default_ebs_encryption(enable=True,
                                             region="eu-west-2")
```
