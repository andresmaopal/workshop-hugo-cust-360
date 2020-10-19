+++
title = "Amazon DynamoDB"
menuTitle = "From Data lake to DynamoDB"
date = 2020-08-28T08:56:14-05:00
weight = 40
chapter = true
pre = "<b>4.4 </b>"
+++

Populate an Amazon DynamoDB table with the results to be the source for low latency queries from your applications or APIs.


Amazon DynamoDB is a key-value and document database that delivers single-digit millisecond performance at any scale. It's a fully managed, multiregion, multimaster, durable database with built-in security, backup and restore, and in-memory caching for internet-scale applications. DynamoDB can handle more than 10 trillion requests per day and can support peaks of more than 20 million requests per second.


![bp 0](/images/ddb/palacan-pic-ddb00.png)

We are going to use a Hive script to perform the query on source table and save it DynamoDB.

**Step 1:** Go to [EMR console](https://us-west-2.console.aws.amazon.com/elasticmapreduce/home?region=us-west-2).

![bp 1](/images/ddb/pic-ddb01.png)


**Step 2:** click on c360cluster.

![bp 1](/images/ddb/pic-ddb02.png)

**Step 3:** click on Steps tab.

![bp 1](/images/ddb/pic-ddb03.png)

**Step 4:** Click on *Add step*.

*	**Step type:** Hive program
*	**Name:** loadtodynamodb
*	**Script S3 location:** s3://`**your_stage_bucket**`/library/c360dynamodbload.q

Use the bucket browser to select the application location.


![bp 1](/images/ddb/pic-ddb04.png)

*	**Input S3 location:** leave blank
*	**Output s3 location:** leave blank
*	**Arguments:** leave blank
*	**Action on failure:** continue


![bp 1](/images/ddb/pic-ddb05.png)


**Step 5:** check the job status, going from pending to running.

![bp 1](/images/ddb/pic-ddb06.png)


**Step 6:** Check all applications status on the *Application user interfaces* tab.

![bp 1](/images/ddb/pic-ddb07.png)
