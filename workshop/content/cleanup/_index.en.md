+++
title = "Cleanup"
menuTitle = "Cleanup"
date = 2020-08-28T08:56:14-05:00
weight = 80
chapter = true
pre = "<b>7. </b>"
+++


After playing with the environment to Cleanup the resources:

- Disable or delete all the [CloudWatch schedules](https://us-west-2.console.aws.amazon.com/cloudwatch/home?region=us-west-2#cw:dashboard=Home) created to avoid creating new data;

- Empty your c360view [S3 buckets](https://s3.console.aws.amazon.com/s3/home?region=us-west-2);

- Go to [CloudFormation console](https://us-west-2.console.aws.amazon.com/cloudformation/home?region=us-west-2) to delete the whole c360view stack
  - this will delete your transactional database RDS, EMR cluster and all the other resources.


- To cancel your Quicksight subscription, only if your are not going to use it in your account:
  - Go to [Quicksight in N.Virgina region](https://us-east-1.quicksight.aws.amazon.com/sn/admin#)
  - Account settings -> Unsubscribe
