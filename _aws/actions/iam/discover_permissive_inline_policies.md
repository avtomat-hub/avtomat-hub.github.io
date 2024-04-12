---
title: Discover Permissive Inline Policies
parent: iam
grand_parent: Actions
layout: default
permalink: /aws/actions/iam/discover_permissive_inline_policies
---

# Discover Permissive Inline Policies

Discover overly permissive inline IAM policies.

<p align="center">
   <a href="https://github.com/avtomat-hub/avtomat-aws/tree/main/avtomat_aws/services/iam/discover_permissive_inline_policies.py">Source code</a> •
   <a href="/aws/permissions/iam/discover_permissive_inline_policies">Permissions</a>
</p>

{: .note}
This action has two modes of operation: <br>
**Normal** (default): permissive if `any action contains * and resource is *` <br>
**Strict**: permissive if `any action contains * or resource is *` <br>

{: .warning}
This action only evaluates inline policies.
Use [discover_permissive_policies](/aws/actions/iam/discover_permissive_policies) for managed policies.

## Usage <button id="toggleButton" class="btn fs-3" onclick="toggleTables()">CLI</button>

### Input

| Parameter | Description                                                                                                                                                        | Type           | Required | Default value   |
|-----------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------|----------|-----------------|
| `focus`   | Resource types to focus on <br> `user`, `group`, `role`                                                                                                            | `list(string)` | No       | All             |
| `strict`  | Determine mode of evaluation <br>If set, any permissive Action **or** Resource is a violation <br>Otherwise, any permissive Action **and** Resource is a violation | `bool`         | No       | False           |
| `region`  | Region for operation                                                                                                                                               | `string`       | No       | Session default |
| `debug`   | Increase log verbosity                                                                                                                                             | `bool`         | No       | False           |
| `silent`  | Decrease log verbosity                                                                                                                                             | `bool`         | No       | False           |
| `output`  | Output format <br/> `table`                                                                                                                                        | `string`       | No       | None            |
| `session` | Established session                                                                                                                                                | `object`       | No       | None            |

### Output

Returns a `list of dictionaries` containing discovered policies:

```python
[
    {
        "Type": "User",
        "Entity": "some-username",
        "Policy": "some-policy-name"
    }
]
```

<div markdown="1" id="cli" style="display: block;">

## Examples

Discover permissive inline policies for all resource types:

```bash
aaws iam discover_permissive_inline_policies
```

Strictly discover permissive policies and focus on users:

```bash
aaws iam discover_permissive_policies --strict --focus user
```

</div>

<div markdown="1" id="prog" style="display: none;">

## Examples

Discover permissive inline policies for all resource types:

```python
from avtomat_aws import iam

response = iam.discover_permissive_inline_policies()
```

Strictly discover permissive policies and focus on users:

```python
from avtomat_aws import iam

response = iam.discover_permissive_policies(strict=True, focus=["user"])
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