+++
title = "Visualize with Quicksight"
menuTitle = "Visualize with Quicksight"
date = 2020-08-28T08:56:14-05:00
weight = 70
chapter = true
pre = "<b>6. </b>"
+++

To explore the data with dashboards you can use [Amazon Quicksight](https://aws.amazon.com/quicksight/?nc1=h_ls).

As a fully managed service, QuickSight lets you easily create and publish interactive dashboards that include ML Insights. Dashboards can then be accessed from any device, and embedded into your applications, portals, and websites.

**Step 1:** Sign up for Amazon Quicksight.

If you don't have Amazon Quicksight account enabled in your AWS Account follow the steps [here](https://docs.aws.amazon.com/quicksight/latest/user/setup-new-quicksight-account.html).


**Step 3:** Go to [Quicksight console](https://quicksight.aws.amazon.com/sn/start). You need go to us-east-1 N.Virginia for this setup.

![qs2](/images/qs/qs-01.png)


**Step 4:** Select Add or remove from `Security & permissions.`

![qs2](/images/qs/qs-02.png)


**Step 5:** Check Amazon S3.

![qs2](/images/qs/qs-03.png)


**Step 6:** Select your three `c360view-us-west-2-` buckets and Check *Write permission for Athena Workgroup*.

![qs2](/images/qs/qs-04.png)



**Step 7:**  Check Athena.


![qs2](/images/qs/qs-05.png)

- do the same selection as before.

![qs2](/images/qs/qs-04.png)

{{% notice note %}}
If you use another bucket for Athena results, please add it to your selection.
{{% /notice  %}}


**Step 8:**  Click on *Update*.

![qs2](/images/qs/qs-06.png)



Grant select on databases to your user or role on Quicksight.

**Step 9:** Go to [IAM console](https://console.aws.amazon.com/iam/home?region=us-west-2#/policies) and click on `Create Policy`.


Select json tab and paste the following json block.

    {
        "Version": "2012-10-17",
        "Statement": [
            {
                "Sid": "listusers",
                "Effect": "Allow",
                "Action": "quicksight:ListUsers",
                "Resource": "*"
            }
        ]
    }

![qs2](/images/qs/qs--3.png)

Click on Review policy.

**Step 10:** Create policy:

- Name: qslist


![qs2](/images/qs/qs--4.png)

Click on Create policy.


**Step 11:** Create an [IAM user](https://console.aws.amazon.com/iam/home?region=us-west-2#/users$new?step=details) `qslist` with  Programmatic access only.


![qs2](/images/qs/qs--1.png)

Click on Next: permissions.


**Step 12:** In *Set permissions*, select* Attach existing policies directly.*

**Step 13:** Look for `qslist` policy. Check it and go to Next: Tags.

![qs2](/images/qs/qs--5.png)

**Step 14:** Click on *Next: Review.*

**Step 15:** Click on *Create user.*

![qs2](/images/qs/qs--6.png)

**Step 16:** Click on  Download.csv file, as you will use it to Configure AWS cli.

![qs2](/images/qs/qs--7.png)


**Step 17:** Download and install `aws cli` in your machine, follow instructions from [aws cli installation guide.](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-install.html)


**Step 18:** Setup credentials to use your cli:

At your machine terminal or windows cmd.

    aws configure --profile qslist

* AWS Access Key ID [None]:  **< your Access key from credentials file >**
* AWS Secret Access Key [None]: **< your Secret Access key from credentials file>**
* Default region name [None]: **us-east-1**
* Default output format [None]: **json**


![qs2](/images/qs/qs--8.png)




**Step 19:**  Pick your `<your account id>`.


 ![qs2](/images/qs/qs--9.png)

**Step 20:** Find your Quicksight user arn.  

At your machine terminal or windows cmd, use < your account id > number from above.

    aws quicksight list-users --aws-account-id <your account id> --namespace default  --region us-east-1 --profile qslist


![qs2](/images/qs/qs--10.png)


**Copy this user full ARN** to use in Lake Formation permissions.




**Step 21:** Go to [Lake Formation console](https://us-west-2.console.aws.amazon.com/lakeformation/home?region=us-west-2#databases).

Select `c360view_analytics` database -> Actions -> Grant.

![qs2](/images/qs/qs-00.png)

Grant your quicksight user permissions to `c360view_analytics` database.


**Step 22:** Go to [tables](https://us-west-2.console.aws.amazon.com/lakeformation/home?region=us-west-2#tables) in Lake Formation.

Select c360denormalized -> Actions -> Grant.

Grant your quicksight user the following permissions to `c360denormalized` table.


![qs2](/images/qs/qs--12.png)


**Step 23 :**  Go to [Quicksight console](https://us-west-2.quicksight.aws.amazon.com/sn/start), US West (Oregon) region.


![qs2](/images/qs/qs-07.png)

**Step 24:**   Click on Datasets -> New dataset.

![qs2](/images/qs/qs-08.png)


**Step 25:**   Choose Athena for Data sources.

![qs2](/images/qs/qs-09.png)


**Step 26:**  New Athena data source.

Data source name: c360
Leave Athena workgroup as primary, and click on Create data source.


![qs2](/images/qs/qs-10.png)

**Step 27:**  Choose your table.

Database: contain sets of tables: c360view_analytics

Tables: contain the data you can visualize: c360denormalized


![qs2](/images/qs/qs--13.png)

Click on *Select.*


**Step 28:**  Choose Directly Query your data -> Visualize.


![qs2](/images/qs/qs--14.png)


**Step 29:**  From the field list choose `occupation`.


**Step 30:**  From the visual type select **Pie chart**.

![qs2](/images/qs/graph-1.png)


**Step 31:**  Click on *+ Add*, and then on Add new visual.

![qs2](/images/qs/graph-2.png)

**Step 32:**  Select the following fields.

- head_of_household_flag
- marital_status
- l3mcredit_avg

**Step 33:**  Click on **Field wells** to check everything is in the correct place.

![qs2](/images/qs/graph-3.png)
