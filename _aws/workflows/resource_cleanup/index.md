---
title: Resource Cleanup
parent: Workflows
has_children: true
layout: default
permalink: /aws/workflows/resource_cleanup
---

# Resource Cleanup

Detect and delete orphaned resources above a certain age.<br/>

<img src="/assets/images/resource_cleanup.png?raw=true" style="width: 80rem; display: block; margin: auto;">

## Overview

This workflow follows a hub-and-spoke model where components are deployed to a service (hub) account and a role is
deployed to each serviced (spoke) account.

### Operation

The workflow will assume a role in each serviced account and perform the following actions in each configured region:

1. Discover resources that don't have exclusion tags
2. Evaluate the age and state of the discovered resources
3. Retrieve resources scheduled for deletion from S3
4. Remove resources from S3 that are not discovered in current run
5. Retrieve resources ready to delete from S3
    - Derived from S3 object last modified date and `wait_before_delete_days`
6. Delete resources that are discovered in current run and ready for deletion
7. Schedule newly detected resources for deletion by uploading to S3

The workflow is scheduled to run once a day through an EventBridge Rule.<br/>
Adjustable by passing a custom `schedule` to
the [schedule](https://github.com/avtomat-hub/terraform-aws-workflow-resource-cleanup/tree/main/modules/schedule)
module.<br/>

Workflow logs can be found in CloudWatch Logs.

At the moment there isn't any support for producing a notification in the event of a resource being deleted.
You can request this by emailing [dimitar@avtomat.io](mailto:dimitar@avtomat.io).

### Supported resource types

<details>
<summary><u>EC2 Images</u></summary>
<ul>
<li>Delete images older than the threshold</li>
<li>Delete underlying snapshots comprising the image</li>
<li>Do not target images managed by AWS Backup</li>
<li>Do not target images with exclusion tags</li>
</ul>
</details>
<details>
<summary><u>EC2 Snapshots</u></summary>
<ul>
<li>Delete snapshots older than the threshold</li>
<li>Do not target snapshots managed by AWS Backup</li>
<li>Do not target snapshots with exclusion tags</li>
</ul>
</details>
<details>
<summary><u>EC2 Volumes</u></summary>
<ul>
<li>Delete volumes in detached state for a period longer than threshold</li>
<li>Create a snapshot before deleting the volume</li>
<li>Do not target volumes with exclusion tags</li>
<li>Maximum threshold supported: 90 days</li>
<li>Log a warning and skip volumes for which CloudTrail event cannot be found</li>
</ul>
</details>
<details>
<summary><u>EC2 Instances</u> - COMING SOON</summary>
<ul>
<li>Delete instances in stopped state for a period longer than threshold</li>
<li>Create an image before deleting the instance</li>
<li>Do not target instances with exclusion tags</li>
<li>Maximum threshold supported: 90 days</li>
<li>Log a warning and skip instances for which CloudTrail event cannot be found</li>
</ul>
</details>

### Configuration

This workflow is configured through `config.json`. Each supported resource type has its own configuration section.

#### Schema

- `accounts` - List of account IDs to be scanned
- `vars` - Workflow variables
    - `regions` - List of regions to be scanned in each account
    - `exclude_tags` - Tags that exclude resources from being scanned
    - `threshold_days` - Age threshold for resources to be scheduled for deletion
    - `wait_before_delete_days` - Grace period before resources that are scheduled for deletion are actually deleted
    - `cutoff_date` - Date before which resources are not scanned (Only applies to `ec2-images` and `ec2-snapshots`)
    - `bucket_name` - S3 bucket name for storing resources that are scheduled for deletion

{: .note}
To exclude a resource type from being scanned, pass an empty `accounts`.

```json
{
  "ec2-images": {
    "accounts": []
  }
}
```

## Requirements

- <a href="https://developer.hashicorp.com/terraform/install" target="_blank">Terraform</a>
- <a href="https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-getting-started.html" target="_blank">AWS CLI</a>
- [avtomat-aws](https://github.com/avtomat-hub/avtomat-aws)
    - Collection must exist as a Lambda Layer in the hub account before deploying this workflow

## Components

| Resource                    | Amount | Description                                                                                                                                |
|-----------------------------|--------|--------------------------------------------------------------------------------------------------------------------------------------------|
| **EventBridge Rule**        | 1      | To schedule the workflow.                                                                                                                  |
| **S3 Bucket**               | 1      | To store resources scheduled for deletion.                                                                                                 |
| **Step Function**           | 1      | To orchestrate the lambda functions.                                                                                                       |
| **Lambda Function**         | 3      | Source code for the workflow. Lambda per resource type.                                                                                    |
| **CloudWatch Log Group**    | 3      | Workflow logs. Log group per lambda.                                                                                                       |
| **IAM Role**                | 5      | x3 Lambda function role. <br/> x1 EventBridge role for rule to start step function. <br/> x1 Step function role to start lambda functions. |
| **IAM Role Policy**         | 5      | x3 Policy for lambda function role. <br/> x1 Policy for eventbridge role. <br/> x1 Policy for step function role.                          |
| **IAM Service Role**        | X      | Service role assumed by the workflow. Deployed to hub and spoke accounts.                                                                  |
| **IAM Service Role Policy** | X      | Policy for service role.                                                                                                                   |

## Deployment

This workflow can be deployed through Terraform.<br/>
Read [Deploy](/aws/workflows/resource_cleanup/deploy) to get started.