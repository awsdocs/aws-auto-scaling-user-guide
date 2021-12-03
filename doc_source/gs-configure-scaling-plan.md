# Step 2: Specify the scaling strategy<a name="gs-configure-scaling-plan"></a>

Use the following procedure to specify scaling strategies for the resources that were found in the previous step\. 

For each type of resource, AWS Auto Scaling chooses the metric that is most commonly used for determining how much of the resource is in use at any given time\. You choose the most appropriate scaling strategy to optimize performance of your application based on this metric\. When you enable the dynamic scaling feature and the predictive scaling feature, the scaling strategy is shared between them\. For more information, see [How scaling plans work](how-it-works.md)\.

The following scaling strategies are available:
+ **Optimize for availability**—AWS Auto Scaling scales the resource out and in automatically to maintain resource utilization at 40 percent\. This option is useful when your application has urgent and sometimes unpredictable scaling needs\.
+ **Balance availability and cost**—AWS Auto Scaling scales the resource out and in automatically to maintain resource utilization at 50 percent\. This option helps you maintain high availability while also reducing costs\.
+ **Optimize for cost**—AWS Auto Scaling scales the resource out and in automatically to maintain resource utilization at 70 percent\. This option is useful for lowering costs if your application can handle having reduced buffer capacity when there are unexpected changes in demand\.

For example, the scaling plan configures your Auto Scaling group to add or remove Amazon EC2 instances based on how much of the CPU is used on average for all instances in the group\. You choose whether to optimize utilization for availability, cost, or a combination of the two by changing the scaling strategy\. 

Alternatively, you can configure a custom strategy if an existing strategy doesn't meet your needs\. With a custom strategy, you can change the target utilization value, choose a different metric, or both\. 

**Important**  
For the introductory tutorial, complete only the first step of the following procedure and then choose **Next** to continue\. 

**To specify a scaling strategy**

1. On the **Specify scaling strategy** page, for **Scaling plan details**, **Name**, enter a name for your scaling plan\. The name of your scaling plan must be unique within your set of scaling plans for the Region\. It can have a maximum of 128 characters, and it must not contain pipes "\|", forward slashes "/", or colons ":"\.

1. All included resources are listed by resource type\. For **Auto Scaling groups**, do the following:  
![\[Choose EC2 Auto Scaling groups\]](http://docs.aws.amazon.com/autoscaling/plans/userguide/images/aws-as-gs-choose-scaling-strategy.PNG)

   1. Skip this step to use the default scaling strategy and metrics\. To use a different scaling strategy or metrics instead, proceed with the following steps:

      1. For the **Scaling strategy**, choose the desired scaling strategy\. 

         For the introductory tutorial, make sure to choose **Optimize for availability**\. This specifies that the average CPU utilization of your Auto Scaling group will be maintained at 40 percent\.

      1. If you chose **Custom**, expand the **Configuration details** to choose the desired metrics and target value\. 
         + For **Scaling metric**, choose the desired scaling metric\.
         + For **Target value**, choose the desired target value, such as the target utilization or the target throughput during any one\-minute interval\. 
         + For **Load metric** \[Auto Scaling groups only\], choose the desired load metric to use for predictive scaling\. 
         + Select **Replace external scaling policies** to specify that AWS Auto Scaling can delete scaling policies previously created from outside of the scaling plan \(such as from other consoles\) and replace them with new target tracking scaling policies created by the scaling plan\.

   1. \(Optional\) By default, predictive scaling is enabled for Auto Scaling groups\. To turn off predictive scaling for the Auto Scaling groups, clear **Enable predictive scaling**\. 

   1. \(Optional\) By default, dynamic scaling is enabled for each resource type\. To turn off dynamic scaling for the resource type, clear **Enable dynamic scaling**\. 

   1. \(Optional\) By default, when you specify an application source from which multiple scalable resources are discovered, all resource types are automatically included in your scaling plan\. To omit a type of resource from your scaling plan, clear **Include in scaling plan**\.

1. \(Optional\) To specify a scaling strategy for another resource type, repeat the preceding steps\.

1. When you are finished, choose **Next** to continue with the scaling plan creation process\.