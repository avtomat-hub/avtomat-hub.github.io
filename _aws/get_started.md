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

<p>
   <a href="#requirements">Requirements</a> •
   <a href="#installation">Installation</a> •
   <a href="#authentication">Authentication</a> •
   <a href="#deployment">Deployment</a>
</p>

---

## Requirements

- <a href="https://www.python.org/downloads/" target="_blank">Python 3.x</a>
- <a href="https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-getting-started.html" target="_blank">AWS CLI</a>


## Installation

Install `avtomat-aws` in a virtual environment:

```bash
python -m venv avtomat-aws
source avtomat-aws/bin/activate
pip install git+ssh://git@github.com/avtomat-hub/avtomat-aws.git
```
Once installed, you can either use actions directly through the command line or import them in your code.

Review the list of [actions](/aws/actions) available and their minimum IAM [permissions](/aws/permissions) required.<br/>
[Examples](/aws/examples) are a great place to explore programmatic usage and chaining ideas.


## Authentication
This collection supports the following authentication methods:
- Profile
- Credentials
- Assume role
- Fallback to Boto3 [authentication flow](https://boto3.amazonaws.com/v1/documentation/api/latest/guide/credentials.html)

### Quick start
- CLI:
```bash
aaws sts whoami
```
- Programmatic:
```python
from avtomat_aws import sts
response = sts.whoami()
print(response)
```

### Overview

All actions work in 3 authentication modes:

- Supplied session (programmatic)
```python
from avtomat_aws import sts
session = sts.create_session(profile="example")
response = sts.whoami(session)
print(response)
```
- Environment variables (CLI)
```bash
eval $(aaws sts create_session --role_arn <ARN_HERE>)
aaws sts whoami
```
- Fallback to Boto3 authentication flow (CLI or Programmatic)
```bash
aaws sts whoami
```
or
```python
response = sts.whoami()
print(response)
```

### Scenarios

- CLI: Assume role with MFA
```bash
eval $(aaws sts create_session --role_arn <ARN_HERE> --mfa_serial <ARN_HERE> --mfa_token <CODE_HERE>)
aaws sts whoami
```

- CLI: Authenticate credentials
```bash
eval $(aaws sts create_session --access_key <KEY> --secret_key <KEY>)
aaws sts whoami
```

- Programmatic: Authenticate credentials
```python
from avtomat_aws import sts
session = sts.create_session(access_key="KEY", secret_key="KEY")
response = sts.whoami(session)       
print(response)                      
```


## Deployment

### AWS Lambda
This collection can be used in AWS Lambda functions with a `python3.x` runtime.<br/>
Refer to [Infrastructure as Code](/aws/iac) for deployment instructions.
