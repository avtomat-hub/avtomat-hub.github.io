---
title: Delete Backups
parent: backup
grand_parent: Actions
layout: default
permalink: /aws/actions/backup/delete_backups
---

# Delete Backups

Delete backup recovery points from a vault.<br/>

<p align="center">
   <a href="https://github.com/avtomat-hub/avtomat-aws/tree/main/avtomat_aws/backup/delete_backups.py">Source code</a> •
   <a href="/aws/permissions/backup/delete_backups">Permissions</a>
</p>

{: .danger}
Deleting a recovery point deletes the underlying backup data (e.g. AMIs, Snapshots, etc.) Use with caution.

## Usage <button id="toggleButton" class="btn fs-3" onclick="toggleTables()">CLI</button>

### Input

| Parameter             | Description                                           | Type           | Required | Default Value   |
|-----------------------|-------------------------------------------------------|----------------|----------|-----------------|
| `backup_vault_name`   | Backup vault from which to delete recovery points     | `string`       | Yes      | None            |
| `recovery_point_arns` | Recovery point ARNs to delete                         | `list(string)` | Yes      | None            |
| `region`              | Region for operation. Leave blank for session default | `string`       | No       | Session Default |
| `debug`               | Increase log verbosity                                | `bool`         | No       | False           |
| `session`             | Established session                                   | `object`       | No       | None            |                           

### Output

Returns a `list` of recovery points that failed the deletion:

```python
['arn:aws:ec2:us-east-1::image/ami-abcdef1234567890']
```

<div markdown="1" id="cli" style="display: block;">

## Examples

Delete backups from Default backup vault:

```bash
aaws backup delete_backups --backup_vault_name Default --recovery_point_arns arn:aws:ec2:us-east-1::image/ami-1234567890abcdef0 arn:aws:ec2:us-east-1::image/ami-abcdef1234567890
```

</div>

<div markdown="1" id="prog" style="display: none;">

## Examples

Delete backups from Default backup vault:

```python
from avtomat_aws import backup

response = backup.delete_backups(recovery_point_arns=["arn:aws:ec2:us-east-1::image/ami-1234567890abcdef0", 
                                                      "arn:aws:ec2:us-east-1::image/ami-abcdef1234567890"])
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