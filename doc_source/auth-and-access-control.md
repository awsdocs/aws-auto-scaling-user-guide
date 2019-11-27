# Authentication and Access Control for AWS Auto Scaling<a name="auth-and-access-control"></a>

Access to AWS Auto Scaling requires credentials that AWS can use to authenticate your requests\. Those credentials must have [permissions](https://docs.aws.amazon.com/IAM/latest/UserGuide/access.html) to perform AWS Auto Scaling actions, such as creating scaling plans\.

This topic provides details on how you can use AWS Identity and Access Management \(IAM\) to help secure your resources by controlling who can perform AWS Auto Scaling actions\. 

By default, a brand new IAM user has no permissions to do anything\. To grant permissions to call AWS Auto Scaling actions, you attach an IAM policy to the IAM users or groups that require the permissions it grants\. 

## Specifying Actions in a Policy<a name="aws-auto-scaling-actions"></a>

You can specify any and all AWS Auto Scaling actions in an IAM policy\. For more information, see [Actions](https://docs.aws.amazon.com/autoscaling/plans/APIReference/API_Operations.html) in the *AWS Auto Scaling API Reference*\.

To specify a single policy, you can use the following prefix with the name of the action: `autoscaling-plans:`\. For example:

```
"Action": "autoscaling-plans:DescribeScalingPlans"
```

Wildcards are supported\. For example, you can use `autoscaling-plans:*` to specify all AWS Auto Scaling actions\.

```
"Action": "autoscaling-plans:*"
```

You can also use `Describe*` to specify all actions whose names start with `Describe`\.

```
"Action": "autoscaling-plans:Describe*"
```

In addition to the permissions for calling AWS Auto Scaling actions, users also require permissions to create a service\-linked role\.

When users create a scaling plan with predictive scaling enabled, AWS Auto Scaling creates a service\-linked role in your account, if the role does not exist already\. The service\-linked role grants permissions to AWS Auto Scaling, so that it can call other services on your behalf\. 

For automatic role creation to succeed, users must have permissions for the `iam:CreateServiceLinkedRole` action\. 

```
"Action": "iam:CreateServiceLinkedRole"
```

For more information, see [Service\-Linked Roles for AWS Auto Scaling](aws-auto-scaling-service-linked-roles.md)\.

## Specifying the Resource<a name="aws-auto-scaling-resources"></a>

AWS Auto Scaling has no service\-defined resources that can be used as the `Resource` element of an IAM policy statement\. Therefore, there are no Amazon Resource Names \(ARNs\) for you to use in an IAM policy\. To control access to AWS Auto Scaling actions, always use an \* \(asterisk\) as the resource when writing an IAM policy\. 

## Specifying Conditions in a Policy<a name="aws-autoscaling-keys"></a>

When you grant permissions, you can use IAM policy language to specify the conditions when a policy should take effect\. For example, you might want a policy to be applied only after a specific date\. To express conditions, use predefined condition keys\. 

For a list of condition keys supported by each AWS service, see [Actions, Resources, and Condition Keys for AWS Services](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_actions-resources-contextkeys.html) in the *IAM User Guide*\. For a list of condition keys that can be used in multiple AWS services, see [AWS Global Condition Context Keys](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html) in the *IAM User Guide*\.

AWS Auto Scaling does not provide additional condition keys\.

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
              "cloudformation:ListStackResources",
              "iam:CreateServiceLinkedRole"
            ],
            "Resource": "*"
        }
    ]
}
```

To configure predictive scaling for Auto Scaling groups, users must also have permission to use the actions in the following example policy\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
              "cloudwatch:GetMetricData",
              "autoscaling:DescribeAutoScalingGroups",
              "autoscaling:DescribeScheduledActions",
              "autoscaling:BatchPutScheduledUpdateGroupAction",
              "autoscaling:BatchDeleteScheduledAction"
            ],
            "Resource": "*"
        }
    ]
}
```

## Additional IAM Permissions<a name="aws-auto-scaling-additional-permissions"></a>

Users must have additional permissions for each type of resource they must add to a scaling plan\. You specify the following actions in the `Action` element of an IAM policy statement\. 

**Auto Scaling groups**
+ `autoscaling:UpdateAutoScalingGroup`
+ `autoscaling:DescribeAutoScalingGroups`
+ `autoscaling:PutScalingPolicy`
+ `autoscaling:DescribePolicies`
+ `autoscaling:DeletePolicy`

**Auto Scaling groups that use predictive scaling**
+ `cloudwatch:GetMetricData`
+ `autoscaling:DescribeAutoScalingGroups`
+ `autoscaling:DescribeScheduledActions`
+ `autoscaling:BatchPutScheduledUpdateGroupAction`
+ `autoscaling:BatchDeleteScheduledAction`

**Resource types other than Auto Scaling groups**
+ `application-autoscaling:RegisterScalableTarget`
+ `application-autoscaling:DescribeScalableTargets`
+ `application-autoscaling:DeregisterScalableTarget`
+ `application-autoscaling:PutScalingPolicy`
+ `application-autoscaling:DescribeScalingPolicies`
+ `application-autoscaling:DeleteScalingPolicy`

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