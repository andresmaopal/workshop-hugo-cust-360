+++
title = "Build Table Definitions"
menuTitle = "Crawler the data"
date = 2020-08-28T08:56:14-05:00
weight = 25
chapter = true
pre = "<b>2.4 </b>"
+++

Execute a crawler at AWS Glue Console to get tables definitions from your raw bucket.


A crawler accesses your data store, extracts metadata, and creates table definitions in the AWS Glue Data Catalog. The Crawlers pane in the AWS Glue console lists all the crawlers that you create. The list displays status and metrics from the last run of your crawler.

![bp 0](/images/crawler/palacan-pic-cw00.png)


**Step 1:** Go to AWS [Glue Crawlers](https://us-west-2.console.aws.amazon.com/glue/home?region=us-west-2#catalog:tab=crawlers):

![bp 0](/images/crawler/pic-cw00.png)


**Create databases and table definitions with Glue Crawler**

**Step 2:** Click on the Crawler360rawdata and Run crawler.

*	•	This crawler will read your raw bucket files and create table definitions for each of the table schema for database c360view-raw.


![bp 1](/images/crawler/pic-cw01.png)

**Step 3:** Select Crawlerc360visitorid and run crawler.

![cf 5](/images/crawler/pic-cw05.png)

**Step 4:** You should see 5 tables added by Crawler360rawdata Crawler.

![cf 2](/images/crawler/pic-cw02.png)

You should see **one table** added by the Crawlerc360visitorid crawler.

![cf 5](/images/crawler/pic-cw06.png)


**Step 4:** You can verify them going to Database -> Tables in the same console.

![cf 5](/images/crawler/pic-cw04.png)

{{% notice note %}}
Glue Crawler created *c360view_raw* and *c360view_stage* databases and the 6 table definitions.
{{% /notice %}}
