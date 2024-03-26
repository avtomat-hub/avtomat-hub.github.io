---
title: Discover Old Access Keys
parent: iam
grand_parent: Actions
layout: default
permalink: /aws/actions/iam/discover_old_access_keys
---

# Discover Old Access Keys

Discover IAM access keys above a certain age.<br/>

<p align="center">
   <a href="https://github.com/avtomat-hub/avtomat-aws/tree/main/avtomat_aws/iam/discover_old_access_keys.py">Source code</a> •
   <a href="/aws/permissions/iam/discover_old_access_keys">Permissions</a>
</p>

## Usage <button id="toggleButton" class="btn fs-3" onclick="toggleTables()">CLI</button>

### Input

| Parameter        | Description                                    | Type     | Required | Default value   |
|------------------|------------------------------------------------|----------|----------|-----------------|
| `threshold_days` | Get access keys older than this number of days | `int`    | Yes      | None            |
| `region`         | Region for operation                           | `string` | No       | Session default |
| `debug`          | Increase log verbosity                         | `bool`   | No       | False           |
| `silent`         | Decrease log verbosity                         | `bool`   | No       | False           |
| `session`        | Established session                            | `object` | No       | None            |

### Output

Returns a `list of dictionaries` containing discovered access keys:

```python
[
    {
        "UserName": "string",
        "AccessKeyId": "string"
    }
]
```

<div markdown="1" id="cli" style="display: block;">

## Examples

Discover access keys older than 90 days:

```bash
aaws iam discover_old_access_keys --threshold_days 90
```

</div>

<div markdown="1" id="prog" style="display: none;">

## Examples

Discover access keys older than 90 days:

```python
from avtomat_aws import iam

response = iam.discover_old_access_keys(threshold_days=90)
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
