---
title: IAM Actions
layout: default
---

```python
from avtomat_aws import helpers
from avtomat_aws import iam

if __name__ == '__main__':

    session = helpers.create_session()

    # Discover access keys older than 90 days and disable them
    access_keys = iam.discover_old_access_keys(threshold_days=90, session=session)
    for key in access_keys:
        iam.modify_access_key(key['AccessKeyId'], key['UserName'], disable=True, session=session)

    # Discover users with passwords older than 90 days or without MFA and disable their console access
    users = []
    users.extend(iam.discover_old_password_users(threshold_days=90, session=session))
    users.extend(iam.discover_no_mfa_users(session=session))
    users = list(set(users))
    for user in users:
        iam.modify_user_console_access(user, disable=True, session=session)

    # Discover users with no activity over 60 days and disable their console access
    users = iam.discover_inactive_users(threshold_days=60, session=session)
    for user in users:
        iam.modify_user_console_access(user, disable=True, session=session)

```