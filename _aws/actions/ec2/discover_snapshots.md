---
title: Discover Snapshots
parent: ec2
grand_parent: Actions
layout: default
permalink: /aws/actions/ec2/discover_snapshots
---

# Discover Snapshots

Discover snapshots of EBS volumes based on specified criteria.

<p align="center">
   <a href="https://github.com/avtomat-hub/avtomat-aws/tree/main/avtomat_aws/services/ec2/discover_snapshots.py">Source code</a> •
   <a href="/aws/permissions/ec2/discover_snapshots">Permissions</a>
</p>

{: .note}
Only snapshots owned by the account are returned.

## Usage <button id="toggleButton" class="btn fs-3" onclick="toggleTables()">CLI</button>

### Input

| Parameter            | Description                                           | Type           | Required | Default Value   |
|----------------------|-------------------------------------------------------|----------------|----------|-----------------|
| `volume_ids`         | Get snapshots that originate from specific volumes    | `list(string)` | No       | All volumes     |
| `snapshot_ids`       | Snapshot IDs to focus on                              | `list(string)` | No       | All snapshots   |
| `unencrypted`        | Get only unencrypted snapshots                        | `bool`         | No       | False           |
| `exclude_aws_backup` | Exclude snapshots managed by AWS Backup               | `bool`         | No       | False           |
| `created_before`     | Get snapshots created before date (YYYY/MM//DD)       | `string`       | No       | None            |
| `created_after`      | Get snapshots created after date (YYYY/MM//DD)        | `string`       | No       | None            |
| `region`             | Region for operation. Leave blank for session default | `string`       | No       | Session Default |
| `debug`              | Increase log verbosity                                | `bool`         | No       | False           |
| `silent`             | Decrease log verbosity                                | `bool`         | No       | False           |
| `output`             | Output format <br/> `table`                           | `string`       | No       | None            |
| `session`            | Established session                                   | `object`       | No       | None            |

### Output

Returns a `list` of discovered snapshot IDs:

```python
['snap-1234567890abcdef0', 'snap-abcdef1234567890']
```

<div markdown="1" id="cli" style="display: block;">

## Examples

Fetch all snapshots in eu-west-2:

```bash
aaws ec2 discover_snapshots --region eu-west-2
```

Fetch snapshots created before 2024/01/01 and not managed by AWS Backup:

```bash
aaws ec2 discover_snapshots --exclude__aws_backup --created_before 2024/01/01
```

</div>

<div markdown="1" id="prog" style="display: none;">

## Examples

Fetch all snapshots in eu-west-2:

```python
from avtomat_aws import ec2

response = ec2.discover_snapshots(region="eu-west-2")
```

Fetch snapshots created before 2024/01/01 and not managed by AWS Backup:

```python
from avtomat_aws import ec2

response = ec2.discover_snapshots(exclude_aws_backup=True,
                                  created_before="2024/01/01")
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
