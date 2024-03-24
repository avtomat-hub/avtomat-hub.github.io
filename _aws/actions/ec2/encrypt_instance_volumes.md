---
title: Encrypt Instance Volumes
parent: ec2
grand_parent: Actions
layout: default
permalink: /aws/actions/ec2/encrypt_instance_volumes
---

# Encrypt Instance Volumes

Encrypt or re-encrypt all EBS volumes attached to an instance with a KMS key.<br/>

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
   <a href="https://github.com/avtomat-hub/avtomat-aws/tree/main/avtomat_aws/ec2/encrypt_instance_volumes.py">Source code</a> •
   <a href="/aws/permissions/ec2/encrypt_instance_volumes">Permissions</a>
</p>

{: .note}
For running instances downtime is minimized by stopping the instance only when volumes are ready to swap. (~2 min)

{: .warning}
If <b>re_encrypt</b> is supplied, already encrypted volumes will be re-encrypted.

## Usage <button id="toggleButton" class="btn fs-3" onclick="toggleTables()">CLI</button>

### Input

| Parameter     | Description                                           | Type     | Required | Default Value   |
|---------------|-------------------------------------------------------|----------|----------|-----------------|
| `instance_id` | Instance ID for volume encryption                     | `string` | Yes      | None            |
| `kms_key_id`  | KMS Key ID to use for encryption                      | `string` | Yes      | None            |
| `re_encrypt`  | Re-encrypt already encrypted volumes                  | `bool`   | No       | False           |
| `region`      | Region for operation. Leave blank for session default | `string` | No       | Session Default |
| `debug`       | Increase log verbosity                                | `bool`   | No       | False           |
| `session`     | Established session                                   | `object` | No       | None            |                           

### Output

Returns a `string` of the encrypted instance ID:

```python
"i-1234567890abcdef0"
```

<div markdown="1" id="cli" style="display: block;">

## Examples

Encrypt all instance volumes with a KMS key (already encrypted volumes are skipped):

```bash
aaws ec2 encrypt_instance_volumes --instance_id i-1234567890abcdef0 --kms_key_id abcd1234-a123-456a-a12b-a123b4cd56ef
```

Encrypt all instance volumes with a KMS key (already encrypted volumes are re-encrypted):

```bash
aaws ec2 encrypt_instance_volumes --re_encrypt --instance_id i-1234567890abcdef0 --kms_key_id abcd1234-a123-456a-a12b-a123b4cd56ef
```

</div>

<div markdown="1" id="prog" style="display: none;">

## Examples

Encrypt all instance volumes with a KMS key (already encrypted volumes are skipped):

```python
from avtomat_aws import ec2

response = ec2.encrypt_instance_volumes(instance_id="i-1234567890abcdef0",
                                        kms_key_id="abcd1234-a123-456a-a12b-a123b4cd56ef")
```

Encrypt all instance volumes with a KMS key (already encrypted volumes are re-encrypted):

```python
from avtomat_aws import ec2

response = ec2.encrypt_instance_volumes(re_encrypt=True,
                                        instance_id="i-1234567890abcdef0",
                                        kms_key_id="abcd1234-a123-456a-a12b-a123b4cd56ef")
```

</div>

<script>
  function toggleTables() {
    var cli = document.getElementById("cli");
    var prog = document.getElementById("prog");
    var toggleButton = document.getElementById("toggleButton");
    if (cli.style.display === "none") {
      cli.style.display = "block";
      prog.style.display = "none";
      toggleButton.innerHTML = "CLI";
    } else {
      cli.style.display = "none";
      prog.style.display = "block";
      toggleButton.innerHTML = "Programmatic";
    } 
  }
</script>
