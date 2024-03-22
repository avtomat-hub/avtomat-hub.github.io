---
title: Create Objects
parent: s3
grand_parent: Actions
layout: default
permalink: /aws/actions/s3/create_objects
---

# Create Objects

Create objects in an S3 bucket.

{: .note}
The body of an object can be a file path or inline data.

<p align="center">
   <a href="https://github.com/avtomat-hub/avtomat-aws/tree/main/avtomat_aws/s3/create_objects.py">Source code</a> •
   <a href="/aws/permissions/s3/create_objects">Permissions</a>
</p>

## Usage <button id="cliButton" class="btn fs-3" onclick="toggleTables()" style="display: inline;">CLI</button> <button id="progButton" class="btn fs-3" onclick="toggleTables()" style="display: none;">Programmatic</button>

<div markdown="1" id="cliTable" style="display: block;">

### Input

| Parameter | Description                                                       | Type     | Required | Default value   |
|-----------|-------------------------------------------------------------------|----------|----------|-----------------|
| `bucket`  | Name of the S3 bucket to create objects in                        | `string` | Yes      | None            |
| `object`  | Object to create. Repeat for multiple objects. Format: `key body` | `string` | Yes      | None            |
| `prefix`  | Prefix to filter objects by                                       | `string` | No       | None            |
| `region`  | Region for operation                                              | `string` | No       | Session default |
| `debug`   | Log verbosity                                                     | `bool`   | No       | False           |
| `session` | Established session                                               | `object` | No       | None            |

### Output

Returns a `list` of objects that failed the creation:

```python
['object1', 'object2']
```

## Examples

Create `examples/object1` and `examples/object2` in `example-bucket`:

```bash
aaws s3 create_objects --bucket example-bucket --object examples/object1 /path/to/file --object examples/object2 "inline data"
```

</div>

<div markdown="1" id="progTable" style="display: none;">

### Input

| Parameter | Description                                                      | Type         | Required | Default value   |
|-----------|------------------------------------------------------------------|--------------|----------|-----------------|
| `bucket`  | Name of the S3 bucket to create objects in                       | `string`     | Yes      | None            |
| `objects` | Objects to create. Format: `[{"Key":"example", "Body": "data"}]` | `list(dict)` | Yes      | None            |
| `prefix`  | Prefix to filter objects by                                      | `string`     | No       | None            |
| `region`  | Region for operation                                             | `string`     | No       | Session default |
| `debug`   | Log verbosity                                                    | `bool`       | No       | False           |
| `session` | Established session                                              | `object`     | No       | None            |

### Output

Returns a `list` of objects that failed the creation:

```python
['object1', 'object2']
```

## Examples

Create `examples/object1` and `examples/object2` in `example-bucket`:

```python
from avtomat_aws import s3

response = s3.create_objects(bucket='example-bucket',
                             objects=[{"Key": "examples/object1", "Body": "/path/to/file"},
                                      {"Key": "examples/object2", "Body": "inline data"}])
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