---
title: Encrypt Instance Volumes
parent: ec2
grand_parent: Actions
layout: default
---

# Encrypt Instance Volumes

Encrypt or re-encrypt all EBS volumes attached to an instance with a KMS key.<br/>

{: .note}
For running instances downtime is minimized by stopping the instance only when volumes are ready to swap. (~2 min)

{: .warning}
If <b>re_encrypt</b> is supplied, already encrypted volumes will be re-encrypted.

Steps:

1. Create snapshots of all volumes
2. Create encrypted volumes from the snapshots with the specified KMS key
3. Copy tags from the original volumes to the encrypted volumes
4. Stop the instance
5. Detach original volumes
6. Attach encrypted volumes
    - Preserve original device names (e.g. /dev/sda1)
7. If instance was originally running:
    - Start the instance
8. Delete the snapshots
9. Original volumes remain for rollback purposes

<p align="center">
   <a href="/avtomat_aws/ec2/encrypt_instance_volumes.py">Source code</a> •
   <a href="/permissions/ec2/encrypt_instance_volumes">Permissions</a>
</p>

## Usage

### Input

Parameters are used for both programmatic input and command-line arguments.<br/>

- The `Applicable` column indicates whether the parameter is accepted in Programmatic (P), Command-Line (C), or Both (
  B).<br/>
- For Command-Line execution, type `list` parameters are passed as space-separated strings.

| Parameter     | Description                                           | Type     | Applicable | Required | Default Value   |
|---------------|-------------------------------------------------------|----------|------------|----------|-----------------|
| `instance_id` | Instance ID for volume encryption                     | `string` | B          | Yes      | None            |
| `kms_key_id`  | KMS Key ID to use for encryption                      | `string` | B          | Yes      | None            |
| `re_encrypt`  | Re-encrypt already encrypted volumes                  | `bool`   | B          | No       | False           |
| `role_arn`    | AWS Role ARN for session creation                     | `string` | B          | No       | None            |
| `region`      | Region for operation. Leave blank for session default | `string` | B          | No       | Session Default |
| `debug`       | Increase log verbosity                                | `bool`   | B          | No       | False           |
| `session`     | Established session                                   | `object` | P          | No       | None            |                           |

### Output

Returns a `string` of the encrypted instance ID:

```python
"i-1234567890abcdef0"
```

## Examples

Encrypt all instance volumes with a KMS key (already encrypted volumes are skipped):

```bash
aws_ec2_encrypt_instance_volumes --instance_id i-1234567890abcdef0 --kms_key_id abcd1234-a123-456a-a12b-a123b4cd56ef
```

Encrypt all instance volumes with a KMS key (already encrypted volumes are re-encrypted):

```bash
aws_ec2_encrypt_instance_volumes --re_encrypt --instance_id i-1234567890abcdef0 --kms_key_id abcd1234-a123-456a-a12b-a123b4cd56ef
```

Programmatic usage:

```python
from avtomat_aws import ec2

response = ec2.encrypt_instance_volumes(instance_id="i-1234567890abcdef0",
                                        kms_key_id="abcd1234-a123-456a-a12b-a123b4cd56ef")
```
