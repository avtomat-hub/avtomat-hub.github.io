---
title: Modify Tags
parent: ec2
grand_parent: Actions
layout: default
permalink: /aws/actions/ec2/modify_tags
---

# Modify Tags

Create or delete tags for EC2 resources.<br/>

{: .note}
<a href="https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/Using_Tags.html#tag-resources" target="_blank">Supported
EC2 resources</a>

{: .warning}
If a tag key already exists, the tag value is replaced with the new value.

{: .warning}
**dynamic_tags** mode will make an API call per resource. Not suitable for operations of scale.

<p align="center">
   <a href="https://github.com/avtomat-hub/avtomat-aws/tree/main/avtomat_aws/ec2/modify_tags.py">Source code</a> •
   <a href="/aws/permissions/ec2/modify_tags">Permissions</a>
</p>

## Usage

### Input

| Parameter      | Description                                                                                        | Type           | Required        | Default Value   |
|----------------|----------------------------------------------------------------------------------------------------|----------------|-----------------|-----------------|
| `resource_ids` | List of EC2 resource IDs to apply tags to                                                          | `list(string)` | Yes             | None            |
| `tags`         | Tags to create or delete (Key=Value)                                                               | `list(string)` | Yes             | None            |
| `create`       | Create tags                                                                                        | `bool`         | If not `delete` | False           |
| `delete`       | Delete tags                                                                                        | `bool`         | If not `create` | False           |
| `dynamic_tags` | Dynamically add the resource ID to the tag key or value where `{resource_id}` placeholder is found | `bool`         | No              | False           |
| `region`       | Region for operation. Leave blank for session default                                              | `string`       | No              | Session Default |
| `debug`        | Increase log verbosity                                                                             | `bool`         | No              | False           |
| `session`      | Established session                                                                                | `object`       | No              | None            |                           

### Output

Returns a `list` of resources that failed the modification:

```python
['vol-1234567890abcdef0', 'i-abcdef1234567890']
```

## Examples

Create tags for resources:

```bash
aaws ec2 modify_tags --resource_ids vol-1234567890abcdef0 i-abcdef1234567890 --tags Name=example "Owner=Foo + Bar" --create
```

Delete tags for resources:

```bash
aaws ec2 modify_tags --resource_ids vol-1234567890abcdef0 i-abcdef1234567890 --tags Name Owner --delete
```

Create dynamic tags for resources:

```bash
aaws ec2 modify_tags --resource_ids vol-1234567890abcdef0 i-abcdef1234567890 --tags Foo={resource_id} "Bar={resource_id}-foo" --create --dynamic_tags
```

Programmatic usage:

```python
from avtomat_aws import ec2

response = ec2.modify_tags(resource_ids=["vol-1234567890abcdef0", "i-abcdef1234567890"],
                           tags=["Foo={resource_id}", "Bar={resource_id}-foo"],
                           create=True,
                           dynamic_tags=True)
```
