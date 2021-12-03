# Identity and Access Management for scaling plans<a name="auth-and-access-control"></a>



AWS Identity and Access Management \(IAM\) is an AWS service that helps an administrator securely control access to AWS resources\. IAM administrators control who can be *authenticated* \(signed in\) and *authorized* \(have permissions\) to use AWS Auto Scaling resources\. IAM is an AWS service that you can use with no additional charge\.

To use scaling plans, you need an AWS account and credentials\. To increase the security of your account, we recommend that you use an *IAM user* to provide access credentials instead of using your AWS account credentials\. For more information, see [Amazon Web Services account root user credentials vs\. IAM user credentials](https://docs.aws.amazon.com/general/latest/gr/root-vs-iam.html) in the *AWS General Reference* and [IAM best practices](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html) in the *IAM User Guide*\. 

For an overview of IAM users and why they are important for the security of your account, see [AWS security credentials](https://docs.aws.amazon.com/general/latest/gr/aws-security-credentials.html) in the *AWS General Reference*\.

For details about working with IAM, see the *[IAM User Guide](https://docs.aws.amazon.com/IAM/latest/UserGuide/)*\. 

## Access control<a name="access-control"></a>

You can have valid credentials to authenticate your requests, but unless you have permissions you cannot create or access scaling plans\. For example, you must have permissions to create scaling plans, configure predictive scaling, and so on\. 

The following sections provide details on how an IAM administrator can use IAM to help secure your scaling plans, by controlling who can work with scaling plans\. 

**Topics**
+ [Access control](#access-control)
+ [How scaling plans work with IAM](security_iam_service-with-iam.md)
+ [Predictive scaling service\-linked role](aws-auto-scaling-service-linked-roles.md)
+ [Identity\-based policy examples for scaling plans](security_iam_id-based-policy-examples.md)