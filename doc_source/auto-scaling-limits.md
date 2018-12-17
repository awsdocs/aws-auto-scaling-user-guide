# AWS Auto Scaling Limits<a name="auto-scaling-limits"></a>

Your AWS account has the following limits related to AWS Auto Scaling\. To request a limit increase, use the [Auto Scaling Limits form](https://console.aws.amazon.com/support/home#/case/create?issueType=service-limit-increase&limitType=service-code-auto-scaling)\.


**Default Limits Per Region Per Account**  

| Item | Default Limit | Notes | 
| --- | --- | --- | 
| Maximum number of scalable resources per resource type |  Amazon DynamoDB: 2000 Amazon EC2 Auto Scaling groups: 200 All other resource types: 500  | Make sure that you specify the type of resource with your request for a limit increase, for example, Amazon EC2 Auto Scaling, Amazon ECS, or DynamoDB\. | 
| Maximum number of scaling plans | 100 |  | 
| Maximum number of scaling instructions per scaling plan | 500 |  | 
| Maximum number of target tracking configurations per scaling instruction | 10 |  | 

For more information on the service limits for other AWS services, see [AWS Service Limits](https://docs.aws.amazon.com/general/latest/gr/aws_service_limits.html) in the *Amazon Web Services General Reference*\.