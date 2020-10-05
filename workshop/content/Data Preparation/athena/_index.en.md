+++
title = "Query with Athena"
menuTitle = "Check with Athena"
date = 2020-08-28T08:56:14-05:00
weight = 15
chapter = true
pre = "<b>3.2 </b>"
+++

Access Amazon Athena console to check the raw and stage tables created so far.

**Step 1:** Go to [Amazon S3](https://s3.console.aws.amazon.com/s3/home?region=us-west-2) console and copy your c360view-us-west-2-<account id>-stage bucket name.

![bp 0](/images/athena/pic-at00.png)


**Step 2:** Click on the stage bucket to open it.


**Step 3:** At the top right of the screen mark and Copy the bucket name

![bp 0](/images/athena/pic-at01.png)


**Step 4:** Go to [Amazon Athena](https://us-west-2.console.aws.amazon.com/athena/home?region=us-west-2) console and setup your bucket output to your stage bucket on settings.

![bp 0](/images/athena/pic-at02.png)


**Step 5:** Click on the ‘set up a query result location in Amazon S3’ message.

Type s3://< your_stage_bucket_name >/athena-results/ as location path.

![bp 0](/images/athena/pic-at03.png)

**Step 6:** Choose c360view_raw to check the raw tables.

![bp 0](/images/athena/pic-at04.png)

**Step 7:** Click on the 3 dots at the right of table account, and select Preview table.

![bp 0](/images/athena/pic-at05.png)

**Step 8:** Check the results.

![bp 0](/images/athena/pic-at06.png)


Notice that as we had CSV without header the name of the columns where crawled as col0 to col3 in the RAW data.
You can edit this on AWS Glue, but our jobs to processed the data in Step Functions are already aware of it.

If you go to c360view_stage database you will find a different scenario.

**Step 9:** Check the other tables data and then go to the c360view_stage database.

![bp 0](/images/athena/pic-at07.png)