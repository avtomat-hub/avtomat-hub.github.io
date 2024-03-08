---
title: Encrypt Volume
parent: ec2
grand_parent: Actions
layout: default
---

# Encrypt Volume

Encrypt or re-encrypt an EBS volume with a KMS key.<br/>

{: .note}
If you are looking to encrypt all volumes of an instance, use <a href="encrypt_instance_volumes.md">encrypt_instance_volumes</a> instead.

{: .note}
For volumes attached to running instances downtime is minimized by stopping the instance only when volumes are ready to swap. (~2 min)

{: .warning}
If <b>re_encrypt</b> is supplied and the volume is already encrypted, it will be re-encrypted.

Steps:

1. Create snapshot of the volume
2. Create encrypted volume from the snapshot with the specified KMS key
3. Copy tags from original volume to encrypted volume
4. If volume is attached to an instance:
    - Stop the instance
    - Detach original volume
    - Attach encrypted volume
        - Preserve original device name (e.g. /dev/sda1)
    - If instance was originally running:
        - Start the instance
5. Delete the snapshot
6. Original volume remains for rollback purposes

<p align="center">
   <a href="/avtomat_aws/ec2/encrypt_volume.py">Source code</a> •
   <a href="/permissions/ec2/encrypt_volume">Permissions</a>
</p>

## Usage

### Input

Parameters are used for both programmatic input and command-line arguments.<br/>

- The `Applicable` column indicates whether the parameter is accepted in Programmatic (P), Command-Line (C), or Both (
  B).<br/>
- For Command-Line execution, type `list` parameters are passed as space-separated strings.

| Parameter    | Description                                           | Type     | Applicable | Required | Default Value   |
|--------------|-------------------------------------------------------|----------|------------|----------|-----------------|
| `volume_id`  | Volume ID to encrypt                                  | `string` | B          | Yes      | None            |
| `kms_key_id` | KMS Key ID to use for encryption                      | `string` | B          | Yes      | None            |
| `re_encrypt` | Re-encrypt already encrypted volume                   | `bool`   | B          | No       | False           |
| `role_arn`   | AWS Role ARN for session creation                     | `string` | B          | No       | None            |
| `region`     | Region for operation. Leave blank for session default | `string` | B          | No       | Session Default |
| `debug`      | Increase log verbosity                                | `bool`   | B          | No       | False           |
| `session`    | Established session                                   | `object` | P          | No       | None            |                           |

### Output

Returns a `string` of the new, encrypted volume ID:

```python
"vol-1234567890abcdef0"
```

## Examples

Encrypt a volume with a KMS key: (skipped if already encrypted)

```bash
aws_ec2_encrypt_volume --volume_id vol-1234567890abcdef0 --kms_key_id abcd1234-a123-456a-a12b-a123b4cd56ef
```

Encrypt a volume with a KMS key: (re-encrypted if already encrypted)

```bash
aws_ec2_encrypt_volume --re_encrypt --volume_id vol-1234567890abcdef0 --kms_key_id abcd1234-a123-456a-a12b-a123b4cd56ef
```

Programmatic usage:

```python
from avtomat_aws import ec2

response = ec2.encrypt_volume(volume_id="vol-1234567890abcdef0",
                              kms_key_id="abcd1234-a123-456a-a12b-a123b4cd56ef")
```
