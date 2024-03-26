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

## Usage <button id="toggleButton" class="btn fs-3" onclick="toggleTables()">CLI</button>

### Input

| Parameter            | Description                                           | Type           | Required | Default Value   |
|----------------------|-------------------------------------------------------|----------------|----------|-----------------|
| `security_group_ids` | List of Security Group IDs to delete                  | `list(string)` | Yes      | None            |
| `region`             | Region for operation. Leave blank for session default | `string`       | No       | Session Default |
| `debug`              | Increase log verbosity                                | `bool`         | No       | False           |
| `silent`             | Decrease log verbosity                                | `bool`         | No       | False           |
| `session`            | Established session                                   | `object`       | No       | None            |                           

### Output

Returns a `list` of security group IDs that failed the deletion:

```python
['sg-1234567890abcdef0', 'sg-abcdef1234567890']
```

<div markdown="1" id="cli" style="display: block;">

## Examples

Delete security groups in eu-west-2:

```bash
aaws ec2 delete_security_groups --security_group_ids sg-1234567890abcdef0 sg-abcdef1234567890 --region eu-west-2
```

</div>

<div markdown="1" id="prog" style="display: none;">

## Examples

Delete security groups in eu-west-2:

```python
from avtomat_aws import ec2

response = ec2.delete_security_groups(security_group_ids=["sg-1234567890abcdef0", "sg-abcdef1234567890"],
                                      region="eu-west-2")
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

