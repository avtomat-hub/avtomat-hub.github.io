---
title: Discover Active Regions
parent: ec2
grand_parent: Actions
layout: default
permalink: /aws/actions/ec2/discover_active_regions
---

# Discover Active Regions

Discover all active AWS regions for an account. Useful for dynamically targeting operations
across multiple regions.

<p align="center">
   <a href="https://github.com/avtomat-hub/avtomat-aws/tree/main/avtomat_aws/ec2/discover_active_regions.py">Source code</a> •
   <a href="/aws/permissions/ec2/discover_active_regions">Permissions</a>
</p>

## Usage <button id="toggleButton" class="btn fs-3" onclick="toggleTables()">CLI</button>

### Input

| Parameter | Description            | Type     | Required | Default value |
|-----------|------------------------|----------|----------|---------------|
| `debug`   | Increase log verbosity | `bool`   | No       | False         |
| `silent`  | Decrease log verbosity | `bool`   | No       | False         |
| `session` | Established session    | `object` | No       | None          |

### Output

Returns a `list` of discovered regions:

```python
['us-east-1', 'us-west-2', 'eu-west-1']
```

<div markdown="1" id="cli" style="display: block;">

## Examples

Discover active regions:

```bash
aaws ec2 discover_active_regions
```

</div>

<div markdown="1" id="prog" style="display: none;">

## Examples

Discover active regions:

```python
from avtomat_aws import ec2

response = ec2.discover_active_regions()
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
