# Predictive scaling service\-linked role<a name="aws-auto-scaling-service-linked-roles"></a>

AWS Auto Scaling uses service\-linked roles for the permissions that it requires to call other AWS on your behalf when you work with a scaling plan\. For more information, see [Service\-linked roles for scaling plans](security_iam_service-with-iam.md#security_iam_service-with-iam-roles-service-linked)\.

The following sections describe how to create and manage the service\-linked role for predictive scaling\. Start by configuring permissions to allow an IAM entity \(such as a user, group, or role\) to create, edit, or delete a service\-linked role\.

## Permissions granted by the service\-linked role<a name="service-linked-role-permissions"></a>

AWS Auto Scaling uses the service\-linked role named **AWSServiceRoleForAutoScalingPlans\_EC2AutoScaling** to call the following actions on your behalf when you enable predictive scaling:
+ `cloudwatch:GetMetricData`
+ `autoscaling:DescribeAutoScalingGroups`
+ `autoscaling:DescribeScheduledActions`
+ `autoscaling:BatchPutScheduledUpdateGroupAction`
+ `autoscaling:BatchDeleteScheduledAction`

**AWSServiceRoleForAutoScalingPlans\_EC2AutoScaling** trusts the `autoscaling-plans.amazonaws.com` service to assume the role\.

## Create the service\-linked role \(automatic\)<a name="create-service-linked-role-automatic"></a>

You don't need to manually create the **AWSServiceRoleForAutoScalingPlans\_EC2AutoScaling** role\. AWS Auto Scaling creates this role for you when you create a scaling plan in your account and enable predictive scaling\.

For AWS Auto Scaling to create a service\-linked role on your behalf, you must have the required permissions\. For more information, see [Service\-linked role permissions](https://docs.aws.amazon.com/IAM/latest/UserGuide/using-service-linked-roles.html#service-linked-role-permissions) in the *IAM User Guide*\.

## Create the service\-linked role \(manual\)<a name="create-service-linked-role-manual"></a>

To create the service\-linked role manually, you can use the IAM console, IAM CLI, or IAM API\. For more information, see [Creating a service\-linked role](https://docs.aws.amazon.com/IAM/latest/UserGuide/using-service-linked-roles.html#create-service-linked-role) in the *IAM User Guide*\.

**To create a service\-linked role \(AWS CLI\)**  
Use the following [create\-service\-linked\-role](https://docs.aws.amazon.com/cli/latest/reference/iam/create-service-linked-role.html) CLI command to create the service\-linked role\.

```
aws iam create-service-linked-role --aws-service-name autoscaling-plans.amazonaws.com
```

## Edit the service\-linked role<a name="edit-service-linked-role"></a>

You can edit the description of **AWSServiceRoleForAutoScalingPlans\_EC2AutoScaling** using IAM\. For more information, see [Editing a service\-linked role](https://docs.aws.amazon.com/IAM/latest/UserGuide/using-service-linked-roles.html#edit-service-linked-role) in the *IAM User Guide*\.

## Delete the service\-linked role<a name="delete-service-linked-role"></a>

If you no longer need to use scaling plans, we recommend that you delete **AWSServiceRoleForAutoScalingPlans\_EC2AutoScaling**\. 

You can delete a service\-linked role only after you delete all scaling plans in your AWS account that have predictive scaling enabled\. This ensures that you can't inadvertently remove permissions to access your scaling plans\.

You can use the IAM console, IAM CLI, or IAM API to delete the service\-linked role\. For more information, see [Deleting a service\-linked role](https://docs.aws.amazon.com/IAM/latest/UserGuide/using-service-linked-roles.html#delete-service-linked-role) in the *IAM User Guide*\.

After you delete the **AWSServiceRoleForAutoScalingPlans\_EC2AutoScaling** service\-linked role, AWS Auto Scaling creates the role again if you create a scaling plan with predictive scaling enabled\. 

## Supported Regions<a name="slr-regions"></a>

AWS Auto Scaling supports using service\-linked roles in all of the AWS Regions where scaling plans available\. For information about the Regional availability of scaling plans, see [AWS Auto Scaling endpoints and quotas](https://docs.aws.amazon.com/general/latest/gr/autoscaling_region.html) in the *AWS General Reference*\.