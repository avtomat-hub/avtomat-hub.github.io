---
title: Discover Unused Access Keys
parent: iam
grand_parent: Actions
layout: default
permalink: /aws/actions/iam/discover_unused_access_keys
---

# Discover Unused Access Keys

Discover IAM access keys not used for over a number of days.<br/>

<p align="center">
   <a href="https://github.com/avtomat-hub/avtomat-aws/tree/main/avtomat_aws/iam/discover_unused_access_keys.py">Source code</a> •
   <a href="/aws/permissions/iam/discover_unused_access_keys">Permissions</a>
</p>

## Usage

### Input

| Parameter        | Description                                                | Type     | Required | Default value   |
|------------------|------------------------------------------------------------|----------|----------|-----------------|
| `threshold_days` | Get access keys not used for more than this number of days | `int`    | Yes      | None            |
| `region`         | Region for operation                                       | `string` | No       | Session default |
| `debug`          | Log verbosity                                              | `bool`   | No       | False           |
| `session`        | Established session                                        | `object` | No       | None            |

### Output

Returns a `list of dictionaries` containing discovered access keys:

```python
[
    {
        "UserName": "string",
        "AccessKeyId": "string"
    }
]
```

## Examples

Discover access keys not used for more than 60 days:

```bash
aaws iam discover_unused_access_keys --threshold_days 60
```

Programmatic usage:

```python
from avtomat_aws import iam

response = iam.discover_unused_access_keys(threshold_days=60)
```