# Step 2: Specify the Scaling Strategy<a name="gs-configure-scaling-plan"></a>

Use the following procedure to specify scaling strategies for the resources discovered in the previous step\.

For each type of resource, AWS Auto Scaling chooses the most commonly used metric as the default scaling metric\. You determine the most appropriate scaling strategy to optimize performance of your application based on this metric\. For example, the scaling plan configures your Auto Scaling group to add or remove Amazon EC2 instances based on CPU utilization\. You optimize these resources for availability, cost, or a combination of the two by changing the scaling strategy\. Alternatively, you may configure a custom strategy to use different metrics or change the target utilization\. 

**To specify scaling strategies**

1. On the **Configure scaling plan** page, for **Scaling plan details**, **Name**, type a name for your scaling plan\. 

1. \(Optional\) To omit a type of resource from your scaling plan, clear **Include in scaling plan**\.

1. For each type of resource, choose one of the following default strategies to use: 
   + **Optimize for availability**: Specifies a target utilization of 40 percent for the most commonly used scaling metric for that resource type\.
   + **Balance availability and cost**: Specifies a target utilization of 50 percent for the most commonly used scaling metric for that resource type\.
   + **Optimize for cost**: Specifies a target utilization of 70 percent for the most commonly used scaling metric for that resource type\.

   \- OR \- 

   Choose **Custom** to optionally increase or decrease the target utilization or choose different metrics to meet your application needs\. However, the default strategies are fine for this tutorial\.

1. If you chose **Custom** in the previous step, choose your custom settings under **Configuration details**\. Here you can find the list of metrics available to you \(if any\) and related graphs based on data from CloudWatch\. The recent metric history is the main focus of the graphs\. 
   + For **Scaling metric**, choose the desired scaling metric\. 
   + For **Target value**, choose the desired target utilization value\. 
   + For **Load metric** \[Auto Scaling groups only\], choose an appropriate load metric to use for predictive scaling\. 
   + For **Replace external scaling policies**, choose whether to delete scaling policies created from outside of the scaling plan \(such as from other consoles\) and replace them with new target tracking scaling policies created by the scaling plan\.

1. \(Optional\) By default, predictive scaling is enabled for your Auto Scaling groups\. To disable predictive scaling for your Auto Scaling groups, clear **Enable predictive scaling**\. 

1. \(Optional\) By default, dynamic scaling is enabled for each resource type\. To disable dynamic scaling for a type of resources, clear **Enable dynamic scaling**\. 

1. When you are finished, choose **Next**\.