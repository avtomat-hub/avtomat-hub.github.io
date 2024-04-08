---
title: Discover Unused Security Groups
parent: ec2
grand_parent: Actions
layout: default
permalink: /aws/actions/ec2/discover_unused_security_groups
---

# Discover Unused Security Groups

Discover unused security groups.<br/>
Resources checked:

- ENI
- EC2
- RDS
- ELB
- ELBv2
- Lambda
- Redshift
- ElastiCache
- EMR
- ECS
- Neptune
- OpenSearch
- MSK

<p align="center">
   <a href="https://github.com/avtomat-hub/avtomat-aws/tree/main/avtomat_aws/services/ec2/discover_unused_security_groups.py">Source code</a> •
   <a href="/aws/permissions/ec2/discover_unused_security_groups">Permissions</a>
</p>

## Usage <button id="toggleButton" class="btn fs-3" onclick="toggleTables()">CLI</button>

### Input

| Parameter | Description                 | Type     | Required | Default value   |
|-----------|-----------------------------|----------|----------|-----------------|
| `region`  | Region for operation        | `string` | No       | Session default |
| `debug`   | Increase log verbosity      | `bool`   | No       | False           |
| `silent`  | Decrease log verbosity      | `bool`   | No       | False           |
| `output`  | Output format <br/> `table` | `string` | No       | None            |
| `session` | Established session         | `object` | No       | None            |

### Output

Returns a `list` of discovered security group IDs:

```python
['sg-1234567890abcdef0', 'sg-abcdef1234567890']
```

<div markdown="1" id="cli" style="display: block;">

## Examples

Discover unused security groups:

```bash
aaws ec2 discover_unused_security_groups --region us-east-1
```

</div>

<div markdown="1" id="prog" style="display: none;">

## Examples

Discover unused security groups:

```python
from avtomat_aws import ec2

response = ec2.discover_unused_security_groups(region='us-east-1')
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
