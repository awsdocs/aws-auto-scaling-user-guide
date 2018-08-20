# Getting Started with AWS Auto Scaling<a name="auto-scaling-getting-started"></a>

This tutorial provides a hands\-on introduction to AWS Auto Scaling through the AWS Management Console, a web\-based interface\. To create your first scaling plan, complete the following steps\.

**Topics**
+ [Requirements](#gs-requirements)
+ [Step 1: Search for Your Scalable Resources](#gs-select-application)
+ [Step 2: Configure Your Scaling Plan](#gs-configure-scaling-plan)
+ [Step 3: Create Your Scaling Plan](#gs-create-scaling-plan)
+ [Step 4: Delete Your Scaling Plan \(Optional\)](#gs-delete-scaling-plan)

## Requirements<a name="gs-requirements"></a>

AWS Auto Scaling uses an application source to discover the AWS resources that power your application\. You can use a AWS CloudFormation stack or a set of tags as an application source\. You need the name of your CloudFormation stack or a set of tags before you can create a scaling plan\.

You can create one scaling plan per application source and add each scalable resource to one scaling plan\.

## Step 1: Search for Your Scalable Resources<a name="gs-select-application"></a>

Use one of the following procedures to specify the application source for your scalable resources\.

**To specify a CloudFormation stack as the application source**

1. Open the AWS Auto Scaling console at [https://console\.aws\.amazon\.com/awsautoscaling/](https://console.aws.amazon.com/awsautoscaling/)\. From the welcome page, choose **Get started**\.

1. Select **Search by CloudFormation stack**\.

1. Select your AWS CloudFormation stack and choose **Next**\.

**To specify a set of tags as the application source**

1. Open the AWS Auto Scaling console at [https://console\.aws\.amazon\.com/awsautoscaling/](https://console.aws.amazon.com/awsautoscaling/)\. From the welcome page, choose **Get started**\.

1. Select **Search by tag**\.

1. For each tag, select a tag key from **Key** and tag values from **Value**\. To add tags, choose **Add another row**\. To remove tags, choose **Remove**\.

1. When you are finished specifying tags, choose **Next**\.

## Step 2: Configure Your Scaling Plan<a name="gs-configure-scaling-plan"></a>

On the **Configure scaling plan** page, for **Scaling plan details**, **Name**, type a name for your scaling plan\. For each type of scalable resource, select a strategy\. To omit a type of scalable resource from your scaling plan, clear **Include in scaling plan**\. When you are finished, choose **Next**\.

## Step 3: Create Your Scaling Plan<a name="gs-create-scaling-plan"></a>

On the **Review and create** page, choose **Create scaling plan**\.

## Step 4: Delete Your Scaling Plan \(Optional\)<a name="gs-delete-scaling-plan"></a>

When you are finished with a scaling plan, you can delete it\. Deleting a scaling plan deletes the target tracking policies that AWS Auto Scaling created on your behalf\. Deleting a scaling plan does not delete your AWS CloudFormation stack or the scalable resources\.

**To delete a scaling plan**

1. Open the AWS Auto Scaling console at [https://console\.aws\.amazon\.com/awsautoscaling/](https://console.aws.amazon.com/awsautoscaling/)\.

1. On the **Scaling plans** page, select the scaling plan and choose **Delete**\.

1. When prompted for confirmation, choose **Delete**