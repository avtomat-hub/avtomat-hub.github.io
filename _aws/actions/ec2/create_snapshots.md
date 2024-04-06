---
title: Create Snapshots
parent: ec2
grand_parent: Actions
layout: default
permalink: /aws/actions/ec2/create_snapshots
---

# Create Snapshots

Create snapshots of EBS volumes. </br>

<p align="center">
   <a href="https://github.com/avtomat-hub/avtomat-aws/tree/main/avtomat_aws/services/ec2/create_snapshots.py">Source code</a> •
   <a href="/aws/permissions/ec2/create_snapshots">Permissions</a>
</p>

## Usage <button id="toggleButton" class="btn fs-3" onclick="toggleTables()">CLI</button>

### Input

| Parameter    | Description                                           | Type           | Required | Default Value   |
|--------------|-------------------------------------------------------|----------------|----------|-----------------|
| `volume_ids` | Volume IDs to create snapshots for                    | `list(string)` | Yes      | None            |
| `region`     | Region for operation. Leave blank for session default | `string`       | No       | Session Default |
| `debug`      | Increase log verbosity                                | `bool`         | No       | False           |
| `silent`     | Decrease log verbosity                                | `bool`         | No       | False           |
| `session`    | Established session                                   | `object`       | No       | None            |

### Output

Returns a `list` of snapshot IDs that were created:

```python
['snap-1234567890abcdef0', 'snap-abcdef1234567890']
```

<div markdown="1" id="cli" style="display: block;">

## Examples

Create snapshots of volumes:

```bash
aaws ec2 create_snapshots --volume_ids vol-1234567890abcdef0 vol-abcdef1234567890
```

</div>

<div markdown="1" id="prog" style="display: none;">

## Examples

Create snapshots of volumes:

```python
from avtomat_aws import ec2

response = ec2.create_snapshots(volume_ids=["vol-1234567890abcdef0", "vol-abcdef1234567890"])
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