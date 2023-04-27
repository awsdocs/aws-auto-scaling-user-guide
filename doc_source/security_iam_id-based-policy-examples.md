# Identity\-based policy examples for scaling plans<a name="security_iam_id-based-policy-examples"></a>

By default, a brand new IAM user has no permissions to do anything\. An IAM administrator must create and assign IAM policies that give an IAM identity \(such as a user or role\) permission to work with scaling plans\.

To learn how to create an IAM policy using these example JSON policy documents, see [Creating policies on the JSON tab](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_create.html#access_policies_create-json-editor) in the *IAM User Guide*\.

**Topics**
+ [Policy best practices](#security_iam_service-with-iam-policy-best-practices)
+ [Allow users to create scaling plans](#example-policies-scaling-plans)
+ [Allow users to enable predictive scaling](#example-policies-predictive-scaling)
+ [Additional required permissions](#aws-auto-scaling-additional-permissions)
+ [Permissions required to create a service\-linked role](#aws-auto-scaling-slr-permissions)

## Policy best practices<a name="security_iam_service-with-iam-policy-best-practices"></a>

Identity\-based policies determine whether someone can create, access, or delete AWS Auto Scaling resources in your account\. These actions can incur costs for your AWS account\. When you create or edit identity\-based policies, follow these guidelines and recommendations:
+ **Get started with AWS managed policies and move toward least\-privilege permissions** – To get started granting permissions to your users and workloads, use the *AWS managed policies* that grant permissions for many common use cases\. They are available in your AWS account\. We recommend that you reduce permissions further by defining AWS customer managed policies that are specific to your use cases\. For more information, see [AWS managed policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_managed-vs-inline.html#aws-managed-policies) or [AWS managed policies for job functions](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_job-functions.html) in the *IAM User Guide*\.
+ **Apply least\-privilege permissions** – When you set permissions with IAM policies, grant only the permissions required to perform a task\. You do this by defining the actions that can be taken on specific resources under specific conditions, also known as *least\-privilege permissions*\. For more information about using IAM to apply permissions, see [ Policies and permissions in IAM](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies.html) in the *IAM User Guide*\.
+ **Use conditions in IAM policies to further restrict access** – You can add a condition to your policies to limit access to actions and resources\. For example, you can write a policy condition to specify that all requests must be sent using SSL\. You can also use conditions to grant access to service actions if they are used through a specific AWS service, such as AWS CloudFormation\. For more information, see [ IAM JSON policy elements: Condition](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_elements_condition.html) in the *IAM User Guide*\.
+ **Use IAM Access Analyzer to validate your IAM policies to ensure secure and functional permissions** – IAM Access Analyzer validates new and existing policies so that the policies adhere to the IAM policy language \(JSON\) and IAM best practices\. IAM Access Analyzer provides more than 100 policy checks and actionable recommendations to help you author secure and functional policies\. For more information, see [IAM Access Analyzer policy validation](https://docs.aws.amazon.com/IAM/latest/UserGuide/access-analyzer-policy-validation.html) in the *IAM User Guide*\.
+ **Require multi\-factor authentication \(MFA\)** – If you have a scenario that requires IAM users or a root user in your AWS account, turn on MFA for additional security\. To require MFA when API operations are called, add MFA conditions to your policies\. For more information, see [ Configuring MFA\-protected API access](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_mfa_configure-api-require.html) in the *IAM User Guide*\.

For more information about best practices in IAM, see [Security best practices in IAM](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html) in the *IAM User Guide*\.

## Allow users to create scaling plans<a name="example-policies-scaling-plans"></a>

The following shows an example of an identity\-based policy that grants permissions to create scaling plans\. 

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

To work with a scaling plan, end users must have additional permissions that allow them to work with specific resources in their account\. These permissions are listed in [Additional required permissions](#aws-auto-scaling-additional-permissions)\.

Each console user also needs permissions that allow them to discover the scalable resources in their account and to view graphs of CloudWatch metric data from the AWS Auto Scaling console\. The additional set of permissions required to work with the AWS Auto Scaling console is listed below: 
+ `cloudformation:ListStacks`: To list stacks\.
+ `tag:GetTagKeys`: To find scalable resources that contain certain tag keys\.
+ `tag:GetTagValues`: To find resources that contain certain tag values\.
+ `autoscaling:DescribeTags`: To find Auto Scaling groups that contain certain tags\.
+ `cloudwatch:GetMetricData`: To view data in metric graphs\.

## Allow users to enable predictive scaling<a name="example-policies-predictive-scaling"></a>

The following shows an example of an identity\-based policy that grants permissions to enable predictive scaling\. These permissions extend the features of scaling plans that are set up to scale Auto Scaling groups\. 

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

## Additional required permissions<a name="aws-auto-scaling-additional-permissions"></a>

To successfully configure scaling plans, end users must be granted permissions for each target service for which they will configure scaling\. To grant the minimum permissions required to work with target services, read the information in this section and specify the relevant actions in the `Action` element of an IAM policy statement\. 

**Auto Scaling groups**

To add Auto Scaling groups to a scaling plan, users must have the following permissions from Amazon EC2 Auto Scaling: 
+ `autoscaling:UpdateAutoScalingGroup`
+ `autoscaling:DescribeAutoScalingGroups`
+ `autoscaling:PutScalingPolicy`
+ `autoscaling:DescribePolicies`
+ `autoscaling:DeletePolicy`

**ECS services**

To add ECS services to a scaling plan, users must have the following permissions from Amazon ECS and Application Auto Scaling: 
+ `ecs:DescribeServices`
+ `ecs:UpdateService`
+ `application-autoscaling:RegisterScalableTarget`
+ `application-autoscaling:DescribeScalableTargets`
+ `application-autoscaling:DeregisterScalableTarget`
+ `application-autoscaling:PutScalingPolicy`
+ `application-autoscaling:DescribeScalingPolicies`
+ `application-autoscaling:DeleteScalingPolicy`

**Spot Fleet**

To add Spot Fleets to a scaling plan, users must have the following permissions from Amazon EC2 and Application Auto Scaling: 
+ `ec2:DescribeSpotFleetRequests`
+ `ec2:ModifySpotFleetRequest`
+ `application-autoscaling:RegisterScalableTarget`
+ `application-autoscaling:DescribeScalableTargets`
+ `application-autoscaling:DeregisterScalableTarget`
+ `application-autoscaling:PutScalingPolicy`
+ `application-autoscaling:DescribeScalingPolicies`
+ `application-autoscaling:DeleteScalingPolicy`

**DynamoDB tables or global indexes**

To add DynamoDB tables or global indexes to a scaling plan, users must have the following permissions from DynamoDB and Application Auto Scaling: 
+ `dynamodb:DescribeTable`
+ `dynamodb:UpdateTable`
+ `application-autoscaling:RegisterScalableTarget`
+ `application-autoscaling:DescribeScalableTargets`
+ `application-autoscaling:DeregisterScalableTarget`
+ `application-autoscaling:PutScalingPolicy`
+ `application-autoscaling:DescribeScalingPolicies`
+ `application-autoscaling:DeleteScalingPolicy`

**Aurora DB clusters**

To add Aurora DB clusters to a scaling plan, users must have the following permissions from Amazon Aurora and Application Auto Scaling: 
+ `rds:AddTagsToResource`
+ `rds:CreateDBInstance`
+ `rds:DeleteDBInstance`
+ `rds:DescribeDBClusters`
+ `rds:DescribeDBInstances`
+ `application-autoscaling:RegisterScalableTarget`
+ `application-autoscaling:DescribeScalableTargets`
+ `application-autoscaling:DeregisterScalableTarget`
+ `application-autoscaling:PutScalingPolicy`
+ `application-autoscaling:DescribeScalingPolicies`
+ `application-autoscaling:DeleteScalingPolicy`

## Permissions required to create a service\-linked role<a name="aws-auto-scaling-slr-permissions"></a>

AWS Auto Scaling requires permissions to create a service\-linked role the first time any user in your AWS account creates a scaling plan with predictive scaling enabled\. If the service\-linked role does not exist already, AWS Auto Scaling creates it in your account\. The service\-linked role grants permissions to AWS Auto Scaling so that it can call other services on your behalf\. 

For automatic role creation to succeed, users must have permissions for the `iam:CreateServiceLinkedRole` action\.

```
"Action": "iam:CreateServiceLinkedRole"
```

The following shows an example of an identity\-based policy that grants permissions to create a service\-linked role\. 

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": "iam:CreateServiceLinkedRole",
            "Resource": "arn:aws:iam::*:role/aws-service-role/autoscaling-plans.amazonaws.com/AWSServiceRoleForAutoScalingPlans_EC2AutoScaling",
            "Condition": {
                "StringLike": {
                    "iam:AWSServiceName":"autoscaling-plans.amazonaws.com"
                }
            }
        }
    ]
}
```

For more information, see [Predictive scaling service\-linked role](aws-auto-scaling-service-linked-roles.md)\.