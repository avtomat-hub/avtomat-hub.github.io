---
title: Delete Security Groups
parent: Elastic Compute Cloud (EC2)
layout: default
---

# Delete Security Groups

Delete EC2 security groups.<br/>

<p align="center">
   <a href="/avtomat_aws/ec2/delete_security_groups.py">Source code</a> •
   <a href="/permissions/ec2/delete_security_groups">Permissions</a>
</p>

## Usage

### Input

Parameters are used for both programmatic input and command-line arguments.<br/>

- The `Applicable` column indicates whether the parameter is accepted in Programmatic (P), Command-Line (C), or Both (
  B).<br/>
- For Command-Line execution, type `list` parameters are passed as space-separated strings.

| Parameter            | Description                                           | Type           | Applicable | Required | Default Value   |
|----------------------|-------------------------------------------------------|----------------|------------|----------|-----------------|
| `security_group_ids` | List of Security Group IDs to delete                  | `list(string)` | B          | Yes      | None            |
| `role_arn`           | AWS Role ARN for session creation                     | `string`       | B          | No       | None            |
| `region`             | Region for operation. Leave blank for session default | `string`       | B          | No       | Session Default |
| `debug`              | Increase log verbosity                                | `bool`         | B          | No       | False           |
| `session`            | Established session                                   | `object`       | P          | No       | None            |                           

### Output

Returns a `list` of deleted security group IDs:

```python
['sg-1234567890abcdef0', 'sg-abcdef1234567890']
```

## Examples

Delete security groups in eu-west-2:

```bash
aws_ec2_delete_security_groups --security_group_ids sg-1234567890abcdef0 sg-abcdef1234567890 --region eu-west-2
```

Programmatic usage:

```python
from avtomat_aws import ec2

response = ec2.delete_security_groups(security_group_ids=["sg-1234567890abcdef0", "sg-abcdef1234567890"],
                                      region="eu-west-2")
```
