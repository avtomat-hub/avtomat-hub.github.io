---
title: Delete Instances
parent: ec2
grand_parent: Actions
layout: default
permalink: /aws/actions/ec2/delete_instances
---

# Delete Instances

Delete EC2 instances and, optionally, any associated resource types.

Steps:

1. Discover associated resources for each instance (images, volumes, snapshots)
2. If any of the instances are running, stop them
3. If specified, create an image (AMI) before proceeding with deletion
4. Delete the instances
5. If specified, delete associated resources

<p align="center">
   <a href="https://github.com/avtomat-hub/avtomat-aws/tree/main/avtomat_aws/services/ec2/delete_instances.py">Source code</a> •
   <a href="/aws/permissions/ec2/delete_instances">Permissions</a>
</p>

{: .note}
This action does not automatically disable termination or stop protection before deletion. <br>
To achieve this, supply the **disable_protections** parameter.

## Usage <button id="toggleButton" class="btn fs-3" onclick="toggleTables()">CLI</button>

### Input

| Parameter             | Description                                                            | Type           | Required | Default Value   |
|-----------------------|------------------------------------------------------------------------|----------------|----------|-----------------|
| `instance_ids`        | Instance IDs to delete                                                 | `list(string)` | Yes      | None            |
| `include`             | Associated resource types to delete <br> `volume`, `image`, `snapshot` | `list(string)` | No       | None            |
| `final_image`         | Create an image (AMI) before deletion                                  | `bool`         | No       | False           |
| `disable_protections` | Disable termination and stop protection before deletion                | `bool`         | No       | False           |
| `region`              | Region for operation. Leave blank for session default                  | `string`       | No       | Session Default |
| `debug`               | Increase log verbosity                                                 | `bool`         | No       | False           |
| `silent`              | Decrease log verbosity                                                 | `bool`         | No       | False           |
| `output`              | Output format <br/> `table`                                            | `string`       | No       | None            |
| `session`             | Established session                                                    | `object`       | No       | None            |

### Output

Returns a `dictionary` of resources that failed the deletion:

```python
{
    "Instances": ['i-1234567890abcdef0'],
    "Volumes": ['vol-1234567890abcdef0'],
    "Images": ['ami-1234567890abcdef0'],
    "Snapshots": ['snap-1234567890abcdef0']
}
```

<div markdown="1" id="cli" style="display: block;">

## Examples

Delete instances with pre-deletion images (AMIs):

```bash
aaws ec2 delete_instances --instance_ids i-1234567890abcdef0 i-abcdef1234567890 --final_image
```

Delete instances and associated resources:

```bash
aaws ec2 delete_instances --instance_ids i-1234567890abcdef0 i-abcdef1234567890 --include volume image snapshot
```

</div>

<div markdown="1" id="prog" style="display: none;">

## Examples

Delete instances with pre-deletion images (AMIs):

```python
from avtomat_aws import ec2

response = ec2.delete_instances(instance_ids=["i-1234567890abcdef0", "i-abcdef1234567890"],
                                final_image=True)
```

Delete instances and associated resources:

```python
from avtomat_aws import ec2

response = ec2.delete_instances(instance_ids=["i-1234567890abcdef0", "i-abcdef1234567890"],
                                include=["volume", "image", "snapshot"])
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