# Getting started with AWS Auto Scaling<a name="auto-scaling-getting-started"></a>

This section describes the steps to begin using AWS Auto Scaling\. You can use the AWS Management Console to create your first scaling plan\. Then you learn the basics of creating scaling plans with predictive scaling and dynamic scaling enabled\. 

Before you create a scaling plan for use with your application, review your application thoroughly as it runs in the AWS Cloud\. Take note of the following: 
+ Whether you have existing scaling policies created from other consoles\. You can replace the existing scaling policies, or you can keep them \(without being allowed to make any changes to their values\) when you create your scaling plan\.
+ The target utilization that makes sense for each scalable resource in your application based on the resource as a whole\. For example, the amount of CPU that the EC2 instances in an Auto Scaling group are expected to use compared to their available CPU\. Or for a service like DynamoDB that uses a provisioned throughput model, the amount of read and write activity that a table or index is expected to use compared to the available throughput\. In other words, the ratio of consumed to provisioned capacity\. You can change the target utilization at any time after you you've created your scaling plan\.
+ How long it takes to launch and configure a server\. Knowing this will help you configure a window for each EC2 instance to warm up after launching to ensure that we don't launch a new server while the previous one is still launching\.
+ Whether the metric history is sufficiently long to use with predictive scaling \(if using newly created Auto Scaling groups\)\. In general, having a full 14 days of historical data translates into more accurate forecasts\. The minimum is 24 hours\.

The better you understand your application, the more effective you can make your scaling plan\. 

**Topics**
+ [Step 1: Find your scalable resources](gs-select-application.md)
+ [Step 2: Specify the scaling strategy](gs-configure-scaling-plan.md)
+ [Step 3: Configure advanced settings \(optional\)](gs-specify-custom-settings.md)
+ [Step 4: Create your scaling plan](gs-create-scaling-plan.md)
+ [Step 5: Clean up](gs-delete-scaling-plan.md)
+ [Step 6: Next steps](gs-next-steps.md)