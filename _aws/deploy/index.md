---
title: Deploy
nav_order: 2
has_children: true
layout: default
permalink: /aws/deploy
---

# Deploy as layer for AWS Lambda

These pages contain instructions for deploying `avtomat-aws` as a lambda layer to an AWS account.<br/>
Once deployed, lambda functions can access the package by having the layer [attached](https://docs.aws.amazon.com/lambda/latest/dg/adding-layers.html).

## Deployment
The package can be deployed through [Terraform](/aws/deploy/terraform).