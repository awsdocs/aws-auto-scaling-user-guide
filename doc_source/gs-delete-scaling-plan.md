# Delete Your Scaling Plan<a name="gs-delete-scaling-plan"></a>

After you have completed the getting started tutorial, you may choose to keep your scaling plan\. However, if you are not actively using your scaling plan, you should consider deleting it so that your account does not incur unnecessary charges\. 

Deleting a scaling plan deletes the target tracking scaling policies, their associated CloudWatch alarms, and the scheduled scaling actions that AWS Auto Scaling created on your behalf\. 

Deleting a scaling plan does not delete your AWS CloudFormation stack or the scalable resources\. 

**To delete a scaling plan**

1. Open the AWS Auto Scaling console at [https://console\.aws\.amazon\.com/awsautoscaling/](https://console.aws.amazon.com/awsautoscaling/)\.

1. On the **Scaling plans** page, select the scaling plan and choose **Delete**\.

1. When prompted for confirmation, choose **Delete**\.

After you delete your scaling plan, your resources do not revert to their original capacity\. For example, if your Auto Scaling group is scaled to 10 instances when you delete the scaling plan, your group is still scaled to 10 instances after the scaling plan is deleted\. 