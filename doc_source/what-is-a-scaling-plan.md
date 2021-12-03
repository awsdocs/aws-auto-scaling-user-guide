# What is a scaling plan?<a name="what-is-a-scaling-plan"></a>

Use a *scaling plan* to configure auto scaling for related or associated scalable resources in a matter of minutes\. For example, you can use tags to group resources in categories such as production, testing, or development\. Then, you can search for and set up scaling plans for scalable resources that belong to each category\. Or, if your cloud infrastructure includes AWS CloudFormation, you can define stack templates to use to create collections of resources\. Then, create a scaling plan for the scalable resources that belong to each stack\.

## Supported resources<a name="scalable-resources"></a>

AWS Auto Scaling supports the use of scaling plans for the following services and resources:
+ **Amazon Aurora** – Increase or decrease the number of Aurora read replicas that are provisioned for an Aurora DB cluster\. 
+ **Amazon EC2 Auto Scaling** – Launch or terminate EC2 instances by increasing or decreasing the desired capacity of an Auto Scaling group\.
+ **Amazon Elastic Container Service** – Increase or decrease the desired task count in Amazon ECS\.
+ **Amazon DynamoDB** – Increase or decrease the provisioned read and write capacity of a DynamoDB table or a global secondary index\.
+ **Spot Fleet** – Launch or terminate EC2 instances by increasing or decreasing the target capacity of a Spot Fleet\.

## Scaling plan features and benefits<a name="features"></a>

Scaling plans provide the following features and benefits:
+ **Resource discovery** – AWS Auto Scaling provides automatic resource discovery to help find resources in your application that can be scaled\.
+ **Dynamic scaling** – Scaling plans use the Amazon EC2 Auto Scaling and Application Auto Scaling services to adjust capacity of scalable resources to handle changes in traffic or workload\. Dynamic scaling metrics can be standard utilization or throughput metrics, or custom metrics\.
+ **Built\-in scaling recommendations** – AWS Auto Scaling provides scaling strategies with recommendations that you can use to optimize for performance, costs, or a balance between the two\.
+ **Predictive scaling** – Scaling plans also support predictive scaling for Auto Scaling groups\. This helps to scale your Amazon EC2 capacity faster when there are regularly occurring spikes\. 

**Important**  
If you have been using scaling plans only for configuring predictive scaling for your Auto Scaling groups, we strongly recommend that you use the predictive scaling policies of Auto Scaling groups instead\. This recently introduced option offers enhanced features, such as using metrics aggregations to create new custom metrics or retain historical metric data across blue/green deployments\. For more information, see [Predictive scaling for Amazon EC2 Auto Scaling](https://docs.aws.amazon.com/autoscaling/ec2/userguide/ec2-auto-scaling-predictive-scaling.html) in the *Amazon EC2 Auto Scaling User Guide*\.

## How to get started<a name="how-to-get-started"></a>

Use the following resources to help you create and use a scaling plan:
+ [How scaling plans work](how-it-works.md)
+ [Best practices for scaling plans](best-practices.md)
+ [Getting started with scaling plans](getting-started.md)

## Work with scaling plans<a name="scaling-plan-interfaces"></a>

You can create, access, and manage your scaling plans using any of the following interfaces:
+ **AWS Management Console** – Provides a web interface that you can use to access your scaling plans\.
+ **AWS Command Line Interface \(AWS CLI\)** – Provides commands for a broad set of AWS services, and is supported on Windows, macOS, and Linux\. For more information, see [AWS Command Line Interface](http://aws.amazon.com/cli/)\.
+ **AWS SDKs** – Provides language\-specific API operations and takes care of many of the connection details, such as calculating signatures, handling request retries, and handling errors\. For more information, see [AWS SDKs](http://aws.amazon.com/tools/#SDKs)\.
+ **Query API** – Provides low\-level API actions that you call using HTTPS requests\. Using the Query API is the most direct way to access AWS services\. However, it requires your application to handle low\-level details such as generating the hash to sign the request, and handling errors\. For more information, see the [AWS Auto Scaling API Reference](https://docs.aws.amazon.com/autoscaling/plans/APIReference/)\.

To connect programmatically to an AWS service, you use an endpoint\. For information about endpoints for calls to AWS Auto Scaling, see [AWS Auto Scaling endpoints and quotas](https://docs.aws.amazon.com/general/latest/gr/autoscaling_region.html) in the *AWS General Reference*\. This page also shows the Regional availability of scaling plans\.

## Pricing<a name="pricing"></a>

All scaling plan features are enabled for your use\. The features are provided at no additional charge beyond the service fees for CloudWatch and the other AWS Cloud resources that you use\.