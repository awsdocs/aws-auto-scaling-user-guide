# Step 1: Find your scalable resources<a name="gs-select-application"></a>

In the getting started section, you create a scaling plan and get a hands\-on introduction to using AWS Auto Scaling through the AWS Management Console\. 

When you create a scaling plan from the console, AWS Auto Scaling helps you find your scalable resources as a first step\. There are three ways to locate the resources for a new scaling plan from the console:
+ You can choose an AWS CloudFormation stack for the AWS Auto Scaling console to use to automatically discover your scalable resources\. 
+ You can choose a set of tags for the AWS Auto Scaling console to use to automatically discover your scalable resources\.
+ You can choose one or more Amazon EC2 Auto Scaling groups to add to your scaling plan\.

If this is your first scaling plan, we recommend that you start by choosing the third option and create a sample scaling plan using an EC2 Auto Scaling group\.

## Prerequisites for your sample scaling plan<a name="gs-select-application-prereq"></a>

For a beginner\-friendly tutorial for using the console to create a scaling plan, we recommend that you start by creating an Auto Scaling group, and then create the scaling plan and add the Auto Scaling group\. By using an Auto Scaling group, you can enable the predictive scaling feature and the dynamic scaling feature\. You must enable both features to use the full set of features that are available in your scaling plan\.

Get started by creating an Auto Scaling group, if you do not already have one\. For more information, see [Getting started with Amazon EC2 Auto Scaling](https://docs.aws.amazon.com/autoscaling/ec2/userguide/GettingStartedTutorial.html) in the *Amazon EC2 Auto Scaling User Guide*\. If you create a new group, you can delete it afterwards\. As soon as the group is deleted, you stop incurring charges for the Amazon EC2 instances it ran\.

Configure your Auto Scaling group as follows to ensure the scaling plan works as expected:
+ In the launch template or launch configuration that you associate with the Auto Scaling group, enable detailed monitoring to get CloudWatch metric data for EC2 instances at a 1\-minute frequency\. Additional charges apply\. For more information, see [Configure monitoring for Auto Scaling instances](https://docs.aws.amazon.com/autoscaling/ec2/userguide/enable-as-instance-metrics.html) in the *Amazon EC2 Auto Scaling User Guide*\.
+ Enable Auto Scaling group metrics to get aggregated data for your group of instances in CloudWatch\. For more information, see [Enable Auto Scaling group metrics](https://docs.aws.amazon.com/autoscaling/ec2/userguide/as-instance-monitoring.html#as-enable-group-metrics) in the *Amazon EC2 Auto Scaling User Guide*\.
+ If you use a T2 or T3 instance type, use a launch template to configure your instances as `unlimited` so that they can sustain high CPU performance while you're testing\. Additional charges may apply\. For more information, see [Using an Auto Scaling group to launch a burstable performance instance as Unlimited](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/burstable-performance-instances-how-to.html#burstable-performance-instances-auto-scaling-grp) in the *Amazon EC2 User Guide for Linux Instances*\.

## Add your Auto Scaling group to your sample scaling plan<a name="gs-add-auto-scaling-group"></a>

Now that you've created your Auto Scaling group, you're ready to create your sample scaling plan using the AWS Management Console\. 

**To add an Auto Scaling group to a new scaling plan**

1. Open the AWS Auto Scaling console at [https://console\.aws\.amazon\.com/awsautoscaling/](https://console.aws.amazon.com/awsautoscaling/)\.

1. On the navigation bar at the top of the screen, choose the same Region that you used when you created your Auto Scaling group\. 

1. From the welcome page, choose **Get started**\.  
![\[AWS welcome screen\]](http://docs.aws.amazon.com/autoscaling/plans/userguide/images/aws-as-gs-welcome-screen.PNG)

1. On the **Find scalable resources** page, choose **Search by CloudFormation stack**, **Search by tag**, or **Choose EC2 Auto Scaling groups**\.
**Note**  
This tutorial assumes you're choosing an Auto Scaling group\. Later, you can use this same procedure to create a scaling plan using the **Search by CloudFormation stack** or **Search by tag** option\.
   + If you chose **Search by CloudFormation stack**, choose the AWS CloudFormation stack to use\.
   + If you chose **Search by tag**, then for each tag, choose a tag key from **Key** and tag values from **Value**\. To add tags, choose **Add another row**\. To remove tags, choose **Remove**\.
   + If you chose **Choose EC2 Auto Scaling groups**, then for **Auto Scaling groups**, choose one or more Auto Scaling groups\.  
![\[Choose EC2 Auto Scaling groups\]](http://docs.aws.amazon.com/autoscaling/plans/userguide/images/aws-as-gs-choose-asg.PNG)

1. Choose **Next** to add the Auto Scaling group to the scaling plan and to proceed to the next step\.

   If you chose the **Search by CloudFormation stack** or **Search by tag** option, then choosing **Next** makes the scalable resources associated with the stack or set of tags available to the scaling plan\. As you define your scaling plan, you can then choose which of these resources to include or exclude\. 

## Learn more about discovering your scalable resources<a name="gs-choose-discovery-method"></a>

If you have already created a sample scaling plan and would like to create more, the following information explains the scenarios for using a CloudFormation stack or a set of tags in more detail\. You can use this section to decide whether to choose the **Search by CloudFormation stack** or **Search by tag** option to discover your scalable resources when using the console to create your scaling plan\.

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

Tags can be assigned in a number of ways\. For more information, see [Tagging AWS resources](https://docs.aws.amazon.com/general/latest/gr/aws_tagging.html) in the *AWS General Reference*\.