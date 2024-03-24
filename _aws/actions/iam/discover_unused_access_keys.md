---
title: Discover Unused Access Keys
parent: iam
grand_parent: Actions
layout: default
permalink: /aws/actions/iam/discover_unused_access_keys
---

# Discover Unused Access Keys

Discover IAM access keys not used for over a number of days.<br/>

<p align="center">
   <a href="https://github.com/avtomat-hub/avtomat-aws/tree/main/avtomat_aws/iam/discover_unused_access_keys.py">Source code</a> •
   <a href="/aws/permissions/iam/discover_unused_access_keys">Permissions</a>
</p>

## Usage <button id="toggleButton" class="btn fs-3" onclick="toggleTables()">CLI</button>

### Input

| Parameter        | Description                                                | Type     | Required | Default value   |
|------------------|------------------------------------------------------------|----------|----------|-----------------|
| `threshold_days` | Get access keys not used for more than this number of days | `int`    | Yes      | None            |
| `region`         | Region for operation                                       | `string` | No       | Session default |
| `debug`          | Log verbosity                                              | `bool`   | No       | False           |
| `session`        | Established session                                        | `object` | No       | None            |

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

Discover access keys not used for more than 60 days:

```bash
aaws iam discover_unused_access_keys --threshold_days 60
```

</div>

<div markdown="1" id="prog" style="display: none;">

## Examples

Discover access keys not used for more than 60 days:

```python
from avtomat_aws import iam

response = iam.discover_unused_access_keys(threshold_days=60)
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