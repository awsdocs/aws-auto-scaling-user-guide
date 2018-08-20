# What Is AWS Auto Scaling?<a name="what-is-aws-auto-scaling"></a>

AWS Auto Scaling enables you to quickly discover the scalable AWS resources that are part of your application and configure dynamic scaling in a matter of minutes\. The AWS Auto Scaling console provides a single user interface to use the automatic scaling features of multiple AWS services\. It also offers recommendations to configure scaling for the scalable resources in your application\.

For more information about the benefits of this service, see the [AWS Auto Scaling FAQs](https://aws.amazon.com/autoscaling/faqs/)\. 

## Scalable Resources<a name="scalable-resources"></a>

Use AWS Auto Scaling to automatically scale the following resources that support your application:
+ Amazon EC2 Auto Scaling groups
+ Aurora DB clusters
+ DynamoDB global secondary indexes
+ DynamoDB tables
+ ECS services
+ Spot Fleet requests

## How AWS Auto Scaling Works<a name="how-it-works"></a>

With AWS Auto Scaling, you create a scaling plan with a set of instructions used to configure dynamic scaling for the scalable resources in your application\. AWS Auto Scaling creates target tracking scaling policies for the scalable resources in your scaling plan\. Target tracking scaling policies adjust the capacity of your scalable resource as required to maintain resource utilization at the target value that you specified\. For more information, see [Target Tracking Scaling Policies](http://docs.aws.amazon.com/autoscaling/application/userguide/application-auto-scaling-target-tracking.html) in the *Application Auto Scaling User Guide*\.

You can create one scaling plan per application source \(an AWS CloudFormation stack or a set of tags\)\. You can add each scalable resource to one scaling plan\. If you have already configured scaling policies for a scalable resource in your application, AWS Auto Scaling keeps the existing scaling policies instead of creating additional scaling policies for the resource\.

## How to Get Started<a name="how-to-get-started"></a>

To get started, create a scaling plan\. For more information, see [Getting Started with AWS Auto Scaling](auto-scaling-getting-started.md)\.

To see the regional availability for AWS Auto Scaling, see the [AWS Region Table](https://aws.amazon.com/about-aws/global-infrastructure/regional-product-services/)\.

## Related Services<a name="related-services"></a>

To learn more about AWS CloudFormation, see the [AWS CloudFormation User Guide](http://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/)\.

To monitor the calls made to the API for your account, including calls made by the AWS Management Console, command line tools, and other services, use AWS CloudTrail\. For more information, see the [AWS CloudTrail User Guide](http://docs.aws.amazon.com/awscloudtrail/latest/userguide/)\.

For more information on scaling your fleet of Amazon EC2 instances, see the [Amazon EC2 Auto Scaling User Guide](http://docs.aws.amazon.com/autoscaling/ec2/userguide/)\. 

To configure automatic scaling for resources beyond EC2, see the [Application Auto Scaling User Guide](http://docs.aws.amazon.com/autoscaling/application/userguide/)\. 