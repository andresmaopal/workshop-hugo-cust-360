+++
title = "Query with Athena"
menuTitle = "Check with Athena"
date = 2020-08-28T08:56:14-05:00
weight = 15
chapter = true
pre = "<b>3.2 </b>"
+++

Access Amazon Athena console to check the raw and stage tables created so far.

First, as a Lake Formation admin, you need grant your self permission to query the tables.

**Step 1:** Go to [Lake Formation](https://us-west-2.console.aws.amazon.com/lakeformation/home?region=us-west-2#tables) tables, select each of the tables and grant all permissions to your `user` or `role` you are using. Select a table and click Actions -> Grant (permissions).

![bp 0](/images/athena/pic-at00-00.png)

**Step 2:** Select the `grants` and your `user` or `role` in my case 'Teamrole'.
As the admin, select all the privileges for each table, and Grant.


![bp 0](/images/athena/pic-at00-01.png)

Repeat the process for the following tables:

- account
- card
- crm
- database
- gbank
- sourcemf_sourcemf_public_transactions

- visitors


**Step 3:** Go to [Amazon S3](https://s3.console.aws.amazon.com/s3/home?region=us-west-2) console and copy your c360view-us-west-2-<account id>-stage bucket name.

![bp 0](/images/athena/pic-at00.png)


**Step 4:** Click on the stage bucket to open it.


**Step 5:** At the top right of the screen mark and Copy the bucket name

![bp 0](/images/athena/pic-at01.png)


**Step 6:** Go to [Amazon Athena](https://us-west-2.console.aws.amazon.com/athena/home?region=us-west-2) console and setup your bucket output to your stage bucket on settings.

![bp 0](/images/athena/pic-at02.png)


**Step 7:** Click on the ‘set up a query result location in Amazon S3’ message.

Type s3://< your_stage_bucket_name >/athena-results/ as location path.

![bp 0](/images/athena/pic-at03.png)

**Step 8:** Choose c360view_raw to check the raw tables.

![bp 0](/images/athena/pic-at04.png)

**Step 9:** Click on the 3 dots at the right of table account, and select Preview table.

![bp 0](/images/athena/pic-at05.png)

**Step 10:** Check the results.

![bp 0](/images/athena/pic-at06.png)


Notice that as we had CSV without header the name of the columns where crawled as col0 to col3 in the RAW data.
You can edit this on AWS Glue, but our jobs to processed the data in Step Functions are already aware of it.

If you go to c360view_stage database you will find a different scenario.

**Step 11:** Check the other tables data and then go to the c360view_stage database.

![bp 0](/images/athena/pic-at07.png)
