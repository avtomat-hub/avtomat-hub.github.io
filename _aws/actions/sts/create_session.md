---
title: Create Session
parent: sts
grand_parent: Actions
layout: default
permalink: /aws/actions/sts/create_session
---

# Create Session

Create an authenticated session.<br/>
Supported methods:

- Profile
- Credentials
- Assume role
- Fallback to
  Boto3 [authentication flow](https://boto3.amazonaws.com/v1/documentation/api/latest/guide/credentials.html)

<p align="center">
   <a href="https://github.com/avtomat-hub/avtomat-aws/tree/main/avtomat_aws/sts/create_session.py">Source code</a>
</p>

## Usage

### Input

| Parameter       | Description          | Type     | Required | Default value   |
|-----------------|----------------------|----------|----------|-----------------|
| `access_key`    | AWS Access Key       | `string` | No       | None            |
| `secret_key`    | AWS Secret Key       | `string` | No       | None            |
| `session_token` | AWS Session Token    | `string` | No       | None            |
| `profile`       | AWS Profile          | `string` | No       | None            |
| `role_arn`      | AWS Role ARN         | `string` | No       | None            |
| `mfa_serial`    | MFA Device ARN       | `string` | No       | None            |
| `mfa_token`     | MFA Token            | `string` | No       | None            |

### Output

Returns a Boto3 Session `object`.

## Examples

Assume a role with MFA:<br/>

{: .note}
This will export temporary credentials to the environment: `AWS_ACCESS_KEY_ID`, `AWS_SECRET_ACCESS_KEY`, `AWS_SESSION_TOKEN`

```bash
eval $(aaws sts create_session --role_arn arn:aws:iam::123456789012:role/ExampleRole --mfa_serial arn:aws:iam::111111111111:mfa/Example --mfa_token 123456)
```

Programmatic usage:

```python
from avtomat_aws import sts

session = sts.create_session(role_arn="arn:aws:iam::123456789012:role/ExampleRole",
                             mfa_serial="arn:aws:iam::111111111111:mfa/Example",
                             mfa_token="123456")
```