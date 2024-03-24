---
title: Discover Inactive Console Users
parent: iam
grand_parent: Actions
layout: default
permalink: /aws/actions/iam/discover_inactive_console_users
---

# Discover Inactive Console Users

Discover IAM users who haven't used the console over a certain period.<br/>

<p align="center">
   <a href="https://github.com/avtomat-hub/avtomat-aws/tree/main/avtomat_aws/iam/discover_inactive_console_users.py">Source code</a> •
   <a href="/aws/permissions/iam/discover_inactive_console_users">Permissions</a>
</p>

{: .note }
Users who have never used the console but have console access enabled are also returned.

{: .note }
This action only checks console activity. To check console and programmatic (access key) activity, use [Discover Inactive Users](/aws/actions/iam/discover_inactive_users) instead.

## Usage <button id="toggleButton" class="btn fs-3" onclick="toggleTables()">CLI</button>

### Input

| Parameter        | Description                                                  | Type     | Required | Default value   |
|------------------|--------------------------------------------------------------|----------|----------|-----------------|
| `threshold_days` | Get users with last console sign-in over this number of days | `int`    | Yes      | None            |
| `region`         | Region for operation                                         | `string` | No       | Session default |
| `debug`          | Log verbosity                                                | `bool`   | No       | False           |
| `session`        | Established session                                          | `object` | No       | None            |

### Output

Returns a `list of dictionaries` of discovered users:

```python
[{"UserName": "string"}]
```

<div markdown="1" id="cli" style="display: block;">

## Examples

Discover users who haven't used the console for more than 30 days:

```bash
aaws iam discover_inactive_console_users --threshold_days 30
```

</div>

<div markdown="1" id="prog" style="display: none;">

## Examples

Discover users who haven't used the console for more than 30 days:

```python
from avtomat_aws import iam

response = iam.discover_inactive_console_users(threshold_days=30)
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
