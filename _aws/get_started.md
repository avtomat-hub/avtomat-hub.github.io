---
title: Get started
nav_order: 1
layout: default
permalink: /aws/get_started
---

# Amazon Web Services Collection
{: .fs-8 }

This collection is built on top of <a href="https://boto3.amazonaws.com/v1/documentation/api/latest/index.html" target="_blank">Boto3</a>.
{: .fs-5 .fw-300 }

{: .warning}
Under active development. Email [dimitar@avtomat.io](mailto:dimitar@avtomat.io) if you encounter any issues.

---

## Requirements

- <a href="https://www.python.org/downloads/" target="_blank">Python 3.x</a>
- <a href="https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-getting-started.html" target="_blank">AWS CLI</a>


## How to use


### Installation

Install `avtomat-aws` in a virtual environment:

```bash
python -m venv avtomat-aws
source avtomat-aws/bin/activate
pip install git+ssh://git@github.com/avtomat-hub/avtomat-aws.git
```
Once installed, you can either use actions directly through the command line or import them in your code.

Review the list of [actions](/aws/actions) available and their minimum IAM [permissions](/aws/permissions) required.<br/>
[Examples](/aws/examples) are a great place to explore programmatic usage and chaining ideas.


### Authentication
This collection will look for credentials in the following sequence:

1. Environment variables: **Credentials**
```bash
export AWS_ACCESS_KEY_ID=foo
export AWS_SECRET_ACCESS_KEY=bar
```
2. Environment variables: **Profile** (must be present in `~/.aws/credentials` or `~/.aws/config`)
```bash
export AWS_PROFILE=foo
```
3. Credentials file (`~/.aws/credentials`): **default** profile
```bash
[default]
aws_access_key_id = foo
aws_secret_access_key = bar
[dev]
aws_access_key_id = foo2
aws_secret_access_key = bar2
```
4. Config file (`~/.aws/config`): **default** profile
```bash
[default]
aws_access_key_id = foo
aws_secret_access_key = bar
[profile dev]
aws_access_key_id = foo2
aws_secret_access_key = bar2
```

### Region setting
This collection will look for region in the following sequence:
1. Action argument
```bash
ec2.discover_instances(region="us-east-1")
```
2. Environment variables: **default** region
```bash
export AWS_DEFAULT_REGION=us-east-1
```
3. Config file (`~/.aws/config`): **default** region for selected profile
```bash
[profile dev]
region = us-east-1
```
4. Region of already established session
```bash
ec2.discover_instances(session=session)
```
5. Region not supplied anywhere, default to `us-east-1`

## Deployment

### AWS Lambda
This collection can be used in AWS Lambda functions with a `python3.x` runtime.<br/>
Refer to [Infrastructure as Code](/aws/iac) for deployment instructions.
