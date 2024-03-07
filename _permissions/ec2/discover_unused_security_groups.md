---
title: Discover Unused Security Groups
parent: Elastic Compute Cloud (EC2)
layout: default
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
        },
        {
            "Effect": "Allow",
            "Action": "sts:AssumeRole",
            "Resource": "arn:aws:iam::123456789012:role/ExampleRole"
        }
    ]
}
```