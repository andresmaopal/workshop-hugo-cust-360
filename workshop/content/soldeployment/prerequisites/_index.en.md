+++
title = "Required setup"
menuTitle = "Required setup"
date = 2020-08-28T08:56:14-05:00
weight = 5
chapter = true
pre = "<b>1.1 </b>"
+++

### Required setup

Perform the following steps before you launch the CloudFormation template.


### Create key pair in Oregon

A key pair, consisting of a private key and a public key, is a set of security credentials that you use to prove your identity when connecting to an instance, click on [Key pair documentation](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-key-pairs.html) to know more about it.


**Step 1:** Login in AWS console with your account login properties.

**Step 2:** Select Oregon region (us-west-2). At the top right side of your console check if you are doing in the right Region.

![Deploy 1](/images/soldeployment/pic-d-1.png)


**Step 3:** Go to [Key pairs console](https://us-west-2.console.aws.amazon.com/ec2/v2/home?region=us-west-2#KeyPairs:) and create a Key pair in Oregon:

**Key pair name:** c360view-oregon

![Deploy 2](/images/soldeployment/pic-d-2.png)

Click on Create key pair button.

![Deploy 3](/images/soldeployment/pic-d-3.png)

**Step 4:** Download key pair.

If you are in a **Windows** machine please download the key as **ppk** file.
If you are in a **Mac** or **Linux** please download the key as **pem** file.

### Create VPC endpoint for Amazon S3

A VPC endpoint enables you to privately connect your VPC to supported AWS services and VPC endpoint services powered by AWS PrivateLink without requiring an internet gateway, NAT device, VPN connection, or AWS Direct Connect connection.

To know more about VPC endpoint click on [VPC endpoint documentation](https://docs.aws.amazon.com/vpc/latest/userguide/vpc-endpoints.html).


**Step 1:** Go to [Amazon VPC console](https://us-west-2.console.aws.amazon.com/vpc/home?region=us-west-2#) to create an endpoint for Amazon S3, from the left Menu choose endpoints.

![Deployvpc 1](/images/soldeployment/pic-d-vpc-1.png)

**Step 2:** Click on **Create Endpoint** and then choose **AWS Services**.

![Deployvpc 2](/images/soldeployment/pic-d-vpc-2.png)

**Service Name:** *com.amazonaws.us-west-2.s3*
It will probably be in second pagination of AWS services.

![Deployvpc 3](/images/soldeployment/pic-d-vpc-3.png)


**Step 3:** Select the Default VPC.

![Deployvpc 4](/images/soldeployment/pic-d-vpc-4.png)


**Step 4:** Check the Route Table ID as above.

**Step 5:** Keep the Full access policy and don’t change the policy.

![Deployvpc 5](/images/soldeployment/pic-d-vpc-5.png)

**Step 6:** Create endpoint.
