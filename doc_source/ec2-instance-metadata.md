# Instance metadata and user data<a name="ec2-instance-metadata"></a>

*Instance metadata* is data about your instance that you can use to configure or manage the running instance\. Instance metadata is divided into [categories](instancedata-data-categories.md), for example, host name, events, and security groups\.

You can also use instance metadata to access *user data* that you specified when launching your instance\. For example, you can specify parameters for configuring your instance, or include a simple script\. You can build generic AMIs and use user data to modify the configuration files supplied at launch time\. For example, if you run web servers for various small businesses, they can all use the same generic AMI and retrieve their content from the Amazon S3 bucket that you specify in the user data at launch\. To add a new customer at any time, create a bucket for the customer, add their content, and launch your AMI with the unique bucket name provided to your code in the user data\. If you launch more than one instance at the same time, the user data is available to all instances in that reservation\. Each instance that is part of the same reservation has a unique `ami-launch-index` number, allowing you to write code that controls what to do\. For example, the first host might elect itself as the original node in a cluster\. For a detailed AMI launch example, see [Example: AMI launch index value](AMI-launch-index-examples.md)\.

EC2 instances can also include *dynamic data*, such as an instance identity document that is generated when the instance is launched\. For more information, see [Dynamic data categories](instancedata-data-categories.md#dynamic-data-categories)\.

**Important**  
Although you can only access instance metadata and user data from within the instance itself, the data is not protected by authentication or cryptographic methods\. Anyone who has direct access to the instance, and potentially any software running on the instance, can view its metadata\. Therefore, you should not store sensitive data, such as passwords or long\-lived encryption keys, as user data\.

**Note**  
The examples in this topic use the IPv4 address of the Instance Metadata Service \(IMDS\): `169.254.169.254`\. If you are retrieving instance metadata for EC2 instances over the IPv6 address, ensure that you enable and use the IPv6 address instead: `fd00:ec2::254`\. The IPv6 address of the IMDS is compatible with IMDSv2 commands\. The IPv6 address is only accessible on [Instances built on the Nitro System](instance-types.md#ec2-nitro-instances)\.

**Topics**
+ [Use IMDSv2](configuring-instance-metadata-service.md)
+ [Configure the instance metadata options](configuring-instance-metadata-options.md)
+ [Retrieve instance metadata](instancedata-data-retrieval.md)
+ [Work with instance user data](instancedata-add-user-data.md)
+ [Retrieve dynamic data](instancedata-dynamic-data-retrieval.md)
+ [Instance metadata categories](instancedata-data-categories.md)
+ [Example: AMI launch index value](AMI-launch-index-examples.md)
+ [Instance identity documents](instance-identity-documents.md)
+ [Instance identity roles](ec2-instance-identity-roles.md)