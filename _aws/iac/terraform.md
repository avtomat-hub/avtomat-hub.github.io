---
title: Terraform
parent: Infrastructure as Code
layout: default
permalink: /aws/iac/terraform
---

# Terraform deployment
You can use this module locally, by cloning `avtomat-hub/avtomat-aws` or remotely, by referencing the module from your own repository, similar to Terraform Registry.


## Remote
Recommended approach.

### Initial setup

1. Copy `/iac/terraform/examples` to your own repository
2. Review `variables.tf` and export environment variables
3. Point the module source to the `avtomat-hub` GitHub organization.
4. Run `terraform init`
5. Run `terraform apply`

### Maintenance
To update the module, bump the version of the `source` attribute.<br/>
```bash
ref=0.0.1 -> ref=0.0.2
```
Run `terraform init` and `terraform apply`.


## Local

### Initial setup

1. Clone the `avtomat-hub/avtomat-aws` repository
2. Copy `/iac/terraform/examples` to the root of the `/iac/terraform` directory
3. Review `variables.tf` and export environment variables
4. Run `terraform init`
5. Run `terraform apply`

### Maintenance
If a new version of the module is available, pull the changes with `git pull`.<br/>
Run `terraform init` and `terraform apply`.

## Support
Please email any questions, feature requests or bug reports to [dimitar@avtomat.io](mailto:dimitar@avtomat.io)