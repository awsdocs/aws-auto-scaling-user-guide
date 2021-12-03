# Scaling plans and interface VPC endpoints \(AWS PrivateLink\)<a name="scaling-plan-vpc-endpoints"></a>

You can establish a private connection between your scaling plans and other AWS services and endpoint services by creating an interface VPC endpoint\. You can use this connection to call the AWS Auto Scaling API from your VPC without sending traffic over the internet\. The endpoint provides reliable, scalable connectivity to the AWS Auto Scaling API\. It does this without requiring an internet gateway, NAT instance, or VPN connection\. 

Interface VPC endpoints are powered by AWS PrivateLink, a feature that enables private communication between AWS services using private IP addresses\. For more information, see [AWS PrivateLink](http://aws.amazon.com/privatelink)\.

## Create an interface VPC endpoint for scaling plans<a name="create-vpce-aws-as-api"></a>

You can create a VPC endpoint for AWS Auto Scaling \(scaling plans\) using either the Amazon VPC console or the AWS Command Line Interface \(AWS CLI\)\. Create an endpoint for AWS Auto Scaling using the following service name:
+ **com\.amazonaws\.*region*\.autoscaling\-plans** — Creates an endpoint for the AWS Auto Scaling API operations\.

For more information, see [Creating an interface endpoint](https://docs.aws.amazon.com/vpc/latest/userguide/vpce-interface.html#create-interface-endpoint) in the *Amazon VPC User Guide*\. 

Enable private DNS for the endpoint to make API requests to the supported service using its default DNS hostname \(for example, `autoscaling-plans.us-east-1.amazonaws.com`\)\. When creating an endpoint for AWS services, this setting is enabled by default\. For more information, see [Accessing a service through an interface endpoint](https://docs.aws.amazon.com/vpc/latest/userguide/vpce-interface.html#access-service-though-endpoint) in the *Amazon VPC User Guide*\. 

You do not need to change any AWS Auto Scaling settings\. AWS Auto Scaling API calls other AWS services using either service endpoints or private interface VPC endpoints, whichever are in use\. 

## Create a VPC endpoint policy for scaling plans<a name="create-vpce-policy-aws-as-api"></a>

You can attach a policy to your VPC endpoint to control access to the AWS Auto Scaling API\. The policy specifies:
+ The principal that can perform actions\.
+ The actions that can be performed\.
+ The resource on which the actions can be performed\.

The following example shows a VPC endpoint policy that denies everyone permission to delete a scaling plan through the endpoint\. The example policy also grants everyone permission to perform all other actions\.

```
{
   "Statement": [
        {
            "Action": "*",
            "Effect": "Allow",
            "Resource": "*",
            "Principal": "*"
        },
        {
            "Action": "autoscaling-plans:DeleteScalingPlan",
            "Effect": "Deny",
            "Resource": "*",
            "Principal": "*"
        }
    ]
}
```

For more information, see [Using VPC endpoint policies](https://docs.aws.amazon.com/vpc/latest/userguide/vpc-endpoints-access.html#vpc-endpoint-policies) in the *Amazon VPC User Guide*\.

## Endpoint migration<a name="upgrading-cli-sdk-aws-as-api"></a>

On November 22, 2019, we introduced `autoscaling-plans.region.amazonaws.com` as the new default DNS hostname and endpoint for calls to the AWS Auto Scaling API\. The new endpoint is compatible with the latest release of the AWS CLI and SDKs\. If you have not done so already, install the latest AWS CLI and SDKs to use the new endpoint\. To update the AWS CLI, see [Installing the AWS CLI using pip](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-install.html#install-tool-pip) in the *AWS Command Line Interface User Guide*\. For information about the AWS SDKs, see [Tools for Amazon Web Services](https://aws.amazon.com/tools)\.

**Important**  
For backward compatibility, the existing `autoscaling.region.amazonaws.com` endpoint will continue to be supported for calls to the AWS Auto Scaling API\. To set up the `autoscaling.region.amazonaws.com` endpoint as a private interface VPC endpoint, see [Amazon EC2 Auto Scaling and interface VPC endpoints](https://docs.aws.amazon.com/autoscaling/ec2/userguide/ec2-auto-scaling-vpc-endpoints) in the *Amazon EC2 Auto Scaling User Guide*\.

**Endpoint to Call When Using the CLI or the AWS Auto Scaling API**  
For the current release of AWS Auto Scaling, your calls to the AWS Auto Scaling API automatically go to the `autoscaling-plans.region.amazonaws.com` endpoint instead of `autoscaling.region.amazonaws.com`\.

You can call the new endpoint in the CLI by using the following parameter with each command to specify the endpoint: `--endpoint-url https://autoscaling-plans.region.amazonaws.com`\. 

Although it is not recommended, you can also call the old endpoint in the CLI by using the following parameter with each command to specify the endpoint: `--endpoint-url https://autoscaling.region.amazonaws.com`\. 

For the various SDKs used to call the APIs, see the documentation for the SDK of interest to learn how to direct the requests to a specific endpoint\. For more information, see [Tools for Amazon Web Services](https://aws.amazon.com/tools)\.