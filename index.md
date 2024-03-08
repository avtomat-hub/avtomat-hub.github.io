---
title: Home
layout: home
nav_order: 1
---

<h1 align="center">
  <br>
  Amazon Web Services Collection
  <br>
  <br>
</h1>

<h4 align="center">Collection of actions on top of <a href="https://boto3.amazonaws.com/v1/documentation/api/latest/index.html" target="_blank">Boto3</a> designed to automate various cloud operations. Use individually or combine to create complex workflows.</h4>

<p align="center">
  <a href="#features">Features</a> •
  <a href="#requirements">Requirements</a> •
  <a href="#how-to-use">How to use</a>
</p>


## Features

- ✅ **Flexible** 
  - Actions can be used individually (CLI) or chained together to form workflows (programmatic)
- ✅ **Standardised** 
  - Each action receives input, processes it, and returns an output 
- ✅ **Interlinkable** 
  - Output from one action can be used as input to another action
- ✅ **Pre-configured**
  - Built in retry and error handling 
  - Embedded logging for each action
  - Automatic pagination when dealing with many resources
- ✅ **Least-privilege** 
  - Permissions are defined for each action and can be used to swiftly create secure IAM policies


## Requirements

- <a href="https://www.python.org/downloads/" target="_blank">Python 3.x</a>
- <a href="https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-getting-started.html" target="_blank">AWS CLI</a>


## How to use

Install `avtomat-aws` in a virtual environment:

```bash
python -m venv venv
source venv/bin/activate
pip install git+ssh://git@github.com/avtomat-hub/avtomat-aws.git
```

Once installed, you can either use actions directly through the command line or import them in your code.

Each action is documented in [actions](actions) and has least-privilege permissions defined in [permissions](permissions).

Simple chaining ideas can be found in [examples](examples).

---

[avtomat.io](https://www.avtomat.io) &nbsp;•&nbsp;
Email: [dimitar.atanasov@avtomat.io](mailto:dimitar.atanasov@avtomat.io)
