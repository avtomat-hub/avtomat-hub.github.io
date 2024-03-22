---
title: Modify Access Keys
parent: iam
grand_parent: Actions
layout: default
permalink: /aws/actions/iam/modify_access_keys
---

# Modify Access Keys

Enable or disable IAM access keys.<br/>

<p align="center">
   <a href="https://github.com/avtomat-hub/avtomat-aws/tree/main/avtomat_aws/iam/modify_access_keys.py">Source code</a> •
   <a href="/aws/permissions/iam/modify_access_keys">Permissions</a>
</p>

## Usage <button id="cliButton" class="btn fs-3" onclick="toggleTables()" style="display: inline;">CLI</button> <button id="progButton" class="btn fs-3" onclick="toggleTables()" style="display: none;">Programmatic</button>

<div markdown="1" id="cliTable" style="display: block;">

### Input

| Parameter | Description                                                                          | Type     | Required         | Default value   |
|-----------|--------------------------------------------------------------------------------------|----------|------------------|-----------------|
| `key`     | Access key with Id and Username. Repeatable for multiple keys. Format: `id username` | `string` | Yes              | None            |
| `enable`  | Enable access keys                                                                   | `bool`   | If not `disable` | False           |
| `disable` | Disable access keys                                                                  | `bool`   | If not `enable`  | False           |
| `region`  | Region for operation                                                                 | `string` | No               | Session default |
| `debug`   | Log verbosity                                                                        | `bool`   | No               | False           |
| `session` | Established session                                                                  | `object` | No               | None            |

### Output

Returns a `list` of access keys that failed the update:

```python
['AKIA12ZAWVSH44WXASKY']
```

## Examples

Disable an access key for user:

```bash
aaws iam modify_access_keys --key AKIA12ZAWVSH44WXASKY acme-user --disable
```

</div>

<div markdown="1" id="progTable" style="display: none;">

### Input

| Parameter | Description           | Type     | Required         | Default value   |
|-----------|-----------------------|----------|------------------|-----------------|
| `keys`    | Access keys to modify | `dict`   | Yes              | None            |
| `enable`  | Enable access keys    | `bool`   | If not `disable` | False           |
| `disable` | Disable access keys   | `bool`   | If not `enable`  | False           |
| `region`  | Region for operation  | `string` | No               | Session default |
| `debug`   | Log verbosity         | `bool`   | No               | False           |
| `session` | Established session   | `object` | No               | None            |

### Output

Returns a `list` of access keys that failed the update:

```python
['AKIA12ZAWVSH44WXASKY']
```

### Examples

```python
from avtomat_aws import iam
response = iam.modify_access_keys(keys=[{"AccessKeyId": "AKIA12ZAWVSH44WXASKY", "UserName": "acme-user"}],
                                 disable=True)
```

</div>

<script>
  function toggleTables() {
    var cliTable = document.getElementById("cliTable");
    var progTable = document.getElementById("progTable");
    var cliButton = document.getElementById("cliButton");
    var progButton = document.getElementById("progButton");
    if (cliTable.style.display === "none") {
      cliTable.style.display = "block";
      progTable.style.display = "none";
    } else {
      cliTable.style.display = "none";
      progTable.style.display = "block";
    }
    if (cliButton.style.display === "none") {
      cliButton.style.display = "inline";
      progButton.style.display = "none";
    } else {
      cliButton.style.display = "none";
      progButton.style.display = "inline";
    } 
  }
</script>