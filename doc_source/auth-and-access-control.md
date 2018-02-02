# Authentication and Access Control for AWS Auto Scaling<a name="auth-and-access-control"></a>

By default, IAM users don't have permission to create or modify AWS resources\. To grant IAM users permission to create or modify AWS resources, you must create policies using AWS Identity and Access Management \(IAM\)\. IAM policies grant permissions to specific resources and API actions\. You attach am IAM policy to the IAM users or groups that require the permissions it grants\. For more information, see [Access Management](http://docs.aws.amazon.com/IAM/latest/UserGuide/access.html) in the *IAM User Guide*\.

## AWS Auto Scaling Actions<a name="aws-auto-scaling-actions"></a>

You can specify any and all AWS Auto Scaling actions in an IAM policy\. Use the following prefix with the name of the action: `autoscaling-plans:`\. For example:

```
"Action": "autoscaling-plans:DescribeScalingPlans"
```

You can also use wildcards\. For example, use `autoscaling-plans:*` to specify all AWS Auto Scaling actions\.

```
"Action": "autoscaling-plans:*"
```

Use `Describe:*` to specify all actions whose names start with `Describe`\.

```
"Action": "autoscaling-plans:Describe*"
```

For a list of actions, see [AWS Auto Scaling Actions](http://docs.aws.amazon.com/autoscaling/plans/APIReference/API_Operations.html)\.

## AWS Auto Scaling Resources<a name="aws-auto-scaling-resources"></a>

When writing an IAM policy to control access to AWS Auto Scaling actions, you must use "\*" as the resource\. There are no supported Amazon Resource Names \(ARNs\) for AWS Auto Scaling resources\.

## AWS Auto Scaling Keys<a name="aws-autoscaling-keys"></a>

For a list of context keys supported by each AWS service and a list of AWS\-wide policy keys, see [AWS Service Actions and Condition Context Keys](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_actionsconditions.html) and [Global and IAM Condition Context Keys](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html) in the *IAM User Guide*\.

## Example Policies<a name="aws-auto-scaling-example-policies"></a>

To create a scaling plan, users must have permission to use the actions in the following example policy\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
              "autoscaling-plans:*",
              "cloudwatch:PutMetricAlarm",
              "cloudwatch:DeleteAlarms",
              "cloudwatch:DescribeAlarms",
              "cloudformation:ListStackResources"
            ],
            "Resource": "*"
        }
    ]
}
```

Users must have additional permissions for each type of scalable resource they must add to a scaling plan\.

**Auto Scaling groups**

+ `autoscaling:UpdateAutoScalingGroups`

+ `autoscaling:DescribeAutoScalingGroups`

+ `autoscaling:PutScalingPolicy`

+ `autoscaling:DescribePolicies`

+ `autoscaling:DeletePolicy`

**Resource types other than Auto Scaling groups**

+ `application-autoscaling:RegisterScalableTarget`

+ `application-autoscaling:DescribeScalableTargets`

+ `application-autoscaling:DeregisterScalableTarget`

+ `application-autoscaling:PutScalingPolicy`

+ `application-autoscaling:DescribeScalingPolicies`

+ `application-autoscaling:DeleteScalingPolicy`

+ `iam:CreateServiceLinkedRole`

**ECS services**

+ `ecs:DescribeServices`

+ `ecs:UpdateServices`

**Spot Fleet requests**

+ `ec2:DescribeSpotFleetRequests`

+ `ec2:ModifySpotFleetRequest`

**DynamoDB tables or global indexes**

+ `dynamodb:DescribeTable`

+ `dynamodb:UpdateTable`

**Aurora DB clusters**

+ `rds:AddTagsToResource`

+ `rds:CreateDBInstance`

+ `rds:DeleteDBInstance`

+ `rds:DescribeDBClusters`

+ `rds:DescribeDBInstances`