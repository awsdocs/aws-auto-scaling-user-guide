# Getting Started with AWS Auto Scaling<a name="auto-scaling-getting-started"></a>

This tutorial provides a hands\-on introduction to AWS Auto Scaling through the AWS Management Console, a web\-based interface\. To create your first scaling plan, complete the following steps\.


+ [Requirements](#gs-requirements)
+ [Step 1: Select Your Application](#gs-select-application)
+ [Step 2: Configure Your Scaling Plan](#gs-configure-scaling-plan)
+ [Step 3: Create Your Scaling Plan](#gs-create-scaling-plan)
+ [Step 4: Delete Your Scaling Plan \(Optional\)](#gs-delete-scaling-plan)

## Requirements<a name="gs-requirements"></a>

AWS Auto Scaling uses a AWS CloudFormation stack to discover the AWS resources that power your application\. You need the name of your AWS CloudFormation stack before you can create a scaling plan\.

You can create one scaling plan per application and add each scalable resource to one scaling plan\.

## Step 1: Select Your Application<a name="gs-select-application"></a>

Open the AWS Auto Scaling console at [https://console\.aws\.amazon\.com/awsautoscaling/](https://console.aws.amazon.com/awsautoscaling/)\. From the welcome page, choose **Get started**\. Select your AWS CloudFormation stack and choose **Next**\.

## Step 2: Configure Your Scaling Plan<a name="gs-configure-scaling-plan"></a>

On the **Configure scaling plan** page, for **Scaling plan details**, type a name for your scaling plan\. For each type of scalable resource, select a strategy and a metric\. To omit a type of scalable resource from your scaling plan, clear **Include in plan**\. When you are finished, choose **Next**\.

## Step 3: Create Your Scaling Plan<a name="gs-create-scaling-plan"></a>

Review your scaling plan and choose **Create scaling plan**\.

## Step 4: Delete Your Scaling Plan \(Optional\)<a name="gs-delete-scaling-plan"></a>

When you are finished with a scaling plan, you can delete it\. Deleting a scaling plan deletes the target tracking policies that AWS Auto Scaling created on your behalf\. Deleting a scaling plan does not delete your AWS CloudFormation stack or your application resources\.