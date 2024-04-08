---
title: Discover Unused Roles
parent: iam
grand_parent: Actions
layout: default
permalink: /aws/actions/iam/discover_unused_roles
---

# Discover Unused Roles

Discover IAM roles not used over a certain amount of days.<br/>

<p align="center">
   <a href="https://github.com/avtomat-hub/avtomat-aws/tree/main/avtomat_aws/services/iam/discover_unused_roles.py">Source code</a> •
   <a href="/aws/permissions/iam/discover_unused_roles">Permissions</a>
</p>

## Usage <button id="toggleButton" class="btn fs-3" onclick="toggleTables()">CLI</button>

### Input

| Parameter        | Description                                          | Type     | Required | Default value   |
|------------------|------------------------------------------------------|----------|----------|-----------------|
| `threshold_days` | Get roles not used for more than this number of days | `int`    | Yes      | None            |
| `region`         | Region for operation                                 | `string` | No       | Session default |
| `debug`          | Increase log verbosity                               | `bool`   | No       | False           |
| `silent`         | Decrease log verbosity                               | `bool`   | No       | False           |
| `output`         | Output format <br/> `table`                          | `string` | No       | None            |
| `session`        | Established session                                  | `object` | No       | None            |

### Output

Returns a `list` of discovered roles:

```python
['role1', 'role2']
```

<div markdown="1" id="cli" style="display: block;">

## Examples

Discover roles not used for more than 100 days:

```bash
aaws iam discover_unused_roles --threshold_days 100
```

</div>

<div markdown="1" id="prog" style="display: none;">

## Examples

Discover roles not used for more than 100 days:

```python
from avtomat_aws import iam

response = iam.discover_unused_roles(threshold_days=100)
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