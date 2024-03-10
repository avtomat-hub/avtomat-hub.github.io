---
title: ec2
parent: Examples
layout: default
permalink: /aws/examples/ec2
---

```python
from avtomat_aws import helpers
from avtomat_aws import ec2

if __name__ == '__main__':

    session = helpers.create_session()

    regions = ec2.discover_active_regions(session=session)

    # Discover all instances and encrypt their unencrypted volumes
    for region in regions:
        instances = ec2.discover_instances(mode='all', region=region, session=session)
        for instance in instances:
            result = ec2.encrypt_instance_volumes(instance_id=instance,
                                                  kms_key_id="test", region=region, session=session)

    # Discover unencrypted, detached volumes and encrypt them
    for region in regions:
        volumes = ec2.discover_volumes(region=region, detached=True, unencrypted=True, session=session)
        for volume in volumes:
            result = ec2.encrypt_volume(volume_id=volume, kms_key_id="test",
                                        region=region, session=session)

    # Discover detached volumes and snapshots associated with them and delete them
    for region in regions:
        volumes = ec2.discover_volumes(region=region, detached=True, session=session)
        snapshots = ec2.discover_snapshots(region=region, volume_ids=volumes, session=session)
        ec2.delete_volumes(volume_ids=volumes, snapshot=True, region=region, session=session)
        ec2.delete_snapshots(snapshot_ids=snapshots, region=region, session=session)

    # Discover regions where default EBS encryption is not enabled and enable it
    for region in regions:
        result = ec2.discover_default_ebs_encryption(region=region, session=session)
        if not result['enabled']:
            ec2.modify_default_ebs_encryption(enable=True, region=region, session=session)

    # Discover instances missing "Owner" tag and add it
    for region in regions:
        resources = ec2.discover_tags(resource_types=['instance'], key='Owner', missing=True, region=region,
                                      session=session)
        failed_resources = ec2.modify_tags(resource_ids=resources, tags=['Owner=Acme'], region=region,
                                           session=session)

    # Discover unencrypted snapshots, create encrypted copies and delete the original ones
    for region in regions:
        snapshots = ec2.discover_snapshots(region=region, unencrypted=True, session=session)
        copied_snapshots = ec2.copy_snapshots(snapshot_ids=snapshots, region=region, target_region=region,
                                              encrypt=True, session=session)
        ec2.delete_snapshots(snapshot_ids=snapshots, region=region, session=session)

    # Discover unused security groups and delete them
    for region in regions:
        security_groups = ec2.discover_unused_security_groups(region=region, session=session)
        ec2.delete_security_groups(security_group_ids=security_groups, region=region, session=session)

```