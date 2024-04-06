---
title: ec2
parent: Examples
layout: default
permalink: /aws/examples/ec2
---

### Discover all instances and encrypt their unencrypted volumes

```python
from avtomat_aws import sts, ec2

if __name__ == '__main__':
    session = sts.create_session()
    regions = ec2.discover_active_regions(session=session)
    
    for region in regions:
        instances = ec2.discover_instances(region=region, session=session)
        for instance in instances:
            result = ec2.encrypt_instance_volumes(instance_id=instance,
                                                  kms_key_id="1234abcd-12ab-34cd-56ef-1234567890ab", 
                                                  region=region, session=session)
```

---

### Discover unencrypted, detached volumes and encrypt them

```python
from avtomat_aws import sts, ec2

if __name__ == '__main__':
    session = sts.create_session()
    regions = ec2.discover_active_regions(session=session)
    
    for region in regions:
        volumes = ec2.discover_volumes(region=region, detached=True, unencrypted=True, session=session)
        for volume in volumes:
            result = ec2.encrypt_volume(volume_id=volume, kms_key_id="1234abcd-12ab-34cd-56ef-1234567890ab",
                                        region=region, session=session)
```

---

### Discover detached volumes and snapshots associated with them and delete them

```python
from avtomat_aws import sts, ec2

if __name__ == '__main__':
    session = sts.create_session()
    regions = ec2.discover_active_regions(session=session)
    
    for region in regions:
        volumes = ec2.discover_volumes(region=region, detached=True, session=session)
        snapshots = ec2.discover_snapshots(region=region, volume_ids=volumes, session=session)
        ec2.delete_volumes(volume_ids=volumes, snapshot=True, region=region, session=session)
        ec2.delete_snapshots(snapshot_ids=snapshots, region=region, session=session)
```

---

### Discover regions where default EBS encryption is not enabled and enable it

```python
from avtomat_aws import sts, ec2

if __name__ == '__main__':
    session = sts.create_session()
    regions = ec2.discover_active_regions(session=session)
    
    for region in regions:
        result = ec2.discover_default_ebs_encryption(region=region, session=session)
        if not result['enabled']:
            ec2.modify_default_ebs_encryption(enable=True, region=region, session=session)
```

---

### Discover instances missing "Owner" tag and add it

```python
from avtomat_aws import sts, ec2

if __name__ == '__main__':
    session = sts.create_session()
    regions = ec2.discover_active_regions(session=session)
    
    for region in regions:
        resources = ec2.discover_tags(resource_types=['instance'], key='Owner', missing=True, region=region,
                                      session=session)
        failed_resources = ec2.modify_tags(resource_ids=resources, tags=['Owner=Acme'], region=region,
                                           session=session)
```

---

### Discover unencrypted snapshots, create encrypted copies and delete the original ones

```python
from avtomat_aws import sts, ec2

if __name__ == '__main__':
    session = sts.create_session()
    regions = ec2.discover_active_regions(session=session)
    
    for region in regions:
        snapshots = ec2.discover_snapshots(region=region, unencrypted=True, session=session)
        copied_snapshots = ec2.copy_snapshots(snapshot_ids=snapshots, region=region, target_region=region,
                                              encrypt=True, session=session)
        ec2.delete_snapshots(snapshot_ids=snapshots, region=region, session=session)
```

---

### Discover unused security groups and delete them

```python
from avtomat_aws import sts, ec2

if __name__ == '__main__':
    session = sts.create_session()
    regions = ec2.discover_active_regions(session=session)
    
    for region in regions:
        security_groups = ec2.discover_unused_security_groups(region=region, session=session)
        ec2.delete_security_groups(security_group_ids=security_groups, region=region, session=session)
```

---

### Create snapshots of instance root volumes, encrypt them, delete the originals and share with another account
Process used by companies like Wiz or Orca Security when performing agentless vulnerability scanning

```python
from avtomat_aws import sts, ec2

if __name__ == '__main__':
    session = sts.create_session()
    regions = ec2.discover_active_regions(session=session)
    
    for region in regions:
        instances = ec2.discover_instances(region=region, session=session)
        volumes = ec2.discover_volumes(instance_ids=instances, root=True, region=region, session=session)
        snapshots = ec2.create_snapshots(volumes=volumes, region=region, session=session)
        # KMS key is owned by target account and shared with source account
        encrypted_snapshots = ec2.copy_snapshots(snapshot_ids=snapshots,
                                                 region=region,
                                                 target_region=region,
                                                 encrypt=True,
                                                 kms_key_id="1234abcd-12ab-34cd-56ef-1234567890ab",
                                                 session=session)
        ec2.share_snapshots(snapshot_ids=encrypted_snapshots,
                            target_account="123456789012",
                            region=region,
                            session=session)
        # At this point the target account should process the snapshots like create volumes, attach to instances, etc.
        # Once persistent volumes are created or scanning is complete, the snapshots can be deleted
        ec2.delete_snapshots(snapshot_ids=snapshots,
                             region=region,
                             session=session)
        ec2.delete_snapshots(snapshot_ids=encrypted_snapshots,
                             region=region,
                             session=session)
```
    