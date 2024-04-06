---
title: Delete Objects
parent: s3
grand_parent: Actions
layout: default
permalink: /aws/actions/s3/delete_objects
---

# Delete Objects

Delete objects from an S3 bucket.

<p align="center">
   <a href="https://github.com/avtomat-hub/avtomat-aws/tree/main/avtomat_aws/services/s3/delete_objects.py">Source code</a> •
   <a href="/aws/permissions/s3/delete_objects">Permissions</a>
</p>

## Usage <button id="toggleButton" class="btn fs-3" onclick="toggleTables()">CLI</button>

### Input

| Parameter | Description                                  | Type           | Required | Default value   |
|-----------|----------------------------------------------|----------------|----------|-----------------|
| `bucket`  | Name of the S3 bucket to delete objects from | `string`       | Yes      | None            |
| `objects` | Objects to delete                            | `list(string)` | Yes      | None            |
| `prefix`  | Prefix to filter objects by                  | `string`       | No       | None            |
| `region`  | Region for operation                         | `string`       | No       | Session default |
| `debug`   | Increase log verbosity                       | `bool`         | No       | False           |
| `silent`  | Decrease log verbosity                       | `bool`         | No       | False           |
| `session` | Established session                          | `object`       | No       | None            |

### Output

Returns a `list` of objects that failed the deletion:

```python
['object1', 'object2']
```

<div markdown="1" id="cli" style="display: block;">

## Examples

Delete `examples/object1` and `examples/object2` from `example-bucket`:

```bash
aaws s3 delete_objects --bucket example-bucket --objects examples/object1 examples/object2
```

Delete `object1` and `object2` using prefix `examples` from `example-bucket`:

```bash
aaws s3 delete_objects --bucket example-bucket --prefix examples --objects object1 object2
```

</div>

<div markdown="1" id="prog" style="display: none;">

## Examples

Delete `examples/object1` and `examples/object2` from `example-bucket`:

```python
from avtomat_aws import s3

response = s3.delete_objects(bucket='example-bucket',
                             objects=['examples/object1', 'examples/object2'])
```

Delete `object1` and `object2` using prefix `examples` from `example-bucket`:

```python
from avtomat_aws import s3

response = s3.discover_objects(bucket='example-bucket',
                               prefix='examples',
                               objects=['object1', 'object2'])
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