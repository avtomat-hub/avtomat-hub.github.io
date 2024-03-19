---
title: Delete Security Groups
parent: ec2
grand_parent: Actions
layout: default
permalink: /aws/actions/ec2/delete_security_groups
---

# Delete Security Groups

Delete EC2 security groups.<br/>

<p align="center">
   <a href="https://github.com/avtomat-hub/avtomat-aws/tree/main/avtomat_aws/ec2/delete_security_groups.py">Source code</a> •
   <a href="/aws/permissions/ec2/delete_security_groups">Permissions</a>
</p>

## Usage

### Input

| Parameter            | Description                                           | Type           | Required | Default Value   |
|----------------------|-------------------------------------------------------|----------------|----------|-----------------|
| `security_group_ids` | List of Security Group IDs to delete                  | `list(string)` | Yes      | None            |
| `region`             | Region for operation. Leave blank for session default | `string`       | No       | Session Default |
| `debug`              | Increase log verbosity                                | `bool`         | No       | False           |
| `session`            | Established session                                   | `object`       | No       | None            |                           

### Output

Returns a `list` of security group IDs that failed the deletion:

```python
['sg-1234567890abcdef0', 'sg-abcdef1234567890']
```

## Examples

Delete security groups in eu-west-2:

```bash
aaws ec2 delete_security_groups --security_group_ids sg-1234567890abcdef0 sg-abcdef1234567890 --region eu-west-2
```

Programmatic usage:

```python
from avtomat_aws import ec2

response = ec2.delete_security_groups(security_group_ids=["sg-1234567890abcdef0", "sg-abcdef1234567890"],
                                      region="eu-west-2")
```
