---
title: Create Images
parent: ec2
grand_parent: Actions
layout: default
permalink: /aws/actions/ec2/create_images
---

# Create Images

Create images (AMI) of EC2 instances.

<p align="center">
   <a href="https://github.com/avtomat-hub/avtomat-aws/tree/main/avtomat_aws/services/ec2/create_images.py">Source code</a> •
   <a href="/aws/permissions/ec2/create_images">Permissions</a>
</p>

{: .note}
**reboot** ensures that all buffered data and data in memory is written to the volumes before the snapshots are created.<br>
If **reboot** is not specified, underlying snapshots only contain the data that has been written to the volumes. Buffered data and data in memory that has not yet been written to the volumes is not included in the snapshots.

{: .warning}
**reboot** can cause service interruptions. Handle with caution in production and outside maintenance windows.

## Usage <button id="toggleButton" class="btn fs-3" onclick="toggleTables()">CLI</button>

### Input

| Parameter      | Description                                           | Type           | Required | Default Value   |
|----------------|-------------------------------------------------------|----------------|----------|-----------------|
| `instance_ids` | Instance IDs to create images for                     | `list(string)` | Yes      | None            |
| `reboot`       | Reboot instances before creating the images           | `bool`         | No       | False           |
| `region`       | Region for operation. Leave blank for session default | `string`       | No       | Session Default |
| `debug`        | Increase log verbosity                                | `bool`         | No       | False           |
| `silent`       | Decrease log verbosity                                | `bool`         | No       | False           |
| `output`       | Output format <br/> `table`                           | `string`       | No       | None            |
| `session`      | Established session                                   | `object`       | No       | None            |


### Output

Returns a `list` of image IDs created:

```python
['ami-1234567890abcdef0', 'ami-abcdef1234567890']
```

<div markdown="1" id="cli" style="display: block;">

## Examples

Create images of instances without reboot:

```bash
aaws ec2 create_images --instance_ids i-1234567890abcdef0 i-abcdef1234567890
```

Create images of instances with reboot:

```bash
aaws ec2 create_images --instance_ids i-1234567890abcdef0 i-abcdef1234567890 --reboot
```

</div>

<div markdown="1" id="prog" style="display: none;">

## Examples

Create images of instances without reboot:

```python
from avtomat_aws import ec2

response = ec2.create_images(instance_ids=["i-1234567890abcdef0", "i-abcdef1234567890"])
```

Create images of instances with reboot:

```python
from avtomat_aws import ec2

response = ec2.create_images(instance_ids=["i-1234567890abcdef0", "i-abcdef1234567890"], reboot=True)
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