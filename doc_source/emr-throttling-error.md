# Throttling errors<a name="emr-throttling-error"></a>

The errors "Throttled from *Amazon EC2* while launching cluster" and "Failed to provision instances due to throttling from *Amazon EC2*" occur when Amazon EMR cannot complete a request because another service has throttled the activity\. Amazon EC2 is the most common source of throttling errors, but other services may be the cause of throttling errors\. [AWS service limits](https://docs.aws.amazon.com/general/latest/gr/aws_service_limits.html) apply on a per\-Region basis to improve performance, and a throttling error indicates that you have exceeded the service limit for your account in that Region\.

## Possible causes<a name="emr-failed-to-provision-instances-due-to-throttling-causes"></a>

The most common source of Amazon EC2 throttling errors is a large number of cluster instances launching so that your service limit for EC2 instances is exceeded\. Cluster instances may launch for the following reasons:
+ New clusters are created\.
+ Clusters are resized manually\. For more information, see [Manually resizing a running cluster](emr-manage-resize.md)\.
+ Instance groups in a cluster add instances \(scale out\) as a result of an automatic scaling rule\. For more information, see [Understanding automatic scaling rules](emr-automatic-scaling.md#emr-scaling-rules)\.
+ Instance fleets in a cluster add instances to meet an increased target capacity\. For more information, see [Configure instance fleets](emr-instance-fleet.md)\.

It is also possible that the frequency or type of API request being made to Amazon EC2 causes throttling errors\. For more information about how Amazon EC2 throttles API requests, see [Query API request rate](https://docs.aws.amazon.com/AWSEC2/latest/APIReference/query-api-troubleshooting.html#api-request-rate) in the *Amazon EC2 API Reference*\.

## Solutions<a name="emr-throttling-error-solutions"></a>

Consider the following solutions:
+ Follow the instructions in [AWS service quotas](https://docs.aws.amazon.com/general/latest/gr/aws_service_limits.html) in the *Amazon Web Services General Reference* to request a service limit increase\. For some APIs, setting up a CloudWatch event might be a better option than increasing limits\. For more details, see [When to set up EMR events in CloudWatch](emr-service-limits-cloudwatch-events.md)\.
+ If you have clusters that launch on the same schedule—for example, at the top of the hour—consider staggering start times\.
+ If you have clusters that are sized for peak demand, and you periodically have instance capacity, consider specifying automatic scaling to add and remove instances on\-demand\. In this way, instances are used more efficiently, and depending on the demand profile, fewer instances may be requested at a given time across an account\. For more information, see [Using automatic scaling with a custom policy for instance groups ](emr-automatic-scaling.md)\.