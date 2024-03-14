---
title: Discover Default EBS Encryption
parent: ec2
grand_parent: Actions
layout: default
permalink: /aws/actions/ec2/discover_default_ebs_encryption
---

# Discover Default EBS Encryption

Discover the default EBS encryption settings for a region.

<p align="center">
   <a href="https://github.com/avtomat-hub/avtomat-aws/tree/main/avtomat_aws/ec2/discover_default_ebs_encryption.py">Source code</a> •
   <a href="/aws/permissions/ec2/discover_default_ebs_encryption">Permissions</a>
</p>

## Usage

### Input

| Parameter  | Description                                           | Type     | Required | Default value   |
|------------|-------------------------------------------------------|----------|----------|-----------------|
| `region`   | Region for operation. Leave blank for session default | `string` | No       | Session Default |
| `debug`    | Log verbosity                                         | `bool`   | No       | None            |
| `session`  | Established session                                   | `object` | No       | None            |

### Output

Returns a `dictionary` with keys:

```python
{
    "enabled": True|False,
    "kms_key_id": "arn:aws:kms:us-west-2:123456789012:key/1234abcd-12ab-34cd-56ef-1234567890ab"
}
```

## Examples

Discover default EBS encryption setting for eu-west-2:

```bash
aaws ec2 discover_default_ebs_encryption --region eu-west-2
```

Programmatic usage:

```python
from avtomat_aws import ec2

response = ec2.discover_default_ebs_encryption(region="eu-west-2")
```
