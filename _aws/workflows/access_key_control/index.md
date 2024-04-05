---
title: Access Key Control
parent: Workflows
has_children: true
layout: default
permalink: /aws/workflows/access_key_control
---

# Access Key Control

Detect IAM access keys over a certain age and disable them.<br/>

<img src="/assets/images/access_key_control.png?raw=true" style="width: 80rem; display: block; margin: auto;">

## Overview

This workflow follows a hub-and-spoke model where components are deployed to a service (hub) account and a role is
deployed to each serviced (spoke) account.

### Operation

The workflow will assume a role in each serviced account and perform the following actions:

1. Discover IAM access keys over a certain age
2. Disable the discovered access keys

The workflow is scheduled to run once a day through an EventBridge Rule.<br/>
Adjustable by passing a custom `schedule` to
the [core](https://github.com/avtomat-hub/terraform-aws-workflow-access-key-control/tree/main/modules/core) module.<br/>

Workflow logs can be found in CloudWatch Logs.

At the moment there isn't any support for producing a notification in the event of a key being disabled.
You can request this by emailing [dimitar@avtomat.io](mailto:dimitar@avtomat.io).

## Requirements

- <a href="https://developer.hashicorp.com/terraform/install" target="_blank">Terraform</a>
- <a href="https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-getting-started.html" target="_blank">AWS CLI</a>
- [avtomat-aws](https://github.com/avtomat-hub/avtomat-aws)
    - Collection must exist as a Lambda Layer in the hub account before deploying this workflow

## Components

| Resource                       | Amount | Description                                                               |
|--------------------------------|--------|---------------------------------------------------------------------------|
| **EventBridge Rule**           | 1      | To schedule the workflow.                                                 |
| **Lambda Function**            | 1      | Source code for the workflow.                                             |
| **Lambda Function Permission** | 1      | Permission allowing eventbridge rule to invoke lambda function.           |
| **CloudWatch Log Group**       | 1      | Workflow logs.                                                            |
| **IAM Role**                   | 1      | Basic lambda function permissions.                                        |
| **IAM Role Policy**            | 1      | Policy for lambda function role.                                          |
| **IAM Service Role**           | X      | Service role assumed by the workflow. Deployed to hub and spoke accounts. |
| **IAM Service Role Policy**    | X      | Policy for service role.                                                  |

## Deployment

This workflow can be deployed through Terraform.<br/>
Read [Deploy](/aws/workflows/access_key_control/deploy) to get started.