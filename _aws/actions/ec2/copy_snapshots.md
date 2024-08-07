---
title: Copy Snapshots
parent: ec2
grand_parent: Actions
layout: default
permalink: /aws/actions/ec2/copy_snapshots
---

# Copy Snapshots

Create copies of EC2 snapshots in a target region.<br/>

<p align="center">
   <a href="https://github.com/avtomat-hub/avtomat-aws/tree/main/avtomat_aws/services/ec2/copy_snapshots.py">Source code</a> •
   <a href="/aws/permissions/ec2/copy_snapshots">Permissions</a>
</p>

{: .note}
If <b>encrypt</b> is set without <b>kms_key_id</b>, the default AWS managed key in the target region is used.

{: .note}
Snapshots are copied in batches of 20.<br/>
This default value can be increased through <b>pending_limit</b>.<br/>
<a href="https://aws.amazon.com/about-aws/whats-new/2020/04/amazon-ebs-increases-concurrent-snapshot-copy-limits-to-20-snapshots-per-destination-region/" target="_blank">
Concurrent snapshot copy limits</a>

## Usage <button id="toggleButton" class="btn fs-3" onclick="toggleTables()">CLI</button>

### Input

| Parameter       | Description                                           | Type           | Required     | Default Value   |
|-----------------|-------------------------------------------------------|----------------|--------------|-----------------|
| `snapshot_ids`  | List of EC2 snapshots to move                         | `list(string)` | Yes          | None            |
| `target_region` | Target region for the snapshots                       | `string`       | Yes          | None            |
| `pending_limit` | Limit for concurrent snapshot copy operations         | `int`          | No           | 20              |
| `encrypt`       | Encrypt the new snapshots                             | `bool`         | No           | False           |
| `kms_key_id`    | KMS Key ID to use for snapshot encryption             | `string`       | If `encrypt` | None            |
| `region`        | Region for operation. Leave blank for session default | `string`       | No           | Session Default |
| `debug`         | Increase log verbosity                                | `bool`         | No           | False           |
| `silent`        | Decrease log verbosity                                | `bool`         | No           | False           |
| `output`        | Output format <br/> `table`                           | `string`       | No           | None            |
| `session`       | Established session                                   | `object`       | No           | None            |                           

### Output

Returns a `list` of snapshots copies:

```python
['snap-1234567890abcdef0', 'snap-abcdef1234567890']
```

<div markdown="1" id="cli" style="display: block;">

## Examples

Create encrypted copies of snapshots in eu-west-2:

```bash
aaws ec2 copy_snapshots --snapshot_ids snap-1234567890abcdef0 snap-abcdef1234567890 --region eu-west-2 --target_region eu-west-2 --encrypt
```

Copy snapshots from eu-west-2 to us-east-1 and encrypt them with custom KMS key:

```bash
aaws ec2 copy_snapshots --snapshot_ids snap-1234567890abcdef0 snap-abcdef1234567890 --region eu-west-2 --target_region us-east-1 --encrypt --kms_key_id 1234abcd-12ab-34cd-56ef-1234567890ab
```

</div>

<div markdown="1" id="prog" style="display: none;">

## Examples

Create encrypted copies of snapshots in eu-west-2:

```python
from avtomat_aws import ec2

response = ec2.copy_snapshots(snapshot_ids=["snap-1234567890abcdef0", "snap-abcdef1234567890"],
                              region="eu-west-2",
                              target_region="eu-west-2",
                              encrypt=True)
```

Copy snapshots from eu-west-2 to us-east-1 and encrypt them with custom KMS key:

```python
from avtomat_aws import ec2

response = ec2.copy_snapshots(snapshot_ids=["snap-1234567890abcdef0", "snap-abcdef1234567890"],
                              region="eu-west-2",
                              target_region="us-east-1",
                              encrypt=True,
                              kms_key_id="1234abcd-12ab-34cd-56ef-1234567890ab")
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
