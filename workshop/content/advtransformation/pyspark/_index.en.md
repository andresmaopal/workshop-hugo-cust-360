+++
title = "PySpark - Glue"
menuTitle = "Glue PythonShell and PySpark"
date = 2020-08-28T08:56:14-05:00
weight = 10
chapter = true
pre = "<b>4.1 </b>"
+++

Now you are going to perform more advanced transformations using AWS Glue jobs.


**Step 1:** Go to [AWS Glue jobs console](https://us-west-2.console.aws.amazon.com/glue/home?region=us-west-2#etl:tab=jobs), select `n1_c360_dispositions`, Pyspark job.


![bp 0](/images/pyspark/pic-py01.png)

The transformation inside this job performs a join between 3 tables, general banking, account and card, to calculate disposition type and acquisition information.

**Step 2:** Click on Edit job.

![bp 1](/images/pyspark/pic-hhug-py02.png)

**Step 3:** Change **Glue version** to `Spark 2.4, Python 3 with improved startup times (Glue Version 2.0)`.

![bp 1](/images/pyspark/pic-hhug-gluev.png)

**Step 4:** Select your stage S3 bucket c360view-us-west-2-*your_account_id*-stage + '/tmp/' as Temporary directory.

![bp 1](/images/pyspark/pic-hhug-gluev2.png)

Save.

**Step 5:** Select `n1_c360_dispositions` and click on Action, Run job.

![bp 1](/images/pyspark/pic-py02.png)

**Step 6:** Wait for completion.

![bp 1](/images/pyspark/pic-py03.png)

**Step 7:** Check the script and logs.

![bp 1](/images/pyspark/pic-py04.png)

Notice that in this Python script that converts a query result from Amazon Athena to a Pandas data frame and then the result from Pandas transformation to parquet files in Amazon S3 using spark write operation.

**Step 8:** Now select the **Jobcust360etlmftrans**, another Pyspark job, Action and Edit job.

![bp 1](/images/pyspark/pic-hhug-gluev3.png)


**Step 9:** Change **Glue version** to `Spark 2.4, Python 3 with improved startup times (Glue Version 2.0)` and select your stage S3 bucket c360view-us-west-2-*your_account_id*-stage + '/tmp/' as Temporary directory.

![bp 1](/images/pyspark/pic-hhug-gluev4.png)

Save.

**Step 10:** Now select the **Jobcust360etlmftrans**, Action and run job.

![bp 1](/images/pyspark/pic-py05.png)

**Step 11:** Wait for completion.

![bp 1](/images/pyspark/pic-py06.png)

**Step 12:** Check the script and logs.

![bp 1](/images/pyspark/pic-py07.png)

In this pyspark script we are doing some aggregations with the transactions from relational database done by account_id in the last 3 months and also the last 6 months. For this we used the AWS Glue dynamic frame.
