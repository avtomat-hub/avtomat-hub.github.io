---
title: Modify Users Console Access
parent: iam
grand_parent: Actions
layout: default
permalink: /aws/actions/iam/modify_users_console_access
---

# Modify Users Console Access

Enable or disable AWS Management Console access for IAM users.<br/>

{: .note }
When enabling console access the passwords provided are temporary. Users will be prompted to change them upon first
login.<br/>
Users will have the `IAMUserChangePassword` policy attached to allow the password change.

<p align="center">
   <a href="https://github.com/avtomat-hub/avtomat-aws/tree/main/avtomat_aws/iam/modify_users_console_access.py">Source code</a> •
   <a href="/aws/permissions/iam/modify_users_console_access">Permissions</a>
</p>

## Usage <button id="cliButton" class="btn fs-3" onclick="toggleTables()" style="display: inline;">CLI</button> <button id="progButton" class="btn fs-3" onclick="toggleTables()" style="display: none;">Programmatic</button>

<div markdown="1" id="cliTable" style="display: block;">

### Input

| Parameter  | Description                                                                                          | Type     | Required         | Default value   |
|------------|------------------------------------------------------------------------------------------------------|----------|------------------|-----------------|
| `user`     | User with Username and Password(optional). Repeatable for multiple keys. Format: `username password` | `string` | Yes              | None            |
| `enable`   | Enable console access                                                                                | `bool`   | If not `disable` | False           |
| `disable`  | Disable console access                                                                               | `bool`   | If not `enable`  | False           |
| `region`   | Region for operation                                                                                 | `string` | No               | Session default |
| `debug`    | Log verbosity                                                                                        | `bool`   | No               | False           |
| `session`  | Established session                                                                                  | `object` | No               | None            |

### Output

Returns a `list` of users that failed the update:

```python
['acme', 'foo']
```

## Examples

Enable console access for users:

```bash
aaws iam modify_users_console_access --user acme P@ssw0rd123 --user foo P@ssw0rd112233 --enable
```

Disable console access for users:

```bash
aaws iam modify_users_console_access --user acme --user foo --disable
```

</div>

<div markdown="1" id="progTable" style="display: none;">

### Input

| Parameter | Description            | Type         | Required         | Default value   |
|-----------|------------------------|--------------|------------------|-----------------|
| `users`   | Users to modify        | `list(dict)` | Yes              | None            |
| `enable`  | Enable console access  | `bool`       | If not `disable` | False           |
| `disable` | Disable console access | `bool`       | If not `enable`  | False           |
| `region`  | Region for operation   | `string`     | No               | Session default |
| `debug`   | Log verbosity          | `bool`       | No               | False           |
| `session` | Established session    | `object`     | No               | None            |

### Output

Returns a `list` of users that failed the update:

```python
['acme', 'foo']
```

## Examples

Enable console access for users:

```python
from avtomat_aws import iam

response = iam.modify_console_access(users=[{"UserName": "acme", "Password": "P@ssw0rd123"},
                                            {"UserName": "foo", "Password": "P@ssw0rd112233"}],
                                     enable=True)
```

Disable console access for users:

```python
from avtomat_aws import iam

response = iam.modify_console_access(users=[{"UserName": "acme"},
                                            {"UserName": "foo"}],
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