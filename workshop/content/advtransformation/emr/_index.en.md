+++
title = "Amazon EMR"
menuTitle = "Amazon EMR denormalized table"
date = 2020-08-28T08:56:14-05:00
weight = 20
chapter = true
pre = "<b>4.3 </b>"
+++

To create a denormalized table we are going to run a job on [Amazon EMR](https://aws.amazon.com/emr/?nc1=h_ls).

Amazon EMR is a powerful cluster, that you can set with few machines like in this Workshop or tens to thousands of machines. Consider using [spot instances](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-instance-purchasing-options.html) for batch processing and terminate your clusters when you are not using them. It is also recommended to store job results on Amazon S3.

**Step 1:** Go to [EMR console](https://us-west-2.console.aws.amazon.com/elasticmapreduce/home?region=us-west-2).

![bp 1](/images/emr/pic-em01.png)


**Step 2:** click on c360cluster.

![bp 1](/images/emr/pic-em02.png)

**Step 3:** click on Steps tab.

![bp 1](/images/emr/pic-em03.png)

**Step 4:** Add step.

*	**Step type:** Spark application
*	**Name:** denormalization
*	**Deploy mode:** Cluster
*	**Spark-submit option:** leave blank
*	**Application location:** s3://`**your_stage_bucket**`/library/c360_analytics.py

Use the bucket browser to select the application location.

![bp 1](/images/emr/pic-em04.png)

*	**Arguments:** `--BucketName` `**your analytics bucket**`
Pick the name from Amazon S3 console
*Leave a space between `--BucketName` and your bucket name*,  without s3://.

![bp 1](/images/emr/pic-em05.png)

Then, click on Add.


**Step 5:** check the job status, going from pending to running.

![bp 1](/images/emr/pic-em06.png)

After completion the job has created a denormalized table using PySpark.

![bp 1](/images/emr/pic-em07.png)

**Step 6:** go to [Lake formation console](https://us-west-2.console.aws.amazon.com/lakeformation/home?region=us-west-2#tables) select the `c360denormalized` table from `c360view_analytic` databases.

![bp 1](/images/emr/pic-em09.png)

**Step 7:** Grant access to it to your `user` or `role`.

![bp 1](/images/emr/pic-em10.png)

**Step 8:** go to [Athena console](https://us-west-2.console.aws.amazon.com/athena/home?region=us-west-2#query) and check the new c360denormalized table on c360view_analytics database.

![bp 1](/images/emr/pic-em08.png)
