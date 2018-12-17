# Getting Started with Customized Metrics<a name="gs-customized-metric-specification"></a>

AWS Auto Scaling provides the most commonly used metrics for automatic scaling\. However, depending on your needs, you might prefer to get data from different metrics instead of the metrics in the console\. Amazon CloudWatch has many different metrics to choose from\. CloudWatch also lets you create your own metrics\. For more information about CloudWatch, see the [Amazon CloudWatch User Guide](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/)\. 

This topic covers using JSON to specify a customized metric for your scaling plan\. 

To use a customized metric for scaling, you must construct a JSON\-formatted payload with a set of required parameters from AWS Auto Scaling\. Add the values for each parameter from CloudWatch\. You then add the JSON to the associated resources in your scaling plan\. 

JSON represents data in two ways:
+ An *object*, which is an unordered collection of name\-value pairs\. An object is defined within left \(\{\) and right \(\}\) braces\. Each name\-value pair begins with the name, followed by a colon, followed by the value\. Name\-value pairs are comma\-separated\. 
+ An *array*, which is an ordered collection of values\. An array is defined within left \(\[\) and right \(\]\) brackets\. Items in the array are comma\-separated\. 

In the AWS Auto Scaling console, we provide a template for the metric specification\. You can find and update this template as part of the **Custom** metric settings for **Scaling metric** and **Load metric** in your scaling plan's advanced settings\. 

Here is an example of a JSON payload with sample values for each parameter: 

```
 {
   "MetricName": "MyBackendCPU",
   "Namespace": "MyNamespace",
   "Diminesions": [
     {
       "Name": "MyOptionalMetricDimensionName",
       "Value": "MyOptionalMetricDimensionValue"
     }
   ],
   "Statistic": "Sum"
 }
```

For more information, see [Customized Scaling Metric Specification](https://docs.aws.amazon.com/autoscaling/plans/APIReference/API_CustomizedScalingMetricSpecification.html) and [Customized Load Metric Specification](https://docs.aws.amazon.com/autoscaling/plans/APIReference/API_CustomizedLoadMetricSpecification.html) in the *AWS Auto Scaling API Reference*\.