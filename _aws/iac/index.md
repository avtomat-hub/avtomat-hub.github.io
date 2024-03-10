---
title: Infrastructure as Code
nav_order: 2
has_children: true
layout: default
permalink: /aws/iac
---

# Deploy as AWS Lambda layer

These pages contain instructions for deploying `avtomat-aws` as a lambda layer to an AWS account.<br/>
Once deployed, lambda functions can access the package by having the layer [attached](https://docs.aws.amazon.com/lambda/latest/dg/adding-layers.html).

## Deployment
The package can be deployed through [Terraform](/aws/iac/terraform).