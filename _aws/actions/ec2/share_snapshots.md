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

Parameters are used for both programmatic input and command-line arguments.<br/>

- The `Applicable` column indicates whether the parameter is accepted in Programmatic (P), Command-Line (C), or Both (
  B).<br/>
- For Command-Line execution, type `list` parameters are passed as space-separated strings.

| Parameter        | Description                                           | Type           | Applicable | Required | Default Value   |
|------------------|-------------------------------------------------------|----------------|------------|----------|-----------------|
| `snapshot_ids`   | List of EC2 snapshots to move                         | `list(string)` | B          | Yes      | None            |
| `target_account` | Target account for the snapshots                      | `string`       | B          | Yes      | None            |
| `role_arn`       | AWS Role ARN for session creation                     | `string`       | B          | No       | None            |
| `region`         | Region for operation. Leave blank for session default | `string`       | B          | No       | Session Default |
| `debug`          | Increase log verbosity                                | `bool`         | B          | No       | False           |
| `session`        | Established session                                   | `object`       | P          | No       | None            |                           |

### Output

Returns a `list` of successfully shared snapshots:

```python
['snap-1234567890abcdef0', 'snap-abcdef1234567890']
```

## Examples

Share snapshots with account 123456789012:

```bash
aws_ec2_share_snapshots --snapshot_ids snap-1234567890abcdef0 snap-abcdef1234567890 --target_account 123456789012 --region eu-west-2
```

Programmatic usage:

```python
from avtomat_aws import ec2

response = ec2.share_snapshots(snapshot_ids=["snap-1234567890abcdef0", "snap-abcdef1234567890"],
                               target_account="123456789012",
                               region="eu-west-2")
```
