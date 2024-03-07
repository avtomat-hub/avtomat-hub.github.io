---
title: Modify Default EBS Encryption
parent: Elastic Compute Cloud (EC2)
layout: default
---

# Modify Default EBS Encryption

Change the default EBS encryption settings for a region.

<p align="center">
   <a href="/avtomat_aws/ec2/modify_default_ebs_encryption.py">Source code</a> •
   <a href="/permissions/ec2/modify_default_ebs_encryption">Permissions</a>
</p>

## Usage

### Input

Parameters are used for both programmatic input and command-line arguments.

- The `Applicable` column indicates whether the parameter is accepted in Programmatic (P), Command-Line (C), or Both (
  B).

| Parameter        | Description                                              | Type     | Applicable | Required            | Default value   |
|------------------|----------------------------------------------------------|----------|------------|---------------------|-----------------|
| `enable`         | Enable default EBS encryption                            | `bool`   | B          | No                  | None            |
| `disable`        | Disable default EBS encryption                           | `bool`   | B          | No                  | None            |
| `change_kms_key` | Change the KMS Key used for encryption                   | `bool`   | B          | No                  | None            |
| `kms_key_id`     | KMS Key ID to use for encryption                         | `string` | B          | If `change_kms_key` | None            |
| `reset_kms_key`  | Reset the KMS Key used for encryption to AWS EBS default | `bool`   | B          | No                  | None            |
| `role_arn`       | AWS Role ARN for session creation                        | `string` | B          | No                  | None            |
| `region`         | Region for operation. Leave blank for session default    | `string` | B          | No                  | Session Default |
| `debug`          | Log verbosity                                            | `bool`   | B          | No                  | None            |
| `session`        | Established session                                      | `object` | P          | No                  | None            |

### Output

This function has no output.

## Examples

Enable the default EBS encryption setting for eu-west-2:

```bash
aws_ec2_modify_default_ebs_encryption --enable --region eu-west-2
```

Programmatic usage:

```python
from avtomat_aws import ec2

response = ec2.modify_default_ebs_encryption(enable=True,
                                             region="eu-west-2")
```
