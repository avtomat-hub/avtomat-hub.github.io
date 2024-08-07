---
title: Discover Instances
parent: ec2
grand_parent: Actions
layout: default
permalink: /aws/actions/ec2/discover_instances
---

# Discover Instances

Discover AWS instances based on specified criteria.

<p align="center">
   <a href="https://github.com/avtomat-hub/avtomat-aws/tree/main/avtomat_aws/services/ec2/discover_instances.py">Source code</a> •
   <a href="/aws/permissions/ec2/discover_instances">Permissions</a>
</p>

## Usage <button id="toggleButton" class="btn fs-3" onclick="toggleTables()">CLI</button>

### Input

| Parameter      | Description                                                                                                | Type           | Required | Default value                            |
|----------------|------------------------------------------------------------------------------------------------------------|----------------|----------|------------------------------------------|
| `instance_ids` | Instance IDs to focus on                                                                                   | `list(string)` | No       | All instances                            |
| `states`       | Filter instances by states <br> `pending`, `running`, `shutting-down`, `terminated`, `stopping`, `stopped` | `list(string)` | No       | `running`,`stopped`,`pending`,`stopping` |
| `tags`         | Filter instances by tags <br> `Key=Value` or `Key`                                                         | `list(string)` | No       | None                                     |
| `public`       | Filter instances by public ip                                                                              | `bool`         | No       | False                                    |
| `os`           | Filter instances by Windows or Linux operating system <br/> `linux`, `windows`                             | `string`       | No       | None                                     |
| `invert`       | Return instances that didn't conform to the supplied parameters                                            | `bool`         | No       | None                                     |
| `region`       | Region for operation                                                                                       | `string`       | No       | Session default                          |
| `debug`        | Increase log verbosity                                                                                     | `bool`         | No       | False                                    |
| `silent`       | Decrease log verbosity                                                                                     | `bool`         | No       | False                                    |
| `output`       | Output format <br/> `table`                                                                                | `string`       | No       | None                                     |
| `session`      | Established session                                                                                        | `object`       | No       | None                                     |

### Output

Returns a `list` of discovered instance IDs:

```python
['i-1234567890abcdef0', 'i-abcdef1234567890']
```

<div markdown="1" id="cli" style="display: block;">

## Examples

Discover public windows instances in running or stopped state:

```bash
aaws ec2 discover_instances --states running stopped --public --os windows
```

Discover if specific instances are missing specific tags:

```bash
aaws ec2 discover_instances --tags Owner Name=example --instance_ids i-1234567890abcdef0 i-abcdef1234567890 --invert
```

</div>

<div markdown="1" id="prog" style="display: none;">

## Examples

Discover public windows instances in running or stopped state:

```python
from avtomat_aws import ec2

response = ec2.discover_instances(states=["running", "stopped"],
                                  public=True,
                                  os="windows")
```

Discover if specific instances are missing specific tags:

```python
from avtomat_aws import ec2

response = ec2.discover_instances(tags=["Owner", "Name=example"],
                                  instance_ids=["i-1234567890abcdef0", "i-abcdef1234567890"],
                                  invert=True)
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
