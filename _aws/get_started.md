---
title: Get started
nav_order: 1
layout: default
permalink: /aws/get_started
---

# Amazon Web Services Collection
{: .fs-8 }

This collection runs on top of <a href="https://boto3.amazonaws.com/v1/documentation/api/latest/index.html" target="_blank">Boto3</a>.
{: .fs-5 .fw-300 }

{: .warning}
Early development. Raise an [issue](https://github.com/avtomat-hub/avtomat-aws/issues) if you encounter any bugs.

<p>
   <a href="#requirements">Requirements</a> •
   <a href="#installation">Installation</a> •
   <a href="#authentication">Authentication</a> •
   <a href="#deployment">Deployment</a>
</p>

---

## Requirements

- <a href="https://www.python.org/downloads/" target="_blank">Python 3.x</a>
- <a href="https://boto3.amazonaws.com/v1/documentation/api/latest/index.html" target="_blank">Boto3</a>
- AWS configuration files 
  - `~/.aws/credentials` and `~/.aws/config`
  - This is optional but highly recommended for falling back to Boto3 authentication flow


## Installation

### Virtual environment (pip)

```bash
python3 -m venv venv
source venv/bin/activate
pip install avtomat-aws
aaws --help
```

### Global (recommended: pipx)
```bash
pipx install avtomat-aws
aaws --help
```

Once installed you can use actions directly through the command line or import them in your code.

Review the list of [actions](/aws/actions) available and their minimum IAM [permissions](/aws/permissions) required.<br/>
[Examples](/aws/examples) are a great place to explore programmatic usage and chaining ideas.


## Authentication
This collection supports the following authentication methods, in order:
1. Profile
2. Credentials
3. Assume role
4. Fallback to Boto3 [authentication flow](https://boto3.amazonaws.com/v1/documentation/api/latest/guide/credentials.html)

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

### Examples

#### CLI

- Authenticate profile
```bash
eval $(aaws sts create_session --profile <NAME>)
aaws sts whoami
```

- Authenticate credentials
```bash
eval $(aaws sts create_session --access_key <KEY> --secret_key <KEY>)
aaws sts whoami
```

- Assume role with MFA
```bash
eval $(aaws sts create_session --role_arn <ARN> --mfa_serial <ARN> --mfa_token <CODE>)
aaws sts whoami
```

- Assume role without MFA
```bash
eval $(aaws sts create_session --role_arn <ARN>)
aaws sts whoami
```

- Fallback to Boto3 authentication flow
```bash
aaws sts whoami
```

#### Programmatic

- Authenticate credentials
```python
from avtomat_aws import sts
session = sts.create_session(access_key="KEY", secret_key="KEY")
response = sts.whoami(session)       
print(response)                      
```

- Assume role
```python
from avtomat_aws import sts
session = sts.create_session(role_arn="ARN_HERE")
response = sts.whoami(session)
print(response)
```

- Fallback to Boto3 authentication flow
```python
from avtomat_aws import sts
response = sts.whoami()
print(response)
```

For more details, refer to [Create Session](/aws/actions/sts/create_session).


## Deployment

### AWS Lambda
This collection can be used by AWS Lambda functions with `python3.x` runtime.<br/>
Refer to [Deploy](/aws/deploy) for deployment instructions.
