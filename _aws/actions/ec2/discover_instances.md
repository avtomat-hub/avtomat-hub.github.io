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

| Parameter  | Description                       | Type           | Applicable | Required           | Default value                              |
|------------|-----------------------------------|----------------|------------|--------------------|--------------------------------------------|
| `mode`     | Discovery mode (all, tag)         | `string`       | B          | Yes                | all                                        |
| `states`   | Instance states                   | `list(string)` | B          | No                 | ['running','stopped','pending','stopping'] |
| `tags`     | Tags (Key=Value)                  | `list(string)` | B          | If `mode` is `tag` | None                                       |
| `public`   | Get only public instances         | `bool`         | B          | No                 | False                                      |
| `region`   | Region for operation              | `string`       | B          | No                 | Session default                            |
| `debug`    | Log verbosity                     | `bool`         | B          | No                 | None                                       |
| `session`  | Established session               | `object`       | P          | No                 | None                                       |

### Output

Returns a `list` of discovered instance IDs:

```python
['i-1234567890abcdef0', 'i-abcdef1234567890']
```

## Examples

Discover tagged instances:

```bash
aaws ec2 discover_instances --mode tag --tags Name=example Owner=acme
```

Discover public instances in running or stopped state:

```bash
aaws ec2 discover_instances --mode all --states running stopped --public
```

Programmatic usage:

```python
from avtomat_aws import ec2

response = ec2.discover_instances(mode='all',
                                  public=True,
                                  states=['running', 'stopped'])
```