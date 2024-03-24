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

## Usage <button id="toggleButton" class="btn fs-3" onclick="toggleTables()">CLI</button>

<div markdown="1" id="cli" style="display: block;">

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

Disable access keys for users:

```bash
aaws iam modify_access_keys --key AKIA12ZAWVSH44WXASKY acme --key AKEA112WWDAH44CXZSRE foo --disable
```

</div>

<div markdown="1" id="prog" style="display: none;">

### Input

| Parameter | Description           | Type         | Required         | Default value   |
|-----------|-----------------------|--------------|------------------|-----------------|
| `keys`    | Access keys to modify | `list(dict)` | Yes              | None            |
| `enable`  | Enable access keys    | `bool`       | If not `disable` | False           |
| `disable` | Disable access keys   | `bool`       | If not `enable`  | False           |
| `region`  | Region for operation  | `string`     | No               | Session default |
| `debug`   | Log verbosity         | `bool`       | No               | False           |
| `session` | Established session   | `object`     | No               | None            |

### Output

Returns a `list` of access keys that failed the update:

```python
['AKIA12ZAWVSH44WXASKY']
```

## Examples

Disable access keys for users:

```python
from avtomat_aws import iam

response = iam.modify_access_keys(keys=[{"AccessKeyId": "AKIA12ZAWVSH44WXASKY", "UserName": "acme"},
                                        {"AccessKeyId": "AKEA112WWDAH44CXZSRE", "UserName": "foo"}],
                                  disable=True)
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