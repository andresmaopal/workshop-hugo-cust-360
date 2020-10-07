+++
title = "Lake Formation setup"
menuTitle = "Lake Formation setup"
date = 2020-08-28T08:56:14-05:00
weight = 15
chapter = true
pre = "<b>2.2 </b>"
+++

#### Setup your Data Lake with Lake Formation


**Step 1:** Go to the [Lake Formation console](https://us-west-2.console.aws.amazon.com/lakeformation/home?region=us-west-2):

![lf 0](/images/lakeformation/pic-lf00.png)

If you have a Get Started screen, click on Get Started.

If are now on Lake Formation console go to Permissions -> **Admins and database creators**, and grant your user as administrator.


**Step 2:** Add your **user** or the **role** you are using as Data Lake admin, so your user can administer storage areas, databases and tables.

![cf 1](/images/lakeformation/pic-lf01.png)

Add your user as Administrator and Save


**Step 3:** Add the buckets starting with “c360view” as [data lake locations](https://us-west-2.console.aws.amazon.com/lakeformation/home?region=us-west-2#register-list) for Lake Formation. Indicating there are part of your data lake.

![cf 2](/images/lakeformation/pic-lf02.png)

**Step 4:** Click Register location.

![cf 3](/images/lakeformation/pic-lf03.png)


**Step 5:** Click on Browse and select each c360view bucket to register.

![cf 4](/images/lakeformation/pic-lf04.png)

Repeat it for the 3 buckets:

*	c360view-us-west-2-<your_account_id>-raw
*	c360view-us-west-2-<your_account_id>-stage
*	c360view-us-west-2-<your_account_id>-analytics

After registration you will see a screen like the following.

![cf 5](/images/lakeformation/pic-lf05.png)


**Step 6:** On [Lake Formation data locations permission console](https://us-west-2.console.aws.amazon.com/lakeformation/home?region=us-west-2#location-permissions) Click on Grant to grant access to the AWS Lambda, AWS Glue service role and Amazon EMR EC2 role.

![cf 6](/images/lakeformation/pic-lf06.png)


**Step 7:** Grant the locations to **Glue-role-c360view**.

*	IAM users and roles: **Glue-role-c360view**

#### Storage locations:
  *	c360view-us-west-2-<your_account_id>-raw
  *	c360view-us-west-2-<your_account_id>-stage
  *	c360view-us-west-2-<your_account_id>-analytics

![cf 8](/images/lakeformation/pic-lf08.png)


You will see these grants for locations.


![cf 10](/images/lakeformation/pic-lf10.png)


**Step 8:** Go to [Admins and database creators](https://us-west-2.console.aws.amazon.com/lakeformation/home?region=us-west-2#catalog-settings).


![cf 11](/images/lakeformation/pic-lf11.png)

**Step 9:** Grant `database creator` to the following roles:

- Glue-role-c360view

![cf 12](/images/lakeformation/pic-lf12.png)

Click `Grant`
