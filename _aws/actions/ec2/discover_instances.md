---
title: Discover Instances
parent: ec2
grand_parent: Actions
layout: default
permalink: /aws/actions/ec2/discover_instances
---

# Discover Instances

Discover AWS instances based on specified criteria such as tags or simply all instances.

<p align="center">
   <a href="https://github.com/avtomat-hub/avtomat-aws/tree/main/avtomat_aws/ec2/discover_instances.py">Source code</a> •
   <a href="/aws/permissions/ec2/discover_instances">Permissions</a>
</p>

## Usage

### Input

Parameters are used for both programmatic input and command-line arguments.<br/>

- The `Applicable` column indicates whether the parameter is accepted in Programmatic (P), Command-Line (C), or Both (
  B).<br/>
- For Command-Line execution, type `list` parameters are passed as space-separated strings.

| Parameter      | Description                                                                       | Type           | Applicable | Required | Default value                              |
|----------------|-----------------------------------------------------------------------------------|----------------|------------|----------|--------------------------------------------|
| `states`       | Instance states                                                                   | `list(string)` | B          | No       | ['running','stopped','pending','stopping'] |
| `tags`         | Tags (Key=Value)                                                                  | `list(string)` | B          | No       | None                                       |
| `instance_ids` | Instance IDs to focus on                                                          | `list(string)` | B          | No       | None                                       |
| `public`       | Get only public instances                                                         | `bool`         | B          | No       | False                                      |
| `invert`       | If `instance_ids` is supplied, return the ones that didn't conform to the filters | `bool`         | B          | No       | None                                       |
| `region`       | Region for operation                                                              | `string`       | B          | No       | Session default                            |
| `debug`        | Log verbosity                                                                     | `bool`         | B          | No       | None                                       |
| `session`      | Established session                                                               | `object`       | P          | No       | None                                       |

### Output

Returns a `list` of discovered instance IDs:

```python
['i-1234567890abcdef0', 'i-abcdef1234567890']
```

## Examples

Discover public instances in running or stopped state:

```bash
aaws ec2 discover_instances --states running stopped --public
```

Discover if specific instances are missing specific tags:

```bash
aaws ec2 discover_instances --tags Owner Name=example --instance_ids i-1234567890abcdef0 i-abcdef1234567890 --invert
```

Programmatic usage:

```python
from avtomat_aws import ec2

response = ec2.discover_instances(tags=["Owner", "Name=example"],
                                  instance_ids=["i-1234567890abcdef0", "i-abcdef1234567890"],
                                  invert=True)
```