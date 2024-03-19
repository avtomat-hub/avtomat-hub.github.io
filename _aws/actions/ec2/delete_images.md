---
title: Delete Images
parent: ec2
grand_parent: Actions
layout: default
permalink: /aws/actions/ec2/delete_images
---

# Delete Images

Delete EC2 images (AMI).<br/>

<p align="center">
   <a href="https://github.com/avtomat-hub/avtomat-aws/tree/main/avtomat_aws/ec2/delete_images.py">Source code</a> •
   <a href="/aws/permissions/ec2/delete_images">Permissions</a>
</p>

{: .warning}
Images managed by AWS Backup cannot be deleted using this action. Instead,
use [Delete Backups](/aws/actions/backup/delete_backups).

## Usage

### Input

| Parameter           | Description                                           | Type           | Required | Default Value   |
|---------------------|-------------------------------------------------------|----------------|----------|-----------------|
| `image_ids`         | List of Image IDs to delete                           | `list(string)` | Yes      | None            |
| `include_snapshots` | Delete snapshots associated with this image           | `bool`         | No       | False           |
| `region`            | Region for operation. Leave blank for session default | `string`       | No       | Session Default |
| `debug`             | Increase log verbosity                                | `bool`         | No       | False           |
| `session`           | Established session                                   | `object`       | No       | None            |                           

### Output

Returns a `list` of image IDs that failed the deletion:

```python
['ami-1234567890abcdef0', 'ami-abcdef1234567890']
```

## Examples

Delete images but leave snapshots:

```bash
aaws ec2 delete_images --image_ids ami-1234567890abcdef0 ami-abcdef1234567890
```

Delete images and associated snapshots:

```bash
aaws ec2 delete_images --image_ids ami-1234567890abcdef0 ami-abcdef1234567890 --include_snapshots
```

Programmatic usage:

```python
from avtomat_aws import ec2

response = ec2.delete_images(image_ids=["ami-1234567890abcdef0", "ami-abcdef1234567890"],
                             include_snapshots=True)
```
