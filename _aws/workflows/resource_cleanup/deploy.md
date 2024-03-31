---
title: Deploy
parent: Resource Cleanup
grand_parent: Workflows
layout: default
permalink: /aws/workflows/resource_cleanup/deploy
---

# Terraform deployment
You can use these modules locally, by copying the workflow repository, or remotely, by referencing the modules from your own repository, similar to Terraform Registry.

<p align="center">
   <a href="https://github.com/avtomat-hub/terraform-aws-workflow-resource-cleanup">Source code</a>
</p>

## Remote

### Initial setup

1. Copy one of the `examples` to your own repository
2. Point module sources to the `avtomat-hub` GitHub organization.
3. Review `variables.tf` and export environment variables
   - The hub account will be the account for which environment variables are exported
4. Run `terraform init` and `terraform apply`

### Maintenance
To update the modules, bump the version of the `source` attributes:
```bash
ref=0.0.1 -> ref=0.0.2
```
Run `terraform init` and `terraform apply`.


## Local

### Initial setup

1. Copy this repository to your version control system
2. Copy one of the `examples` to the root of the repository or to a separate repository
3. Point module sources to local paths or version control system URLs, depending on the approach in step 2
4. Review `variables.tf` and export environment variables
   - The hub account will be the account for which environment variables are exported 
5. Run `terraform init` and `terraform apply`

### Maintenance
If a new version of the module is published in `avtomat-hub`, pull the changes to your copy.<br/>
Run `terraform init` and `terraform apply`.

## Support
Please email any questions, feature requests or bug reports to [dimitar@avtomat.io](mailto:dimitar@avtomat.io)