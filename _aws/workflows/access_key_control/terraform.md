---
title: Terraform
parent: Access Key Control
grand_parent: Workflows
layout: default
permalink: /aws/workflows/access_key_control/terraform
---

# Terraform deployment
You can use this module locally, by cloning the workflow repository, or remotely, by referencing the modules from your own repository, similar to Terraform Registry.

<p align="center">
   <a href="https://github.com/avtomat-hub/aws-workflow-access-key-control/tree/main/terraform">Source code</a>
</p>

## Remote
Recommended approach.

### Initial setup

1. Copy one of the examples to your own repository
2. Review `variables.tf` and export environment variables
   - The account for which environment variables are exported is the hub account
3. Point the module sources to the `avtomat-hub` GitHub organization.
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

1. Clone this repository
2. Navigate to the [terraform](.) directory
3. Copy one of the [examples](examples) to the root of the [terraform](.) directory
4. Review `variables.tf` and export environment variables
   - The account for which environment variables are exported is the hub account
5. Run `terraform init`
6. Run `terraform apply`

### Maintenance
If a new version of the module is available, pull the changes with `git pull`.<br/>
Run `terraform init` and `terraform apply`.

## Support
Please email any questions, feature requests or bug reports to [dimitar@avtomat.io](mailto:dimitar@avtomat.io)