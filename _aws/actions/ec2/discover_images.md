---
title: Discover Images
parent: ec2
grand_parent: Actions
layout: default
permalink: /aws/actions/ec2/discover_images
---

# Discover Images

Discover EC2 images (AMI) based on specified criteria.

<p align="center">
   <a href="https://github.com/avtomat-hub/avtomat-aws/tree/main/avtomat_aws/ec2/discover_images.py">Source code</a> •
   <a href="/aws/permissions/ec2/discover_images">Permissions</a>
</p>

{: .note}
Only images owned by the account are returned.

## Usage

### Input

| Parameter            | Description                                           | Type           | Required | Default Value   |
|----------------------|-------------------------------------------------------|----------------|----------|-----------------|
| `image_ids`          | Image IDs to focus on                                 | `list(string)` | No       | All images      |
| `public`             | Get only publicly exposed images                      | `bool`         | No       | False           |
| `exclude_aws_backup` | Exclude snapshots managed by AWS Backup               | `bool`         | No       | False           |
| `created_before`     | Get snapshots created before date (YYYY/MM//DD)       | `string`       | No       | None            |
| `created_after`      | Get snapshots created after date (YYYY/MM//DD)        | `string`       | No       | None            |
| `region`             | Region for operation. Leave blank for session default | `string`       | No       | Session Default |
| `debug`              | Increase log verbosity                                | `bool`         | No       | False           |
| `session`            | Established session                                   | `object`       | No       | None            |

### Output

Returns a `list` of discovered image IDs:

```python
['ami-1234567890abcdef0', 'ami-abcdef1234567890']
```

## Examples

Fetch all images in eu-west-2:

```bash
aaws ec2 discover_images --region eu-west-2
```

Fetch images created before 2024/01/01 and not managed by AWS Backup:

```bash
aaws ec2 discover_images --exclude__aws_backup --created_before 2024/01/01
```

Programmatic usage:

```python
from avtomat_aws import ec2

response = ec2.discover_images(exclude_aws_backup=True,
                               created_before="2024/01/01")
```
