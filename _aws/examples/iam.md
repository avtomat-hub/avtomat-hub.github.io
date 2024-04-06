---
title: iam
parent: Examples
layout: default
permalink: /aws/examples/iam
---

### Discover access keys older than 90 days and disable them

```python
from avtomat_aws import sts, iam

if __name__ == '__main__':
    session = sts.create_session()

    access_keys = iam.discover_old_access_keys(threshold_days=90, session=session)
    iam.modify_access_keys(keys=access_keys, disable=True, session=session)
```

---

### Discover users with passwords older than 90 days and disable their console access

```python
from avtomat_aws import sts, iam

if __name__ == '__main__':
    session = sts.create_session()
    
    users = iam.discover_old_password_users(threshold_days=90, session=session)
    iam.modify_users_console_access(users=users, disable=True, session=session)
```

---

### Discover users without MFA and disable their console access

```python
from avtomat_aws import sts, iam

if __name__ == '__main__':
    session = sts.create_session()

    users = iam.discover_no_mfa_users(session=session)
    iam.modify_users_console_access(users=users, disable=True, session=session)
```

---

### Discover users with no activity over 60 days and disable their console access

```python
from avtomat_aws import sts, iam

if __name__ == '__main__':
    session = sts.create_session()
    
    users = iam.discover_inactive_users(threshold_days=60, session=session)
    iam.modify_users_console_access(users=users, disable=True, session=session)
```
