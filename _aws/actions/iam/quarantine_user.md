---
title: Quarantine User
parent: iam
grand_parent: Actions
layout: default
permalink: /aws/actions/iam/quarantine_user
---

# Quarantine User

Disable console and programmatic access and apply `AWSCompromisedKeyQuarantineV2` policy to an IAM user.<br/>

<p align="center">
   <a href="https://github.com/avtomat-hub/avtomat-aws/tree/main/avtomat_aws/services/iam/quarantine_user.py">Source code</a> •
   <a href="/aws/permissions/iam/quarantine_user">Permissions</a>
</p>

{: .danger }
Current password of the user will be deleted and will not be recoverable.<br/>

{: .note}
Access keys are deactivated but not deleted.

## Usage <button id="toggleButton" class="btn fs-3" onclick="toggleTables()">CLI</button>

### Input

| Parameter | Description                 | Type     | Required | Default value   |
|-----------|-----------------------------|----------|----------|-----------------|
| `user`    | User to quarantine          | `string` | Yes      | None            |
| `region`  | Region for operation        | `string` | No       | Session default |
| `debug`   | Increase log verbosity      | `bool`   | No       | False           |
| `silent`  | Decrease log verbosity      | `bool`   | No       | False           |
| `output`  | Output format <br/> `table` | `string` | No       | None            |
| `session` | Established session         | `object` | No       | None            |

### Output

This function has no output.

<div markdown="1" id="cli" style="display: block;">

## Examples

Quarantine a user:

```bash
aaws iam quarantine_user --user acme-user
```

</div>

<div markdown="1" id="prog" style="display: none;">

## Examples

Quarantine a user:

```python
from avtomat_aws import iam

response = iam.quarantine_user(user='acme-user')
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
