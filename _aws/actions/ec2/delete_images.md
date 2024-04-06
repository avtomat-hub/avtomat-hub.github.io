---
title: Delete Images
parent: ec2
grand_parent: Actions
layout: default
permalink: /aws/actions/ec2/delete_images
---

# Delete Images

Delete EC2 images (AMI).<br/>

<p align="center">
   <a href="https://github.com/avtomat-hub/avtomat-aws/tree/main/avtomat_aws/services/ec2/delete_images.py">Source code</a> •
   <a href="/aws/permissions/ec2/delete_images">Permissions</a>
</p>

{: .note}
Images managed by AWS Backup cannot be deleted using this action. Instead,
use [Delete Backups](/aws/actions/backup/delete_backups).

## Usage <button id="toggleButton" class="btn fs-3" onclick="toggleTables()">CLI</button>

### Input

| Parameter           | Description                                           | Type           | Required | Default Value   |
|---------------------|-------------------------------------------------------|----------------|----------|-----------------|
| `image_ids`         | List of Image IDs to delete                           | `list(string)` | Yes      | None            |
| `include_snapshots` | Delete snapshots associated with this image           | `bool`         | No       | False           |
| `region`            | Region for operation. Leave blank for session default | `string`       | No       | Session Default |
| `debug`             | Increase log verbosity                                | `bool`         | No       | False           |
| `silent`            | Decrease log verbosity                                | `bool`         | No       | False           |
| `session`           | Established session                                   | `object`       | No       | None            |                           

### Output

Returns a `list` of image IDs that failed the deletion:

```python
['ami-1234567890abcdef0', 'ami-abcdef1234567890']
```

<div markdown="1" id="cli" style="display: block;">

## Examples

Delete images but leave snapshots:

```bash
aaws ec2 delete_images --image_ids ami-1234567890abcdef0 ami-abcdef1234567890
```

Delete images and associated snapshots:

```bash
aaws ec2 delete_images --image_ids ami-1234567890abcdef0 ami-abcdef1234567890 --include_snapshots
```

</div>

<div markdown="1" id="prog" style="display: none;">

## Examples

Delete images but leave snapshots:

```python
from avtomat_aws import ec2

response = ec2.delete_images(image_ids=["ami-1234567890abcdef0", "ami-abcdef1234567890"])
```

Delete images and associated snapshots:

```python
from avtomat_aws import ec2

response = ec2.delete_images(image_ids=["ami-1234567890abcdef0", "ami-abcdef1234567890"],
                             include_snapshots=True)
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
