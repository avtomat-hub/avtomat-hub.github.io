---
title: sts
parent: Examples
layout: default
permalink: /aws/examples/sts
---

### Perform actions across active regions in a given account

```python
from avtomat_aws import sts, ec2

if __name__ == '__main__':
    role_arn = "arn:aws:iam::123456789012:role/ExampleRole"
    
    session = sts.create_session(role_arn=role_arn)
    regions = ec2.discover_active_regions(session=session)
    
    for region in regions:
        response = some_action(region=region, session=session)
```

---

### Perform actions across multiple accounts

```python
from avtomat_aws import sts

if __name__ == '__main__':
    role_arns = ["arn:aws:iam::123456789012:role/ExampleRole", 
                 "arn:aws:iam::210987654321:role/ExampleRole"]
    
    for arn in role_arns:
        session = sts.create_session(role_arn=arn)
        response = some_action(session=session)
```