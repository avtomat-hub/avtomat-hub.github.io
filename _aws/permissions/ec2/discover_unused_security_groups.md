---
title: Discover Unused Security Groups
parent: ec2
grand_parent: Permissions
layout: default
permalink: /aws/permissions/ec2/discover_unused_security_groups
---

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "ec2:DescribeSecurityGroups",
                "ec2:DescribeNetworkInterfaces",
                "ec2:DescribeInstances",
                "rds:DescribeDBInstances",
                "elasticloadbalancing:DescribeLoadBalancers",
                "elasticloadbalancing:DescribeLoadBalancerAttributes",
                "lambda:ListFunctions",
                "redshift:DescribeClusters",
                "elasticache:DescribeCacheClusters",
                "elasticmapreduce:ListClusters",
                "elasticmapreduce:DescribeCluster",
                "ecs:ListClusters",
                "ecs:ListTasks",
                "ecs:DescribeTasks",
                "es:ListDomainNames",
                "es:DescribeDomain",
                "kafka:ListClusters"
            ],
            "Resource": "*"
        }
    ]
}
```