---
title: Encrypt Volume
parent: ec2
grand_parent: Actions
layout: default
permalink: /aws/actions/ec2/encrypt_volume
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
   <a href="https://github.com/avtomat-hub/avtomat-aws/tree/main/avtomat_aws/ec2/encrypt_volume.py">Source code</a> •
   <a href="/aws/permissions/ec2/encrypt_volume">Permissions</a>
</p>

## Usage

### Input

| Parameter    | Description                                           | Type     | Required | Default Value   |
|--------------|-------------------------------------------------------|----------|----------|-----------------|
| `volume_id`  | Volume ID to encrypt                                  | `string` | Yes      | None            |
| `kms_key_id` | KMS Key ID to use for encryption                      | `string` | Yes      | None            |
| `re_encrypt` | Re-encrypt already encrypted volume                   | `bool`   | No       | False           |
| `region`     | Region for operation. Leave blank for session default | `string` | No       | Session Default |
| `debug`      | Increase log verbosity                                | `bool`   | No       | False           |
| `session`    | Established session                                   | `object` | No       | None            |                           

### Output

Returns a `string` of the new, encrypted volume ID:

```python
"vol-1234567890abcdef0"
```

## Examples

Encrypt a volume with a KMS key: (skipped if already encrypted)

```bash
aaws ec2 encrypt_volume --volume_id vol-1234567890abcdef0 --kms_key_id abcd1234-a123-456a-a12b-a123b4cd56ef
```

Encrypt a volume with a KMS key: (re-encrypted if already encrypted)

```bash
aaws ec2 encrypt_volume --re_encrypt --volume_id vol-1234567890abcdef0 --kms_key_id abcd1234-a123-456a-a12b-a123b4cd56ef
```

Programmatic usage:

```python
from avtomat_aws import ec2

response = ec2.encrypt_volume(volume_id="vol-1234567890abcdef0",
                              kms_key_id="abcd1234-a123-456a-a12b-a123b4cd56ef")
```
