---
title: Discover Objects
parent: s3
grand_parent: Actions
layout: default
permalink: /aws/actions/s3/discover_objects
---

# Discover Objects

Discover objects in an S3 bucket.

<p align="center">
   <a href="https://github.com/avtomat-hub/avtomat-aws/tree/main/avtomat_aws/s3/discover_objects.py">Source code</a> •
   <a href="/aws/permissions/s3/discover_objects">Permissions</a>
</p>

## Usage <button id="toggleButton" class="btn fs-3" onclick="toggleTables()">CLI</button>

### Input

| Parameter         | Description                                         | Type     | Required | Default value   |
|-------------------|-----------------------------------------------------|----------|----------|-----------------|
| `bucket`          | Name of the S3 bucket to discover objects in        | `string` | Yes      | None            |
| `prefix`          | Prefix to filter objects by                         | `string` | No       | None            |
| `modified_before` | Get objects last modified before date (YYYY/MM//DD) | `string` | No       | None            |
| `modified_after`  | Get objects last modified after date (YYYY/MM//DD)  | `string` | No       | None            |
| `name_only`       | Return only the object name, not the entire path    | `bool`   | No       | False           |
| `region`          | Region for operation                                | `string` | No       | Session default |
| `debug`           | Log verbosity                                       | `bool`   | No       | False           |
| `session`         | Established session                                 | `object` | No       | None            |

### Output

Returns a `list` of discovered objects:

```python
['object1', 'object2']
```

<div markdown="1" id="cli" style="display: block;">

## Examples

Discover objects in `example-bucket`:

```bash
aaws s3 discover_objects --bucket example-bucket
```

</div>

<div markdown="1" id="prog" style="display: none;">

## Examples

Discover objects in `example-bucket`:

```python
from avtomat_aws import s3

response = s3.discover_objects(bucket='example-bucket')
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
