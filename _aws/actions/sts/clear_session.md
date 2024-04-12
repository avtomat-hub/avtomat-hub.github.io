---
title: Clear Session
parent: sts
grand_parent: Actions
layout: default
permalink: /aws/actions/sts/clear_session
---

# Clear Session

Clear an authenticated session.<br/>

<p align="center">
   <a href="https://github.com/avtomat-hub/avtomat-aws/tree/main/avtomat_aws/cli/sts/clear_session.py">Source code</a>
</p>

{: .note}
This action can only be used in CLI mode.

## Usage <button id="toggleButton" class="btn fs-3" onclick="toggleTables()">CLI</button>

### Input

| Parameter       | Description            | Type     | Required | Default value |
|-----------------|------------------------|----------|----------|---------------|
| `debug`         | Increase log verbosity | `bool`   | No       | False         |
| `silent`        | Decrease log verbosity | `bool`   | No       | False         |

### Output

Returns either Linux (bash) or Windows (powershell) commands to clear exported environment variables.
#### Linux
```bash
unset AWS_ACCESS_KEY_ID; 
unset AWS_SECRET_ACCESS_KEY; 
unset AWS_SESSION_TOKEN;
```
#### Windows
```bash
$Env:AWS_ACCESS_KEY_ID=''; 
$Env:AWS_SECRET_ACCESS_KEY='';
$Env:AWS_SESSION_TOKEN='';
```

<div markdown="1" id="cli" style="display: block;">

## Examples

Clear a session:

{: .note}
This will remove temporary credentials from the environment.

#### Linux
```bash
eval $(aaws sts clear_session)
```

#### Windows
```bash
aaws sts clear_session | Invoke-Expression
```

</div>
