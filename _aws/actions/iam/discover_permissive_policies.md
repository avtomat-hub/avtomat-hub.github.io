---
title: Discover Permissive Policies
parent: iam
grand_parent: Actions
layout: default
permalink: /aws/actions/iam/discover_permissive_policies
---

# Discover Permissive Policies

Discover overly permissive IAM policies.

<p align="center">
   <a href="https://github.com/avtomat-hub/avtomat-aws/tree/main/avtomat_aws/services/iam/discover_permissive_policies.py">Source code</a> •
   <a href="/aws/permissions/iam/discover_permissive_policies">Permissions</a>
</p>

{: .note}
This action has two modes of operation: <br>
**Normal** (default): permissive if `any action contains * and resource is *` <br>
**Strict**: permissive if `any action contains * or resource is *` <br>

{: .warning}
This action does not evaluate inline policies. Use [discover_permissive_inline_policies](/aws/actions/iam/discover_permissive_inline_policies) for that.

## Usage <button id="toggleButton" class="btn fs-3" onclick="toggleTables()">CLI</button>

### Input

| Parameter | Description                                                                                                                                                           | Type     | Required | Default value   |
|-----------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------|----------|-----------------|
| `strict`  | Determine mode of evaluation. <br>If set, any permissive Action **or** Resource is a violation. <br>Otherwise, any permissive Action **and** Resource is a violation. | `bool`   | No       | False           |
| `region`  | Region for operation                                                                                                                                                  | `string` | No       | Session default |
| `debug`   | Increase log verbosity                                                                                                                                                | `bool`   | No       | False           |
| `silent`  | Decrease log verbosity                                                                                                                                                | `bool`   | No       | False           |
| `output`  | Output format <br/> `table`                                                                                                                                           | `string` | No       | None            |
| `session` | Established session                                                                                                                                                   | `object` | No       | None            |

### Output

Returns a `list` of discovered policy names:

```python
['PolicyName1', 'PolicyName2']
```

<div markdown="1" id="cli" style="display: block;">

## Examples

Discover permissive policies:

```bash
aaws iam discover_permissive_policies
```

Strictly discover permissive policies:

```bash
aaws iam discover_permissive_policies --strict
```

</div>

<div markdown="1" id="prog" style="display: none;">

## Examples

Discover permissive policies:

```python
from avtomat_aws import iam

response = iam.discover_permissive_policies()
```

Strictly discover permissive policies:

```python
from avtomat_aws import iam

response = iam.discover_permissive_policies(strict=True)
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