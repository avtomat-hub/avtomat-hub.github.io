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
   <a href="https://github.com/avtomat-hub/avtomat-aws/tree/main/avtomat_aws/ec2/discover_instances.py">Source code</a> •
   <a href="/aws/permissions/ec2/discover_instances">Permissions</a>
</p>

## Usage

### Input

| Parameter      | Description                                                     | Type           | Required | Default value                              |
|----------------|-----------------------------------------------------------------|----------------|----------|--------------------------------------------|
| `states`       | Instance states                                                 | `list(string)` | No       | ['running','stopped','pending','stopping'] |
| `tags`         | Tags (Key=Value)                                                | `list(string)` | No       | None                                       |
| `instance_ids` | Instance IDs to focus on                                        | `list(string)` | No       | None                                       |
| `public`       | Get only public instances                                       | `bool`         | No       | False                                      |
| `invert`       | Return instances that didn't conform to the supplied parameters | `bool`         | No       | None                                       |
| `os`           | Get only Windows or Linux instances                             | `string`       | No       | None                                       |
| `region`       | Region for operation                                            | `string`       | No       | Session default                            |
| `debug`        | Log verbosity                                                   | `bool`         | No       | None                                       |
| `session`      | Established session                                             | `object`       | No       | None                                       |

### Output

Returns a `list` of discovered instance IDs:

```python
['i-1234567890abcdef0', 'i-abcdef1234567890']
```

## Examples

Discover public windows instances in running or stopped state:

```bash
aaws ec2 discover_instances --states running stopped --public --os windows
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