# Getting Started with AWS Auto Scaling<a name="auto-scaling-getting-started"></a>

This section describes the steps to begin using AWS Auto Scaling\. You use the AWS Management Console to create your first scaling plan, and learn the basics of creating scaling plans with predictive scaling and dynamic scaling enabled\. 

Before you create a scaling plan for use with your application, review your application thoroughly as it runs in the AWS Cloud\. Take note of the following: 
+ How long it takes to launch and configure a server\.
+ Whether you have existing scaling policies created from other consoles\.
+ What metrics have the most relevance to your application's performance\. 
+ The target utilization that makes sense for each scalable resource in your application based on the resource as a whole, for example, the full Amazon EC2 Auto Scaling group instead of individual instances\. 
+ Whether the metric history is sufficiently long to use with predictive scaling \(if using newly created Amazon EC2 Auto Scaling groups\)\. In general, having a full 14 days of historical data translates into more accurate forecasts\. The minimum is 24 hours\.

The better you understand your application, the more effective you can make your scaling plan\. 

**Topics**
+ [Best Practices and Considerations](#gs-considerations)
+ [Step 1: Find Your Scalable Resources](gs-select-application.md)
+ [Step 2: Specify the Scaling Strategy](gs-configure-scaling-plan.md)
+ [Step 3: Configure Advanced Settings \(Optional\)](gs-specify-custom-settings.md)
+ [Step 4: Create Your Scaling Plan](gs-create-scaling-plan.md)
+ [Step 5: Clean Up](gs-delete-scaling-plan.md)
+ [Getting Started with Customized Metrics](gs-customized-metric-specification.md)

## Best Practices and Considerations<a name="gs-considerations"></a>

Keep the following best practices and considerations in mind when you use AWS Auto Scaling:
+ Wherever possible, you should scale on Amazon EC2 instance metrics with a 1\-minute frequency because that ensures a faster response to utilization changes\. Scaling on metrics with a 5\-minute frequency can result in a slower response time and scaling on stale metric data\. By default, EC2 instances are enabled for basic monitoring, which means metric data for instances is available at 5\-minute intervals\. For an additional charge, you can enable detailed monitoring to get metric data for instances at a 1\-minute frequency\. For more information, see [Configure Monitoring for Auto Scaling Instances](https://docs.aws.amazon.com/autoscaling/ec2/userguide/as-instance-monitoring.html#enable-as-instance-metrics) in the *Amazon EC2 Auto Scaling User Guide*\.
+ We also recommend that you enable Auto Scaling group metrics\. Otherwise, actual capacity data is not shown in the capacity forecast graphs that are available on completion of the Create Scaling Plan wizard\. To enable Auto Scaling group metrics, open an Auto Scaling group in the Amazon EC2 console, and from the **Monitoring** tab, choose **Enable Group Metrics Collection**\. These metrics describe the group rather than any of its instances\. For more information, see [Enable Auto Scaling Group Metrics](https://docs.aws.amazon.com/autoscaling/ec2/userguide/as-instance-monitoring.html#as-enable-group-metrics) in the *Amazon EC2 Auto Scaling User Guide*\.
+ Check which instance type your Auto Scaling group uses\. Amazon EC2 instances with burstable performance, which are T3 and T2 instances, are designed to provide a baseline level of CPU performance with the ability to burst to a higher level when required by your workload\. Depending on the target utilization specified by the scaling plan, you could run the risk of exceeding the baseline and then running out of CPU credits, which limits performance\. For more information, see [CPU Credits and Baseline Performance for Burstable Performance Instances](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/burstable-credits-baseline-concepts.html) and [Using an Auto Scaling Group to Launch a Burstable Performance Instance as Unlimited](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/burstable-performance-instances-how-to.html#burstable-performance-instances-auto-scaling-grp) in the *Amazon EC2 User Guide for Linux Instances*\.
+ Predictive scaling uses workload forecasts to schedule capacity in the future\. The quality of the forecasts varies based on how cyclical the workload is and the applicability of the trained forecasting model\. Predictive scaling can be run in forecast only mode to assess the quality of the forecasts\. You can set the predictive scaling mode to **Forecast only** in the scaling plan's advanced settings\. 
+ If you choose to specify diﬀerent metrics for predictive scaling, you must ensure that the scaling metric and load metric are strongly correlated\. The metric value must increase and decrease proportionally to the number of instances in the Auto Scaling group\. This ensures that the metric data can be used to proportionally scale out or in the number of instances\. For example, the load metric is total request count and the scaling metric is average CPU utilization\. If the total request count increases by 50 percent, the average CPU utilization should also increase by 50 percent, provided that capacity remains unchanged\.
+ You can create scaling policies from various AWS consoles, but AWS Auto Scaling does not overwrite these other scaling policies or create new ones by default\. You can optionally replace the existing scaling policies with target tracking scaling policies created from the AWS Auto Scaling console by enabling the **Replace external scaling policies** setting in the scaling plan\. 
+ Before creating your scaling plan, you should delete any previously scheduled scaling actions that you no longer need by accessing the consoles they were created from\. AWS Auto Scaling does not create a predictive scaling action that overlaps an existing scheduled scaling action\.
+ Your customized settings for minimum and maximum capacity, along with other settings used for dynamic scaling, show up in other consoles\. However, we recommend that after you create a scaling plan, you do not modify these settings from other consoles because your scaling plan does not receive the updates from other consoles\. 
+ Your scaling plan can contain resources from multiple services, but each resource can be in only one scaling plan at a time\. 