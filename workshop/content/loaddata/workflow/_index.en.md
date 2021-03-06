+++
title = "Use Database Blueprint"
menuTitle = "Use LF Database Blueprint"
date = 2020-08-28T08:56:14-05:00
weight = 30
chapter = true
pre = "<b>2.5 </b>"
+++

Create a workflow to bring data from your transactional relational database.

Check in your [CloudWatch events Rules](https://us-west-2.console.aws.amazon.com/cloudwatch/home?region=us-west-2#rules:) if you have started the c360-ScheduledIngestionPostgresql-<your account id>, as it has been created later maybe you did not start this one yet.

**Step 1:** If this Rule is not “green”, please enable it now on Actions.
![bp 0](/images/workflow/pic-wf00.png)


**Step 2:** Lake Formation Use blueprint to import data from a relational database
Go to [Lake Formation Workflows Blueprints](https://us-west-2.console.aws.amazon.com/lakeformation/home?region=us-west-2#workflows), and Use a Blueprint.

![bp 1](/images/workflow/pic-wf01.png)



**Step 3:** Choose database snapshot

![bp 1](/images/workflow/pic-wf02.png)

*	**Database connection:** sourcemf
*	**Source Path:** `sourcemf/%` (it means sourcemf database, with (%) all tables)

![bp 1](/images/workflow/pic-wf03.png)

*	**Do not choose any “Exclude patterns”**
*	**Target Database:** c360view_raw
*	**Target storage location:**  s3://c360view-us-west-2-<your-account>-raw
*	**Data format:** CSV

![bp 1](/images/workflow/pic-wf04.png)

*	**Frequency:** run on demand

*	**Workflow name:** `sourcemf_full_workflow`
*	**IAM role:** Glue-role-c360view
*	**Table Prefix:** `sourcemf`

![bp 1](/images/workflow/pic-wf05.png)

Click on *Create*. 


**Step 4:** After created it **Start it now**

![bp 1](/images/workflow/pic-wf06.png)


It will take some minutes for you to see the workflow importing data.

![bp 1](/images/workflow/pic-wf07.png)


You will come back later to this workflow, while it starts let’s perform some data processing.
