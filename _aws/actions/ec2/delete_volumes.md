---
title: Delete Volumes
parent: ec2
grand_parent: Actions
layout: default
permalink: /aws/actions/ec2/delete_volumes
---

# Delete Volumes

Delete EBS volumes with optional pre-deletion snapshots.<br/>

<p align="center">
   <a href="https://github.com/avtomat-hub/avtomat-aws/tree/main/avtomat_aws/ec2/delete_volumes.py">Source code</a> •
   <a href="/aws/permissions/ec2/delete_volumes">Permissions</a>
</p>

{: .note}
Volumes must be in <b>available</b> state to be deleted.

{: .note}
Snapshots can be created before deletion if <b>snapshot</b> is supplied.

## Usage <button id="toggleButton" class="btn fs-3" onclick="toggleTables()">CLI</button>

### Input

| Parameter    | Description                                           | Type           | Required | Default Value   |
|--------------|-------------------------------------------------------|----------------|----------|-----------------|
| `volume_ids` | List of Volume IDs to delete                          | `list(string)` | Yes      | None            |
| `snapshot`   | Create snapshots before deletion                      | `bool`         | No       | False           |
| `region`     | Region for operation. Leave blank for session default | `string`       | No       | Session Default |
| `debug`      | Increase log verbosity                                | `bool`         | No       | False           |
| `silent`     | Decrease log verbosity                                | `bool`         | No       | False           |
| `session`    | Established session                                   | `object`       | No       | None            |                           

### Output

Returns a `list` of volume IDs that failed the deletion:

```python
['vol-1234567890abcdef0', 'vol-abcdef1234567890']
```

<div markdown="1" id="cli" style="display: block;">

## Examples

Delete volumes with pre-deletion snapshots:

```bash
aaws ec2 delete_volumes --volume_ids vol-1234567890abcdef0 vol-abcdef1234567890 --snapshot
```

</div>

<div markdown="1" id="prog" style="display: none;">

## Examples

Delete volumes with pre-deletion snapshots:

```python
from avtomat_aws import ec2

response = ec2.delete_volumes(volume_ids=["vol-1234567890abcdef0", "vol-abcdef1234567890"],
                              snapshot=True)
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
