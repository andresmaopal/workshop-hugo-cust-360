+++
title = "Convert DB to Parquet"
menuTitle = "Convert DB data to Parquet"
date = 2020-08-28T08:56:14-05:00
weight = 40
chapter = true
pre = "<b>3.4 </b>"
+++

Perform transformation with relational database source raw tables and to have them transformed into parquet files.

Check in your step functions [State machine console](https://us-west-2.console.aws.amazon.com/states/home?region=us-west-2#/statemachines).


**Step 1:** Click on the link of relational database transformation “MyStateMachineRelationalDB-hash”.


![bp 0](/images/transdb/pic-td01.png)


**Step 2:** Start execution.

![bp 1](/images/transdb/pic-td02.png)

**Step 3:** Do not change the parameters and confirm Start execution.

![bp 1](/images/transdb/pic-td03.png)

**Step 4:** Verify the completion of the workflow. (Refresh your browser)

![bp 1](/images/transdb/pic-td04.png)

**Step 5:** Go to [Amazon Athena console](https://us-west-2.console.aws.amazon.com/athena/home?region=us-west-2#query), c360view_stage database and check the table mf_transactions_pqt.

![bp 1](/images/transdb/pic-td05.png)

You may need to grant access to "c360view_stage"."mf_transactions_pqt"  table to your *user* or *role* in Lake Formation console.
