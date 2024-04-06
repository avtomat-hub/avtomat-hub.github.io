---
title: Discover No MFA Users
parent: iam
grand_parent: Actions
layout: default
permalink: /aws/actions/iam/discover_no_mfa_users
---

# Discover No MFA Users

Discover IAM users without MFA enabled.<br/>

<p align="center">
   <a href="https://github.com/avtomat-hub/avtomat-aws/tree/main/avtomat_aws/services/iam/discover_no_mfa_users.py">Source code</a> •
   <a href="/aws/permissions/iam/discover_no_mfa_users">Permissions</a>
</p>

## Usage <button id="toggleButton" class="btn fs-3" onclick="toggleTables()">CLI</button>

### Input

| Parameter | Description            | Type     | Required | Default value   |
|-----------|------------------------|----------|----------|-----------------|
| `region`  | Region for operation   | `string` | No       | Session default |
| `debug`   | Increase log verbosity | `bool`   | No       | False           |
| `silent`  | Decrease log verbosity | `bool`   | No       | False           |
| `session` | Established session    | `object` | No       | None            |

### Output

Returns a `list of dictionaries` of discovered users:

```python
[{"UserName": "string"}]
```

<div markdown="1" id="cli" style="display: block;">

## Examples

Discover users without MFA enabled:

```bash
aaws iam discover_no_mfa_users
```

</div>

<div markdown="1" id="prog" style="display: none;">

## Examples

Discover users without MFA enabled:

```python
from avtomat_aws import iam

response = iam.discover_no_mfa_users()
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