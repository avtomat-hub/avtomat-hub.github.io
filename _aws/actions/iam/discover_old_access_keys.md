---
title: Discover Old Access Keys
parent: iam
grand_parent: Actions
layout: default
permalink: /aws/actions/iam/discover_old_access_keys
---

# Discover Old Access Keys

Discover IAM access keys above a certain age.<br/>

<p align="center">
   <a href="https://github.com/avtomat-hub/avtomat-aws/tree/main/avtomat_aws/iam/discover_old_access_keys.py">Source code</a> •
   <a href="/aws/permissions/iam/discover_old_access_keys">Permissions</a>
</p>

## Usage

### Input

Parameters are used for both programmatic input and command-line arguments.<br/>

- The `Applicable` column indicates whether the parameter is accepted in Programmatic (P), Command-Line (C), or Both (
  B).<br/>
- For Command-Line execution, type `list` parameters are passed as space-separated strings.

| Parameter        | Description                                    | Type     | Applicable | Required | Default value   |
|------------------|------------------------------------------------|----------|------------|----------|-----------------|
| `threshold_days` | Get access keys older than this number of days | `int`    | B          | Yes      | None            |
| `region`         | Region for operation                           | `string` | B          | No       | Session default |
| `debug`          | Log verbosity                                  | `bool`   | B          | No       | None            |
| `session`        | Established session                            | `object` | P          | No       | None            |

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

Discover access keys older than 90 days:

```bash
aaws iam discover_old_access_keys --threshold_days 90
```

Programmatic usage:

```python
from avtomat_aws import iam

response = iam.discover_old_access_keys(threshold_days=90)
```