# Step 1: Find Your Scalable Resources<a name="gs-select-application"></a>

In the Getting Started section, you create a scaling plan and get a hands\-on introduction to using AWS Auto Scaling through the AWS Management Console\. The Getting Started walkthrough focuses on the most straightforward configuration for a scaling plan\. It also describes the Create Scaling Plan wizard and all of the ways that you can use it to configure a scaling plan\. 

The first step in the wizard asks you to find your scalable resources\. There are two ways to locate the resources for a new scaling plan:
+ You specify an application source \(an AWS CloudFormation stack or a set of tags\) for AWS Auto Scaling to use to automatically discover your scalable resources\. As you define your scaling plan, you can then choose which of these resources to include or exclude\. 
+ Alternatively, you can choose one or more Auto Scaling groups of Amazon EC2 instances to use in your scaling plan\.

For your scalable resources from multiple services to be discoverable, you must have an AWS CloudFormation stack or a set of tags\. When you use a CloudFormation stack, AWS Auto Scaling only finds resources that are defined in the selected stack\. It does not traverse through nested stacks\.

For your ECS services to be discoverable in a CloudFormation stack, AWS Auto Scaling needs to know which ECS cluster is running the service\. This requires that your ECS services be in the same CloudFormation stack as the ECS cluster that is running the service\. Otherwise, they must be part of the default cluster\. To be identified correctly, the service name must also be unique across each of these ECS clusters\.

Tags can be assigned in a number of ways\. Use the console for each individual service by accessing the **Tags** tab on the relevant resource screen, or use the [Tag Editor](https://docs.aws.amazon.com/awsconsolehelpdocs/latest/gsg/tag-editor.html)\. Currently, ECS services and Spot Fleet requests cannot be discovered using tags\. 

**Important**  
For a beginner\-friendly tutorial, you can start more simply by choosing an Auto Scaling group to add to your scaling plan\. By using an Auto Scaling group, you can enable the predictive scaling feature and the dynamic scaling feature\. You must enable both features to use the full set of advanced features that are available in your scaling plan\.

## Prerequisites<a name="gs-select-application-prereq"></a>

Before you begin, use the Amazon EC2 console to create a new Auto Scaling group by following the steps for [Creating an Auto Scaling Group Using a Launch Template](https://docs.aws.amazon.com/autoscaling/ec2/userguide/create-asg-launch-template.html) in the *Amazon EC2 Auto Scaling User Guide*\. You can choose any group, but let's use a new group for this tutorial, so that you can delete it afterwards\. As soon as the group is deleted, you stop incurring charges for the Amazon EC2 instances it ran\.

You can optionally configure your Auto Scaling group to ensure it performs optimally by following these guidelines:
+ Enable detailed monitoring to get metric data for individual instances at a 1\-minute frequency\. Additional charges apply\. For more information, see [Configure Monitoring for Auto Scaling Instances](https://docs.aws.amazon.com/autoscaling/ec2/userguide/as-instance-monitoring.html#enable-as-instance-metrics) in the *Amazon EC2 Auto Scaling User Guide*\.
+ Enable Auto Scaling group metrics to get aggregated data for your group of instances at a 1\-minute frequency\. For more information, see [Enable Auto Scaling Group Metrics](https://docs.aws.amazon.com/autoscaling/ec2/userguide/as-instance-monitoring.html#as-enable-group-metrics) in the *Amazon EC2 Auto Scaling User Guide*\.
+ If you use a T2 or T3 instance type, configure your instances as `unlimited` so that they can sustain high CPU performance as required in this tutorial\. Additional charges may apply\. For more information, see [Using an Auto Scaling Group to Launch a Burstable Performance Instance as Unlimited](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/burstable-performance-instances-how-to.html#burstable-performance-instances-auto-scaling-grp) in the *Amazon EC2 User Guide for Linux Instances*\.

You need IAM permissions to create a scaling plan and enable predictive scaling\. For information about the required IAM permissions, see the [Example Policies](auth-and-access-control.md#aws-auto-scaling-example-policies) in this guide\.

## Discovering or Choosing Your Scalable Resources<a name="gs-choose-discovery-method"></a>

Complete the following procedure to find your scalable resources\. 

**Note**  
For this tutorial, choose **Choose EC2 Auto Scaling groups** and then choose the Auto Scaling group that you created in the previous section\.

**To find scalable resources to add to your scaling plan**

1. Open the AWS Auto Scaling console at [https://console\.aws\.amazon\.com/awsautoscaling/](https://console.aws.amazon.com/awsautoscaling/)\.

1. On the navigation bar at the top of the screen, choose the same Region that you used when you created your scalable resources\. 
**Note**  
You can choose any Region that supports AWS Auto Scaling\. For more information, see the [AWS Region Table](https://aws.amazon.com/about-aws/global-infrastructure/regional-product-services/)\.

1. From the welcome page, choose **Get started**\.

1. On the **Find scalable resources** page, choose **Search by CloudFormation stack**, **Search by tag**, or **Choose EC2 Auto Scaling groups**\.
   + If you chose **Search by CloudFormation stack**, choose the AWS CloudFormation stack to use\.
   + If you chose **Search by tag**, then for each tag, choose a tag key from **Key** and tag values from **Value**\. To add tags, choose **Add another row**\. To remove tags, choose **Remove**\.
   + If you chose **Choose EC2 Auto Scaling groups**, then for **Auto Scaling groups**, choose one or more Auto Scaling groups\.

1. Choose **Next**\.