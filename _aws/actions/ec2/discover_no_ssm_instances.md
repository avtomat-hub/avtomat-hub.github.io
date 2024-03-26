---
title: Discover No SSM Instances
parent: ec2
grand_parent: Actions
layout: default
permalink: /aws/actions/ec2/discover_no_ssm_instances
---

# Discover No SSM Instances

Discover EC2 instances without SSM enabled.

<p align="center">
   <a href="https://github.com/avtomat-hub/avtomat-aws/tree/main/avtomat_aws/ec2/discover_no_ssm_instances.py">Source code</a> •
   <a href="/aws/permissions/ec2/discover_no_ssm_instances">Permissions</a>
</p>

## Usage <button id="toggleButton" class="btn fs-3" onclick="toggleTables()">CLI</button>

### Input

| Parameter      | Description              | Type           | Required | Default value   |
|----------------|--------------------------|----------------|----------|-----------------|
| `instance_ids` | Instance IDs to focus on | `list(string)` | No       | None            |
| `region`       | Region for operation     | `string`       | No       | Session default |
| `debug`        | Increase log verbosity   | `bool`         | No       | False           |
| `silent`       | Decrease log verbosity   | `bool`         | No       | False           |
| `session`      | Established session      | `object`       | No       | None            |

### Output

Returns a `list` of discovered instance IDs:

```python
['i-1234567890abcdef0', 'i-abcdef1234567890']
```

<div markdown="1" id="cli" style="display: block;">

## Examples

Discover instances without SSM enabled in eu-west-2:

```bash
aaws ec2 discover_no_ssm_instances --region eu-west-2
```

Discover if specific instances don't have SSM enabled:

```bash
aaws ec2 discover_no_ssm_instances --instance_ids i-1234567890abcdef0 i-abcdef1234567890
```

</div>

<div markdown="1" id="prog" style="display: none;">

## Examples

Discover instances without SSM enabled in eu-west-2:

```python
from avtomat_aws import ec2

response = ec2.discover_no_ssm_instances(region="eu-west-2")
```

Discover if specific instances don't have SSM enabled:

```python
from avtomat_aws import ec2

response = ec2.discover_no_ssm_instances(instance_ids=['i-1234567890abcdef0', 'i-abcdef1234567890'])
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
