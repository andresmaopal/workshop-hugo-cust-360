+++
title = "Low latency 360 view"
menuTitle = "Customer 360view low latency"
date = 2020-08-28T08:56:14-05:00
weight = 60
chapter = true
pre = "<b>5. </b>"
+++

Query Amazon DynamoDB table with the results to be the source for low latency queries from your applications or APIs.

![adv trans](/images/intro/hhug-adv-ddb.png)


**Step 1:** Go to [Amazon DynamoDB console](https://us-west-2.console.aws.amazon.com/dynamodb/home?region=us-west-2#tables:selected=DDBc360view;tab=items).

![bp 1](/images/viewddb/pic-ddb01.png)


**Step 2:** Click on the table DDBc360view that you have populated with a Hive script using yor EMR cluster, and click on tab Items.

![bp 1](/images/viewddb/pic-ddb02.png)

Notice that the console did a Scan operation, returning all data, but in your application, you may want to be specific and use a client id or/and branch for example.

**Step 3:** So, take note of some pk (partition key), that is your “client_id” from denormalized table and sk (sort key) that is your “branch_id”, so you can perform some specific query.
In my case, I can use 5002, 5006, 5014, 5021, 5025, 5035… and so on for client id (our pk), and 198, 465, 236, 218, 109, 215, 394, 381, 225 for branch.
Your numbers will be different as the data being generated in your account is random.



**Step 4:** Scroll the view to the right and down so you can check other fields for the records.


![bp 1](/images/viewddb/pic-ddb03.png)


**Step 5:** Now instead of Scan, select Query and put a value of client id in the pk field. In my case 5002, but select one of yours taken in previous step.

![bp 1](/images/viewddb/pic-ddb04.png)


**Step 6:** click on Start search and see that it’s display right away.

![bp 1](/images/viewddb/pic-ddb05.png)

**Step 7:** click at the pk link for the id you chose so you can see the full payload.

![bp 1](/images/viewddb/pic-ddb06.png)

![bp 1](/images/viewddb/pic-ddb07.png)

### Repeat this for some customer ids.

You did a query by partition key, you can also use the index to directly find for every customer in a branch by choosing the index already created GSI1 index that is a Global secondary index.

Using GSIs we can change the query key by other field we need to find data very fast.

**Step 1:** GSelect the GSI1 index to query.

![bp 1](/images/viewddb/pic-ddb11.png)


**Step 2:** Put a branch number, such as 394 in my case.

![bp 1](/images/viewddb/pic-ddb12.png)

You can enter in the pk of the desired client and see the whole profile.

The use case for this Amazon DynamoDB table is to have fast access to data when you need to interact directly with your customer. Examples of use cases are mobile branch manager applications, or contact center applications, in order to check the profile of a customer, or even other dimensions you decide to increment here, as in the scenario of next best offer.

There are several examples to expose a DynamoDB table with an API, using Amazon API Gateway, as in this Workshop. But if your application resides inside your AWS account, you probably may use calls directly to DynamoDB SDK and API.


If you want to check other codes used in this workshop go to your stage bucket in S3, in the "library" folder.

![bp 1](/images/viewddb/pic-ddb13.png)


You can also check the lambda functions code on AWS Lambda console by clicking in any of them.


![bp 1](/images/viewddb/pic-ddb14.png)


For Data scientists and business users, you can also use [Amazon Sagemaker](https://aws.amazon.com/sagemaker/?nc1=h_ls) and [Amazon Quicksight](https://aws.amazon.com/quicksight/?nc1=h_ls) to explore the data using Athena. Find more details on the links for [creating data set from Athena on Quicksight](https://docs.aws.amazon.com/quicksight/latest/user/create-a-data-set-athena.html) and [Run SQL queries from your Sagemaker notebooks using Amazon Athena](https://aws.amazon.com/Workshops/machine-learning/run-sql-queries-from-your-sagemaker-notebooks-using-amazon-athena/).
