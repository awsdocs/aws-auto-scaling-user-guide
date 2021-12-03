# How scaling plans work with IAM<a name="security_iam_service-with-iam"></a>

Before you use IAM to manage who can create, access, and manage AWS Auto Scaling scaling plans, you should understand what IAM features are available to use with scaling plans\.

**Topics**
+ [Identity\-based policies](#security_iam_service-with-iam-id-based-policies)
+ [Resource\-based policies](#security_iam_service-with-iam-resource-based-policies)
+ [Access Control Lists \(ACLs\)](#security_iam_service-with-iam-acls)
+ [Authorization based on tags](#security_iam_service-with-iam-tags)
+ [IAM roles](#security_iam_service-with-iam-roles)

## Identity\-based policies<a name="security_iam_service-with-iam-id-based-policies"></a>

With IAM identity\-based policies, you can specify allowed or denied actions and resources, and the conditions under which actions are allowed or denied\. Scaling plans support specific actions, resources, and condition keys\. To learn about all of the elements that you use in a JSON policy, see [IAM JSON policy elements reference](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_elements.html) in the *IAM User Guide*\.

### Actions<a name="security_iam_service-with-iam-id-based-policies-actions"></a>

Administrators can use AWS JSON policies to specify who has access to what\. That is, which **principal** can perform **actions** on what **resources**, and under what **conditions**\.

The `Action` element of a JSON policy describes the actions that you can use to allow or deny access in a policy\. Policy actions usually have the same name as the associated AWS API operation\. There are some exceptions, such as *permission\-only actions* that don't have a matching API operation\. There are also some operations that require multiple actions in a policy\. These additional actions are called *dependent actions*\.

Include actions in a policy to grant permissions to perform the associated operation\.

Scaling plan actions in IAM policy statements use the following prefix before the action: `autoscaling-plans:`\. Policy statements must include either an `Action` or `NotAction` element\. Scaling plans have their own sets of actions that describe tasks that you can perform with this service\.

To specify multiple actions in a single statement, separate them with commas as shown in the following example\.

```
"Action": [
      "autoscaling-plans:DescribeScalingPlans",
      "autoscaling-plans:DescribeScalingPlanResources"
```

You can specify multiple actions using wildcards \(\*\)\. For example, to specify all actions that begin with the word `Describe`, include the following action\.

```
"Action": "autoscaling-plans:Describe*"
```

To see a complete list of scaling plan actions that can be used in policy statements, see [Actions, resources, and condition keys for AWS Auto Scaling](https://docs.aws.amazon.com/service-authorization/latest/reference/list_awsautoscaling.html) in the *Service Authorization Reference*\. 

### Resources<a name="security_iam_service-with-iam-id-based-policies-resources"></a>

The `Resource` element specifies the object or objects to which the action applies\.

Scaling plans have no service\-defined resources that can be used as the `Resource` element of an IAM policy statement\. Therefore, there are no Amazon Resource Names \(ARNs\) for you to use in an IAM policy\. To control access to scaling plan actions, always use an \* \(asterisk\) as the resource when writing an IAM policy\. 

### Condition keys<a name="security_iam_service-with-iam-id-based-policies-conditionkeys"></a>

The `Condition` element \(or `Condition` *block*\) lets you specify conditions in which a statement is in effect\. For example, you might want a policy to be applied only after a specific date\. To express conditions, use predefined condition keys\.

Scaling plans do not provide any service\-specific condition keys, but they do support using some global condition keys\. To see all AWS global condition keys, see [AWS global condition context keys](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html) in the *IAM User Guide*\. 

The `Condition` element is optional\. 

### Examples<a name="security_iam_service-with-iam-id-based-policies-examples"></a>

To view examples of identity\-based policies for scaling plans, see [Identity\-based policy examples for scaling plans](security_iam_id-based-policy-examples.md)\.

## Resource\-based policies<a name="security_iam_service-with-iam-resource-based-policies"></a>

Other Amazon Web Services, such as Amazon Simple Storage Service, support resource\-based permissions policies\. For example, you can attach a permissions policy to an S3 bucket to manage access permissions to that bucket\.

Scaling plans do not support resource\-based policies\.

## Access Control Lists \(ACLs\)<a name="security_iam_service-with-iam-acls"></a>

Scaling plans do not support Access Control Lists \(ACLs\)\.

## Authorization based on tags<a name="security_iam_service-with-iam-tags"></a>

Scaling plans cannot be tagged\. They also have no service\-defined resources that can be tagged\. Therefore, they do not support controlling access based on tags on a resource\.

Scaling plans may contain taggable resources, such as Auto Scaling groups, that support controlling access based on tags\. For more information, see the IAM documentation for that AWS service\. 

## IAM roles<a name="security_iam_service-with-iam-roles"></a>

An [IAM role](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles.html) is an entity within your AWS account that has specific permissions\.

### Using temporary credentials<a name="security_iam_service-with-iam-roles-tempcreds"></a>

You can use temporary credentials to sign in with federation, to assume an IAM role, or to assume a cross\-account role\. You obtain temporary security credentials by calling AWS STS API operations such as [AssumeRole](https://docs.aws.amazon.com/STS/latest/APIReference/API_AssumeRole.html) or [GetFederationToken](https://docs.aws.amazon.com/STS/latest/APIReference/API_GetFederationToken.html)\. 

Scaling plans support using temporary credentials\. 

### Service\-linked roles for scaling plans<a name="security_iam_service-with-iam-roles-service-linked"></a>

AWS Auto Scaling uses service\-linked roles for the permissions that it requires to call other AWS services on your behalf\. Service\-linked roles make setting up scaling plans easier because you don't have to manually add the necessary permissions\. For more information, see [Using service\-linked roles](https://docs.aws.amazon.com/IAM/latest/UserGuide/using-service-linked-roles.html) in the *IAM User Guide*\.

AWS Auto Scaling uses a few types of service\-linked roles to call other AWS services on your behalf when you work with a scaling plan:
+ *Predictive scaling service\-linked role* — Allows AWS Auto Scaling to access historical metric data from CloudWatch\. Also allows creation of scheduled actions for Auto Scaling groups based on a load forecast and capacity prediction\. For more information, see [Predictive scaling service\-linked role](aws-auto-scaling-service-linked-roles.md)\.
+ *Amazon EC2 Auto Scaling service\-linked role* — Allows AWS Auto Scaling to access and manage target tracking scaling policies for Auto Scaling groups\. For more information, see [Service\-linked roles for Amazon EC2 Auto Scaling](https://docs.aws.amazon.com/autoscaling/ec2/userguide/autoscaling-service-linked-role.html) in the *Amazon EC2 Auto Scaling User Guide*\.
+ *Application Auto Scaling service\-linked role* — Allows AWS Auto Scaling to access and manage target tracking scaling policies for other scalable resources\. There is one service\-linked role for each service\. For more information, see [Service\-linked roles for Application Auto Scaling](https://docs.aws.amazon.com/autoscaling/application/userguide/application-auto-scaling-service-linked-roles.html) in the *Application Auto Scaling User Guide*\.

You can use the following procedure to determine if your account already has a service\-linked role\.<a name="procedure_check_instance_role"></a>

**To determine whether a service\-linked role already exists**

1. Open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Roles**\. 

1. Search the list for `AWSServiceRole` to find the service\-linked roles that exist in your account\. Look for the name of the service\-linked role that you want to check\.

### Service roles<a name="security_iam_service-with-iam-roles-service"></a>

AWS Auto Scaling has no service roles for scaling plans\.