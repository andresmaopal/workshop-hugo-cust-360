+++
title = "Glue Crawler"
menuTitle = "Glue Crawler"
date = 2020-08-28T08:56:14-05:00
weight = 15
chapter = true
pre = "<b>4.2 </b>"
+++

Run the Glue crawler Crawler360jobtables3m, Crawler360jobtables6m to pick up definition for the data just created by the last job.


**Step 1:** Go to [AWS Glue crawler console](https://us-west-2.console.aws.amazon.com/glue/home?region=us-west-2#catalog:tab=crawlers).


**Step 2:** Select Crawler360jobtables3m and click on run crawler.

![bp 1](/images/glue/pic-gl01.png)

**Step 3:** Select Crawler360jobtables6m and click on run crawler.

![bp 1](/images/glue/pic-gl02.png)

**Step 4:** Verify that each new crawler run has added one table definition.

![bp 1](/images/glue/pic-gl03.png)


**Step 5:** Go to Glue Databases -> tables, check the tables you have. You can filter by Database at search bar for `c360view_stage`.
We have now 14 tables in the `c360view_stage` database.

![bp 1](/images/glue/pic-gl04.png)
