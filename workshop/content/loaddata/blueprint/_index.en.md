+++
title = "Connect to Database"
menuTitle = "Connect to Database"
date = 2020-08-28T08:56:14-05:00
weight = 20
chapter = true
pre = "<b>2.3 </b>"
+++

Create a connection for relational database as source.


**Step 1:** Go to [AWS Glue Database Connections](https://us-west-2.console.aws.amazon.com/glue/home?region=us-west-2#catalog:tab=connections), and Add connection.

![bp 0](/images/blueprint/pic-bp00.png)

*	**Connection name:** sourcemf
*	**Connection type:** Amazon RDS
*	**Database Engine:** PostgreSQL



![cf 1](/images/blueprint/pic-bp01.png)


**Step 2:** Set up access, choosing your Instance sourcemf:

*	**Instance:** sourcemf
*	**Database name:** sourcemf
*	**Username:** sourcemf
*	**Password:** `Tim3t0change`

![cf 2](/images/blueprint/pic-bp02.png)


**Step 3:** Click on **Finish:**

![cf 3](/images/blueprint/pic-bp03.png)


**Step 4:** Edit your connection to Add a Security group to your connection:

![cf 4](/images/blueprint/pic-bp04.png)

**Step 5:** Check the c360view-c360-Access and c360view-RDS-Source security group:
* **Group name:** c360view-c360-Access and c360view-RDS-Source
* **Password:** Tim3t0change (re-enter it)

![cf 5](/images/blueprint/pic-bp05.png)

**Step 6:** Test your connection:
*	**IAM role:** Glue-role-c360view

![cf 6](/images/blueprint/pic-bp06.png)


**Step 7:** You will see sourcemf connected successfully:

![cf 7](/images/blueprint/pic-bp07.png)

If you receive the following error:

![cf 8](/images/blueprint/pic-bp08.png)

Edit your connection again and change the Subnet to another one.

![cf 9](/images/blueprint/pic-bp09.png)

Then test the connection with the new chosen subnet until it works.
