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

## Usage <button id="toggleButton" class="btn fs-3" onclick="toggleTables()">CLI</button>

### Input

| Parameter        | Description                                              | Type     | Required            | Default value   |
|------------------|----------------------------------------------------------|----------|---------------------|-----------------|
| `enable`         | Enable default EBS encryption                            | `bool`   | No                  | None            |
| `disable`        | Disable default EBS encryption                           | `bool`   | No                  | None            |
| `change_kms_key` | Change the KMS Key used for encryption                   | `bool`   | No                  | None            |
| `kms_key_id`     | KMS Key ID to use for encryption                         | `string` | If `change_kms_key` | None            |
| `reset_kms_key`  | Reset the KMS Key used for encryption to AWS EBS default | `bool`   | No                  | None            |
| `region`         | Region for operation. Leave blank for session default    | `string` | No                  | Session Default |
| `debug`          | Increase log verbosity                                   | `bool`   | No                  | False           |
| `silent`         | Decrease log verbosity                                   | `bool`   | No                  | False           |
| `session`        | Established session                                      | `object` | No                  | None            |

### Output

This function has no output.

<div markdown="1" id="cli" style="display: block;">

## Examples

Enable the default EBS encryption setting for eu-west-2:

```bash
aaws ec2 modify_default_ebs_encryption --enable --region eu-west-2
```

Change the KMS key used for default EBS encryption in us-east-1:

```bash
aaws ec2 modify_default_ebs_encryption --change_kms_key --kms_key_id abcd1234-a123-456a-a12b-a123b4cd56ef
```

</div>

<div markdown="1" id="prog" style="display: none;">

## Examples

Enable the default EBS encryption setting for eu-west-2:

```python
from avtomat_aws import ec2

response = ec2.modify_default_ebs_encryption(enable=True,
                                             region="eu-west-2")
```

Change the KMS key used for default EBS encryption in us-east-1:

```python
from avtomat_aws import ec2

response = ec2.modify_default_ebs_encryption(change_kms_key=True,
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
