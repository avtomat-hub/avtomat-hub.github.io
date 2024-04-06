---
title: Delete Snapshots
parent: ec2
grand_parent: Actions
layout: default
permalink: /aws/actions/ec2/delete_snapshots
---

# Delete Snapshots

Delete EBS snapshots.<br/>

<p align="center">
   <a href="https://github.com/avtomat-hub/avtomat-aws/tree/main/avtomat_aws/services/ec2/delete_snapshots.py">Source code</a> •
   <a href="/aws/permissions/ec2/delete_snapshots">Permissions</a>
</p>

{: .note}
Snapshots managed by AWS Backup cannot be deleted using this action. Instead,
use [Delete Backups](/aws/actions/backup/delete_backups).

## Usage <button id="toggleButton" class="btn fs-3" onclick="toggleTables()">CLI</button>

### Input

| Parameter      | Description                                           | Type           | Required | Default Value   |
|----------------|-------------------------------------------------------|----------------|----------|-----------------|
| `snapshot_ids` | List of Snapshot IDs to delete                        | `list(string)` | Yes      | None            |
| `region`       | Region for operation. Leave blank for session default | `string`       | No       | Session Default |
| `debug`        | Increase log verbosity                                | `bool`         | No       | False           |
| `silent`       | Decrease log verbosity                                | `bool`         | No       | False           |
| `session`      | Established session                                   | `object`       | No       | None            |                           

### Output

Returns a `list` of snapshot IDs that failed the deletion:

```python
['snap-1234567890abcdef0', 'snap-abcdef1234567890']
```

<div markdown="1" id="cli" style="display: block;">

## Examples

Delete snapshots in eu-west-2:

```bash
aaws ec2 delete_snapshots --snapshot_ids snap-1234567890abcdef0 snap-abcdef1234567890 --region eu-west-2
```

</div>

<div markdown="1" id="prog" style="display: none;">

## Examples

Delete snapshots in eu-west-2:

```python
from avtomat_aws import ec2

response = ec2.delete_snapshots(snapshot_ids=["snap-1234567890abcdef0", "snap-abcdef1234567890"],
                                region="eu-west-2")
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
