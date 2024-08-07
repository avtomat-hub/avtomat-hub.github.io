---
title: Who Am I
parent: sts
grand_parent: Actions
layout: default
permalink: /aws/actions/sts/whoami
---

# Who Am I

Quickly figure out your current credentials.<br/>

<p align="center">
   <a href="https://github.com/avtomat-hub/avtomat-aws/tree/main/avtomat_aws/services/sts/whoami.py">Source code</a> •
   <a href="/aws/permissions/sts/whoami">Permissions</a>
</p>

## Usage <button id="toggleButton" class="btn fs-3" onclick="toggleTables()">CLI</button>

### Input

| Parameter | Description                 | Type     | Required | Default value |
|-----------|-----------------------------|----------|----------|---------------|
| `debug`   | Increase log verbosity      | `bool`   | No       | False         |
| `silent`  | Decrease log verbosity      | `bool`   | No       | False         |
| `output`  | Output format <br/> `table` | `string` | No       | None          |
| `session` | Established session         | `object` | No       | None          |

### Output

Returns a `dictionary` indicating current entity.

```python
{'Arn': 'arn:aws:iam::123456789012:user/FooBar', 'Region': 'us-east-1'}
```

<div markdown="1" id="cli" style="display: block;">

## Examples

Find out who you are:

```bash
aaws sts whoami
```

</div>

<div markdown="1" id="prog" style="display: none;">

## Examples

Find out who you are:

```python
from avtomat_aws import sts

response = sts.whoami()
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
