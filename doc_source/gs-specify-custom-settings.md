# Step 3: Configure Advanced Settings \(Optional\)<a name="gs-specify-custom-settings"></a>

Now that you have specified the scaling strategy to use for each resource type, you may choose to customize any of the default settings on a per resource basis\. In most cases, however, the default settings should be optimal, with the possible exception of the values for minimum capacity and maximum capacity, which should be carefully adjusted\.

Skip this procedure if you would like to keep the default settings\. You can change these settings anytime by editing the scaling plan\.

**To specify custom settings**

1. On the **Specify custom settings** page, expand the section for the resource type to see, and then select any number of resources from the list\. This displays the names of multiple sections containing various settings that you can customize\.

1. \(Optional\) To omit the selected resources from your scaling plan, clear **Include in scaling plan**\.

1. Under **General settings**, you can optionally configure the following general settings\. If you are using dynamic scaling and predictive scaling, these settings are shared between them\. 
   + **Scaling strategy**—Allows you to optimize for availability, for cost, or a balance of both, or specify a custom strategy\.
   + **Enable dynamic scaling**—If this setting is disabled, the scaling plan does not create any target tracking scaling policies for the selected resources\.
   + **Enable predictive scaling**—\[Auto Scaling groups only\] If this setting is disabled, it disables predictive scaling for the selected groups\.
   + **Scaling metric**—Specifies the scaling metric to use\. Alternatively, if you choose **Custom**, you can specify a customized scaling metric to use instead of the scaling metrics that are available in the console\. 
   + **Target value**—Specifies the target utilization value to use\.
   + **Load metric**—\[Auto Scaling groups only\] Specifies the load metric to use\. Alternatively, if you choose **Custom**, you can specify a customized load metric to use instead of the load metrics that are available in the console\. 
   + **Minimum capacity**—Specifies the minimum capacity for the resource\. When AWS Auto Scaling scales in, it does not remove capacity below this value\. 
   + **Maximum capacity**—Specifies the maximum value to scale to in response to a change in demand\. When AWS Auto Scaling scales out, it does not add capacity above this value\. 

1. Under **Dynamic scaling settings**, you can optionally customize the following settings\.
   + **Replace external scaling policies**—If this setting is disabled, it keeps existing scaling policies created from outside of the scaling plan and does not create new ones\.
   + **Disable scale\-in**—If this setting is disabled, the target tracking scaling policy can add *and* remove capacity as traffic changes occur\.
   + **Cooldown**—Creates scale\-out and scale\-in cooldown periods\. Cooldown periods are the amount of time after a scale\-in or scale\-out activity completes before another activity can start\. The intention is to give newly provisioned resources time to start handling demand before triggering a new scaling action\. This setting is not available if the resource is an Auto Scaling group\. For more information, see [Cooldown Period](https://docs.aws.amazon.com/autoscaling/application/userguide/application-auto-scaling-target-tracking.html#target-tracking-cooldown) in the *Application Auto Scaling User Guide*\. 
   + **Instance warmup**—\[Auto Scaling groups only\] Allows you to control the amount of time until a newly launched instance can contribute to the CloudWatch metrics\. For more information, see [Instance Warmup](https://docs.aws.amazon.com/autoscaling/ec2/userguide/as-scaling-target-tracking.html#as-target-tracking-scaling-warmup) in the *Amazon EC2 Auto Scaling User Guide*\.

1. Under **Predictive scaling settings** \[Auto Scaling groups only\], you can optionally customize the following settings\.
   + **Predictive scaling mode**—Specifies the scaling mode\. The default is **Forecast and scale**\. If you change it to **Forecast only**, the scaling plan forecasts future capacity but doesn't create any scheduled scaling actions\. 
   + **Max capacity behavior**—Controls whether the selected resources can scale up above the maximum capacity when the forecast capacity is close to or exceeds the currently specified maximum capacity\. The default is **Set forecast capacity to max capacity**, which enforces the maximum capacity\. If you change it to **Set max capacity to forecast capacity**, the scaling plan may set a higher maximum capacity for the resource when the forecast capacity approaches or exceeds the maximum capacity\. 
   + **Pre\-launch instances**—Adjusts the scheduled scaling actions to run earlier when scaling out\. For example, the forecast says to add capacity at 10:00 AM, and the buffer time is 5 minutes\. The run time of the corresponding scheduled scaling action is then 9:55 AM\. This is helpful for Auto Scaling groups, where it can take a few minutes from the time an instance launches until it comes in service\. The actual time can vary as it depends on several factors, such as the size of the instance and whether there are startup scripts to complete\. 

1. When you are finished customizing settings, choose **Next**\.
**Note**  
To revert any of your changes, select the resources and choose **Revert to original**\. This resets the selected resources to their last known state within the scaling plan\.