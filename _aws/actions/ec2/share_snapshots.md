---
title: Share Snapshots
parent: ec2
grand_parent: Actions
layout: default
permalink: /aws/actions/ec2/share_snapshots
---

# Share Snapshots

Share EC2 snapshots with other accounts.<br/>

<p align="center">
   <a href="https://github.com/avtomat-hub/avtomat-aws/tree/main/avtomat_aws/ec2/share_snapshots.py">Source code</a> •
   <a href="/aws/permissions/ec2/share_snapshots">Permissions</a>
</p>

{: .warning}
If sharing encrypted snapshots with another account, ensure the KMS key is shared with the target account.<br/>
    <a href="https://docs.aws.amazon.com/kms/latest/developerguide/key-policy-modifying-external-accounts.html#cross-account-console" target="_blank">Share a custom key with another account</a>

{: .warning}
 If snapshots are encrypted with AWS managed key, create copies with a custom key and share the copies.<br/>
 <a href="copy_snapshots.md">Copy Snapshots</a>

## Usage <button id="toggleButton" class="btn fs-3" onclick="toggleTables()">CLI</button>

### Input

| Parameter        | Description                                           | Type           | Required | Default Value   |
|------------------|-------------------------------------------------------|----------------|----------|-----------------|
| `snapshot_ids`   | List of EC2 snapshots to move                         | `list(string)` | Yes      | None            |
| `target_account` | Target account for the snapshots                      | `string`       | Yes      | None            |
| `region`         | Region for operation. Leave blank for session default | `string`       | No       | Session Default |
| `debug`          | Increase log verbosity                                | `bool`         | No       | False           |
| `session`        | Established session                                   | `object`       | No       | None            |                           

### Output

Returns a `list` of successfully shared snapshots:

```python
['snap-1234567890abcdef0', 'snap-abcdef1234567890']
```

<div markdown="1" id="cli" style="display: block;">

## Examples

Share snapshots with account 123456789012:

```bash
aaws ec2 share_snapshots --snapshot_ids snap-1234567890abcdef0 snap-abcdef1234567890 --target_account 123456789012 --region eu-west-2
```

</div>

<div markdown="1" id="prog" style="display: none;">

## Examples

Share snapshots with account 123456789012:

```python
from avtomat_aws import ec2

response = ec2.share_snapshots(snapshot_ids=["snap-1234567890abcdef0", "snap-abcdef1234567890"],
                               target_account="123456789012",
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
