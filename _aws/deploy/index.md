---
title: Deploy
layout: default
permalink: /aws/deploy
---

# Deploy as layer for AWS Lambda

Instructions for deploying `avtomat-aws` as a lambda layer to an AWS account.<br/>
Once deployed, lambda functions can access the package by having the layer [attached](https://docs.aws.amazon.com/lambda/latest/dg/adding-layers.html).

## Deployment
1. Install the package in a target folder named `python`
```bash
pip3 install avtomat-aws -t ~/path/to/python
```
2. Create a zip archive of the folder
3. [Upload](https://docs.aws.amazon.com/lambda/latest/dg/creating-deleting-layers.html) the zip archive to Lambda as a layer
4. [Attach](https://docs.aws.amazon.com/lambda/latest/dg/adding-layers.html) the layer to lambda functions