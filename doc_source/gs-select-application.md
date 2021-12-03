# Step 1: Find your scalable resources<a name="gs-select-application"></a>

This section includes a hands\-on introduction to creating scaling plans in the AWS Auto Scaling console\. If this is your first scaling plan, we recommend that you start by creating a sample scaling plan using an Amazon EC2 Auto Scaling group\. 

## Prerequisites<a name="gs-select-application-prereq"></a>

To practice using a scaling plan, create an Auto Scaling group\. Launch at least one Amazon EC2 instance in the Auto Scaling group\. For more information, see [Getting started with Amazon EC2 Auto Scaling](https://docs.aws.amazon.com/autoscaling/ec2/userguide/GettingStartedTutorial.html) in the *Amazon EC2 Auto Scaling User Guide*\.

Use an Auto Scaling group with CloudWatch metrics enabled to have capacity data on the graphs that are available when you complete the **Create Scaling Plan** wizard\. For more information, see [Enable Auto Scaling group metrics](https://docs.aws.amazon.com/autoscaling/ec2/userguide/as-instance-monitoring.html#as-enable-group-metrics) in the *Amazon EC2 Auto Scaling User Guide*\.

Generate some load for a few days or more to have CloudWatch metric data available for the predictive scaling feature, if possible\.

Verify that you have the permissions required to work with scaling plans\. For more information, see [Identity and Access Management for scaling plans](auth-and-access-control.md)\.

## Add your Auto Scaling group to your new scaling plan<a name="gs-add-auto-scaling-group"></a>

When you create a scaling plan from the console, it helps you find your scalable resources as a first step\. Before you begin, confirm that you meet the following requirements:
+ You created an Auto Scaling group and launched at least one EC2 instance, as described in the previous section\.
+ The Auto Scaling group you created has existed for at least 24 hours\.

**To start creating a scaling plan**

1. Open the AWS Auto Scaling console at [https://console\.aws\.amazon\.com/awsautoscaling/](https://console.aws.amazon.com/awsautoscaling/)\.

1. On the navigation bar at the top of the screen, choose the same Region that you used when you created your Auto Scaling group\. 

1. From the welcome page, choose **Get started**\.  
![\[AWS welcome screen\]](http://docs.aws.amazon.com/autoscaling/plans/userguide/images/aws-as-gs-welcome-screen.PNG)

1. On the **Find scalable resources** page, do one of the following:
   + Choose **Search by CloudFormation stack**, and then choose the AWS CloudFormation stack to use\. 
   + Choose **Search by tag**\. Then, for each tag, choose a tag key from **Key** and tag values from **Value**\. To add tags, choose **Add another row**\. To remove tags, choose **Remove**\.
   + Choose **Choose EC2 Auto Scaling groups**, and then choose one or more Auto Scaling groups\.
**Note**  
For an introductory tutorial, choose **Choose EC2 Auto Scaling groups**, and then choose the Auto Scaling group you created\.  
![\[Choose EC2 Auto Scaling groups\]](http://docs.aws.amazon.com/autoscaling/plans/userguide/images/aws-as-gs-choose-asg.PNG)

1. Choose **Next** to continue with the scaling plan creation process\.

## Learn more about discovering your scalable resources<a name="gs-choose-discovery-method"></a>

If you have already created a sample scaling plan and would like to create more, see the following scenarios for using a CloudFormation stack or a set of tags in more detail\. You can use this section to decide whether to choose the **Search by CloudFormation stack** or **Search by tag** option to discover your scalable resources when using the console to create your scaling plan\.

When you choose the **Search by CloudFormation stack** or **Search by tag** option in step 1 of the **Create Scaling Plan** wizard, this makes the scalable resources associated with the stack or set of tags available to the scaling plan\. As you define your scaling plan, you can then choose which of these resources to include or exclude\. 

**Discovering scalable resources using a CloudFormation stack**  
When you use CloudFormation, you work with stacks to provision resources\. All of the resources in a stack are defined by the stack's template\. Your scaling plan adds an orchestration layer on top of the stack that makes it easier to configure scaling for multiple resources\. Without a scaling plan, you would need to set up scaling for each scalable resource individually\. This means figuring out the order for provisioning resources and scaling policies, and understanding the subtleties of how these dependencies work\. 

In the AWS Auto Scaling console, you can select an existing stack to scan it for resources that can be configured for automatic scaling\. AWS Auto Scaling only finds resources that are defined in the selected stack\. It does not traverse through nested stacks\. 

For your ECS services to be discoverable in a CloudFormation stack, the AWS Auto Scaling console must know which ECS cluster is running the service\. This requires that your ECS services be in the same CloudFormation stack as the ECS cluster that is running the service\. Otherwise, they must be part of the default cluster\. To be identified correctly, the ECS service name must also be unique across each of these ECS clusters\.

For more information about CloudFormation, see [What is AWS CloudFormation?](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/Welcome.html) in the *AWS CloudFormation User Guide*\. 

**Discovering scalable resources using tags**  
Tags provide metadata that can be used to discover related scalable resources in the AWS Auto Scaling console, using tag filters\.

Use tags to find any of the following resources: 
+ Aurora DB clusters
+ Auto Scaling groups
+ DynamoDB tables and global secondary indexes

When you search by more than one tag, each resource must have all of the listed tags to be discovered\. 

For more information about tagging, read the following documentation\.
+ Learn how to [tag Aurora clusters](https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/USER_Tagging.html) in the *Amazon Aurora User Guide*\.
+ Learn how to [tag Auto Scaling groups](https://docs.aws.amazon.com/autoscaling/ec2/userguide/autoscaling-tagging.html) in the *Amazon EC2 Auto Scaling User Guide*\.
+ Learn how to [tag DynamoDB resources](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/Tagging.html) in the *Amazon DynamoDB Developer Guide*\.
+ Learn more about best practices for [tagging AWS resources](https://docs.aws.amazon.com/general/latest/gr/aws_tagging.html) in the *AWS General Reference*\.