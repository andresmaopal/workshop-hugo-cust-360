+++
title = "Deploy CloudFormation"
menuTitle = "Deploy CloudFormation"
date = 2020-08-28T08:56:14-05:00
weight = 10
chapter = true
pre = "<b>1.2 </b>"
+++


Deploy CloudFormation template to create basic infrastructure


**Step 1:** Download Cloudformation template [cf-360view.yaml : Right click here and Save Link as File.](/files/cf-360view.yaml)



![cf 0](/images/cloudformation/pic-cf0.png)


**Step 2:** Open the AWS [Cloudformation stack creation](https://us-west-2.console.aws.amazon.com/cloudformation/home?region=us-west-2#/stacks/create/template) And Upload a template file.

![cf 1](/images/cloudformation/pic-cf01.png)


**Step 3:** Choose Next and fill up the parameters:

* **Stack name:** c360view
*	**Network Configuration:**
 *	Which VPC should this be deployed to?: *Default VPC (172.31.0.0/16)*
 *	SubnetAz1: (172.31.0.0/20) (look for this IP range)
 *	SubnetAz2: (172.31.16.0/20) (look for this IP range)
*	**InstanceKeyPairParameter:** c360view-oregon (the one that you created before)

![cf 2](/images/cloudformation/pic-cf2.png)


**Step 4:** Choose Next. No need to change anything on **Configure stack options**, click Next again.


**Step 5:** Scroll down to find a check box and mark the “I acknowledge that AWS CloudFormation might create IAM resources.”  and Create stack.

![cf 3](/images/cloudformation/pic-cf3.png)

**Step 6:** Go to Resources tab to look for completion of resources.

![cf 4](/images/cloudformation/pic-cf4.png)

The template has created the following resources to optimize your time.
3 Amazon S3 buckets:

*	RawDataS3Bucket
*	StageDataS3Bucket
*	AnalyticsDataS3Bucket

1 RDS instance with PostgreSQL database to simulate your transaction database.

*	RDSSource – sourcemf

6 Lambda functions to generate data for different source.

*	c360viewCRMApi
*	c360viewGetCRMApi
*	c360viewGetGaTables
*	c360viewMFgenAccount
*	c360viewMFgenCard
*	c360viewMFgenGBank

5 CloudWatch events schedules, to trigger the Lambda functions.

2 Security group, firewalls, one for the EC2 instance, other for Replication instances and Lambda functions.

1 Role for the AWS Lambda functions
1 Role for the AWS Glue

1 Amazon EMR cluster

Check the status of each resource, and order by resource status.

After you see "CREATE_COMPLETE" for the stack all resources are ready and you can proceed to next step `Load Data`.
