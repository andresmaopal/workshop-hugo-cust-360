+++
title = "Connect to Database"
menuTitle = "Connect to Database"
date = 2020-08-28T08:56:14-05:00
weight = 20
chapter = true
pre = "<b>2.3 </b>"
+++

Create a connection for relational database as source.

You will use Lake Formation Blueprints for this purpose. Lake Formation Blueprints provides the following types of workflows to execute common ETL use:

*	**Database snapshot** – Loads or reloads data from all tables into the data lake from a JDBC source.

*	**Incremental database** – Loads only new data into the data lake from a JDBC source, based on previously set bookmarks

we are going to use a snapshot ingestion for this exercise.


**Step 1:** Go to [AWS Glue Database Connections](https://us-west-2.console.aws.amazon.com/glue/home?region=us-west-2#catalog:tab=connections), and Add connection.

![bp 0](/images/blueprint/pic-bp00.png)

*	**Connection name:** sourcemf
*	**Connection type:** Amazon RDS
*	**Database Engine:** PostgreSQL


![cf 1](/images/blueprint/pic-bp01.png)

Click on Next.


**Step 2:** Set up access, choosing your Instance sourcemf:

*	**Instance:** sourcemf
*	**Database name:** sourcemf
*	**Username:** sourcemf
*	**Password:** `Tim3t0change`

![cf 2](/images/blueprint/pic-bp02.png)

Click on Next.


**Step 3:** Click on **Finish:**

![cf 3](/images/blueprint/pic-bp03.png)

Use refresh button to see your connection.

**Step 4:** Edit your connection to Add a Security group to your connection:

![cf 4](/images/blueprint/pic-bp04.png)

**Step 5:** Click next.

![cf 4hhu](/images/blueprint/pic-bp04-hhug.png)

**Step 6:** In the Security groups section check the **c360view-c360-Access** and **c360view-RDS-Source** security group:

* **Security Group names:** `c360view-c360-Access`
and `c360view-RDS-Source`
* **Password:** `Tim3t0change` (re-enter it)

![cf 5](/images/blueprint/pic-bp05.png)

Click on *Next*, and then on *Finish*.


**Step 7:** Test your connection:
*	**IAM role:** Glue-role-c360view

![cf 6](/images/blueprint/pic-bp06.png)


**Step 8:** You will see sourcemf connected successfully:

![cf 7](/images/blueprint/pic-bp07.png)

If you receive the following error:

![cf 8](/images/blueprint/pic-bp08.png)

Edit your connection again and change the Subnet to another one, from the same VPC.

![cf 9](/images/blueprint/pic-bp09.png)

Then test the connection with the new chosen subnet until it works.
