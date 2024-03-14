---
title: Who Am I
parent: sts
grand_parent: Actions
layout: default
permalink: /aws/actions/sts/whoami
---

# Who Am I

Quickly figure out your current credentials.<br/>

<p align="center">
   <a href="https://github.com/avtomat-hub/avtomat-aws/tree/main/avtomat_aws/sts/whoami.py">Source code</a>
</p>

## Usage

### Input

| Parameter       | Description         | Type     | Required | Default value |
|-----------------|---------------------|----------|----------|---------------|
| `debug`         | Log verbosity       | `bool`   | No       | None          |
| `session`       | Established session | `object` | No       | None          |

### Output

Returns a `string` indicating current entity.
```python
"arn:aws:iam::123456789012:user/FooBar"
```

## Examples

Find current credentials:

```bash
aaws sts whoami
```

Programmatic usage:

```python
from avtomat_aws import sts

response = sts.whoami()
```