---
title: Share Snapshots
parent: ec2
grand_parent: Actions
layout: default
permalink: /aws/actions/ec2/share_snapshots
---

# Share Snapshots

Share EC2 snapshots with other accounts.<br/>

{: .warning}
If sharing encrypted snapshots with another account, ensure the KMS key is shared with the target account.<br/>
    <a href="https://docs.aws.amazon.com/kms/latest/developerguide/key-policy-modifying-external-accounts.html#cross-account-console" target="_blank">Share a custom key with another account</a>

{: .warning}
 If snapshots are encrypted with AWS managed key, create copies with a custom key and share the copies.<br/>
 <a href="copy_snapshots.md">Copy Snapshots</a>

<p align="center">
   <a href="https://github.com/avtomat-hub/avtomat-aws/tree/main/avtomat_aws/ec2/share_snapshots.py">Source code</a> •
   <a href="/aws/permissions/ec2/share_snapshots">Permissions</a>
</p>

## Usage

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

## Examples

Share snapshots with account 123456789012:

```bash
aaws ec2 share_snapshots --snapshot_ids snap-1234567890abcdef0 snap-abcdef1234567890 --target_account 123456789012 --region eu-west-2
```

Programmatic usage:

```python
from avtomat_aws import ec2

response = ec2.share_snapshots(snapshot_ids=["snap-1234567890abcdef0", "snap-abcdef1234567890"],
                               target_account="123456789012",
                               region="eu-west-2")
```
