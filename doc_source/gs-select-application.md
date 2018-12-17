# Step 1: Find Your Scalable Resources<a name="gs-select-application"></a>

In this section, you create a scaling plan and get a hands\-on introduction to using AWS Auto Scaling through the AWS Management Console, a web\-based interface\. The getting started walkthrough focuses on the most straightforward configuration for a scaling plan to help you get an idea of how to use AWS Auto Scaling\. 

The first step is to choose a method for finding your scalable resources\. Searching lets you specify how AWS Auto Scaling discovers the scalable resources to add to your scaling plan\. As you define your scaling plan, you can then specify which resources to include or exclude\. Alternatively, you can choose specific Amazon EC2 Auto Scaling groups instead of searching for them\.

For your scalable resources from multiple services to be discoverable in the AWS Auto Scaling console, you need the name of your AWS CloudFormation stack or a set of tags\. Tags can be assigned in a number of different ways\. Use the console of individual services with the **Tags** tab on the relevant resource screen, or from the [Tag Editor](https://docs.aws.amazon.com/awsconsolehelpdocs/latest/gsg/tag-editor.html)\. Currently, ECS services and Spot Fleet requests cannot be discovered using tags\. 

To ensure that your ECS services are discoverable, AWS Auto Scaling needs to know which ECS cluster is running the service\. For AWS Auto Scaling to know this, your ECS services must be in the same CloudFormation stack as the ECS cluster that is running the service\. Otherwise, they must be part of the default cluster\. To be identified correctly, the service name must also be unique across each of these ECS clusters\.

Use one of the following procedures to find your scalable resources\. Keep in mind that each scalable resource can be added to only one scaling plan at a time\.

**To search by CloudFormation stack**

1. Open the AWS Auto Scaling console at [https://console\.aws\.amazon\.com/awsautoscaling/](https://console.aws.amazon.com/awsautoscaling/)\.

1. From the welcome page, choose **Get started**\.

1. Select **Search by CloudFormation stack**\.

1. Select your AWS CloudFormation stack and choose **Next**\.

**To search using a set of tags**

1. Open the AWS Auto Scaling console at [https://console\.aws\.amazon\.com/awsautoscaling/](https://console.aws.amazon.com/awsautoscaling/)\.

1. From the welcome page, choose **Get started**\.

1. Select **Search by tag**\.

1. For each tag, select a tag key from **Key** and tag values from **Value**\. To add tags, choose **Add another row**\. To remove tags, choose **Remove**\.

1. When you are finished specifying tags, choose **Next**\.

**To choose specific **Auto Scaling groups****

1. Open the AWS Auto Scaling console at [https://console\.aws\.amazon\.com/awsautoscaling/](https://console.aws.amazon.com/awsautoscaling/)\.

1. From the welcome page, choose **Get started**\.

1. Select **Choose EC2 Auto Scaling groups**\.

1. Choose one or more Auto Scaling groups from the list and choose **Next**\.