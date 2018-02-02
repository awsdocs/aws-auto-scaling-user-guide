# What Is AWS Auto Scaling?<a name="what-is-aws-auto-scaling"></a>

AWS Auto Scaling enables you to configure automatic scaling for the scalable AWS resources for your application in a matter of minutes\. AWS Auto Scaling uses the Auto Scaling and Application Auto Scaling services to configure scaling policies for your scalable AWS resources\.

For more information about the benefits of this service, see [AWS Auto Scaling](https://aws.amazon.com/autoscaling/)\.

## Scalable Resources<a name="scalable-resources"></a>

Use AWS Auto Scaling to automatically scale the following resources for your applications:

+ Aurora DB clusters

+ Auto Scaling groups

+ ECS services

+ DynamoDB global secondary indexes

+ DynamoDB tables

+ Spot Fleet requests

## How AWS Auto Scaling Works<a name="how-it-works"></a>

With AWS Auto Scaling, you create a scaling plan with a set of instructions used to configure dynamic scaling for the scalable resources in your application\. AWS Auto Scaling creates target tracking scaling policies for the scalable resources in your scaling plan\. Target tracking scaling policies adjust the capacity of your scalable resource as required to maintain resource utilization at the target value that you specified\. For more information, see [Target Tracking Scaling Policies](http://docs.aws.amazon.com/autoscaling/application/userguide/application-auto-scaling-target-tracking.html) in the *Application Auto Scaling User Guide*\.

You can create one scaling plan per application\. You can add each scalable resource to one scaling plan\. If you have already configured scaling policies for a scalable resource in your application, AWS Auto Scaling keeps the existing scaling policies instead of creating additional scaling policies for the resource\.

## How to Get Started<a name="how-to-get-started"></a>

To get started, create a scaling plan\. For more information, see [Getting Started with AWS Auto Scaling](auto-scaling-getting-started.md)\.