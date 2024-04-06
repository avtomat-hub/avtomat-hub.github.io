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
   <a href="https://github.com/avtomat-hub/avtomat-aws/tree/main/avtomat_aws/services/sts/create_session.py">Source code</a> •
   <a href="/aws/permissions/sts/create_session">Permissions</a>
</p>

## Usage <button id="toggleButton" class="btn fs-3" onclick="toggleTables()">CLI</button>

### Input

| Parameter       | Description            | Type     | Required | Default value |
|-----------------|------------------------|----------|----------|---------------|
| `access_key`    | AWS Access Key         | `string` | No       | None          |
| `secret_key`    | AWS Secret Key         | `string` | No       | None          |
| `session_token` | AWS Session Token      | `string` | No       | None          |
| `profile`       | AWS Profile            | `string` | No       | None          |
| `role_arn`      | AWS Role ARN           | `string` | No       | None          |
| `mfa_serial`    | MFA Device ARN         | `string` | No       | None          |
| `mfa_token`     | MFA Token              | `string` | No       | None          |
| `debug`         | Increase log verbosity | `bool`   | No       | False         |
| `silent`        | Decrease log verbosity | `bool`   | No       | False         |

### Output

Returns a Boto3 Session `object`.

<div markdown="1" id="cli" style="display: block;">

## Examples

Assume a role with MFA:<br/>

{: .note}
This will export temporary credentials to the
environment: `AWS_ACCESS_KEY_ID`, `AWS_SECRET_ACCESS_KEY`, `AWS_SESSION_TOKEN`

```bash
eval $(aaws sts create_session --role_arn arn:aws:iam::123456789012:role/ExampleRole --mfa_serial arn:aws:iam::111111111111:mfa/Example --mfa_token 123456)
```

</div>

<div markdown="1" id="prog" style="display: none;">

## Examples

Assume a role with MFA:<br/>

{: .note}
This will return a Boto3 session object that can be passed to other actions.

```python
from avtomat_aws import sts

session = sts.create_session(role_arn="arn:aws:iam::123456789012:role/ExampleRole",
                             mfa_serial="arn:aws:iam::111111111111:mfa/Example",
                             mfa_token="123456")
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
