---
title: Get Date
parent: general
grand_parent: Actions
layout: default
permalink: /aws/actions/general/get_date
---

# Get Date

Return a date in the requested format.<br/>

<p align="center">
   <a href="https://github.com/avtomat-hub/avtomat-aws/tree/main/avtomat_aws/services/general/get_date.py">Source code</a>
</p>

## Usage <button id="toggleButton" class="btn fs-3" onclick="toggleTables()">CLI</button>

### Input

| Parameter | Description                                                                | Type     | Required | Default Value |
|-----------|----------------------------------------------------------------------------|----------|----------|---------------|
| `after`   | Return a date number of days in the future                                 | `int`    | No       | None          |
| `before`  | Return a date number of days in the past                                   | `int`    | No       | None          |
| `format`  | Specify the format of the returned date. <br/> `string`, `iso`, `datetime` | `string` | No       | `datetime`    |
| `debug`   | Increase log verbosity                                                     | `bool`   | No       | False         |
| `silent`  | Decrease log verbosity                                                     | `bool`   | No       | False         |
| `output`  | Output format <br/> `table`                                                | `string` | No       | None          |

### Output

Returns the generated date in the requested format:

```python
'2021/01/01' | '2021-01-01T00:00:00Z' | '2021-01-01 00:00:00'
```

<div markdown="1" id="cli" style="display: block;">

## Examples

Get the date 10 days in the future in `iso` format:

```bash
aaws general get_date --after 10 --format iso
```

Get the date 15 days in the past in `string` format:

```bash
aaws general get_date --before 15 --format string
```

</div>

<div markdown="1" id="prog" style="display: none;">

## Examples

Get the date 10 days in the future in `iso` format:

```python
from avtomat_aws import general

response = general.get_date(after=10, format='iso')
```

Get the date 15 days in the past in `string` format:

```python
from avtomat_aws import general

response = general.get_date(before=15, format='string')
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
