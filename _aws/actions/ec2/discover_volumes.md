---
title: Discover Volumes
parent: ec2
grand_parent: Actions
layout: default
permalink: /aws/actions/ec2/discover_volumes
---

# Discover Volumes

Discover EBS volumes based on specified criteria.

<p align="center">
   <a href="https://github.com/avtomat-hub/avtomat-aws/tree/main/avtomat_aws/ec2/discover_volumes.py">Source code</a> •
   <a href="/aws/permissions/ec2/discover_volumes">Permissions</a>
</p>

## Usage <button id="toggleButton" class="btn fs-3" onclick="toggleTables()">CLI</button>

### Input

| Parameter      | Description                                           | Type           | Required | Default Value   |
|----------------|-------------------------------------------------------|----------------|----------|-----------------|
| `instance_ids` | Get volumes attached to specified instances           | `list(string)` | No       | All instances   |
| `volume_ids`   | Volume IDs to focus on                                | `list(string)` | No       | All volumes     |
| `unencrypted`  | Get only unencrypted volumes                          | `bool`         | No       | False           |
| `detached`     | Get only detached volumes                             | `bool`         | No       | False           |
| `types`        | Get only specific type volumes                        | `list(string)` | No       | None            |
| `region`       | Region for operation. Leave blank for session default | `string`       | No       | Session Default |
| `debug`        | Increase log verbosity                                | `bool`         | No       | False           |
| `silent`       | Decrease log verbosity                                | `bool`         | No       | False           |
| `session`      | Established session                                   | `object`       | No       | None            |

### Output

Returns a `list` of discovered volume IDs:

```python
['vol-1234567890abcdef0', 'vol-abcdef1234567890']
```

<div markdown="1" id="cli" style="display: block;">

## Examples

Fetch all volumes for specified instances:

```bash
aaws ec2 discover_volumes --instance_ids i-1234567890abcdef0 i-0987654321fedcba0
```

Fetch all detached and unencrypted volumes of type gp2 or gp3:

```bash
aaws ec2 discover_volumes --unencrypted --detached --types gp2 gp3
```

</div>

<div markdown="1" id="prog" style="display: none;">

## Examples

Fetch all volumes for specified instances:

```python
from avtomat_aws import ec2

response = ec2.discover_volumes(instance_ids=["i-1234567890abcdef0", "i-0987654321fedcba0"])
```

Fetch all detached and unencrypted volumes of type gp2 or gp3:

```python
from avtomat_aws import ec2

response = ec2.discover_volumes(unencrypted=True,
                                detached=True,
                                types=['gp2', 'gp3'])
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
