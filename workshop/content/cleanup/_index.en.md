+++
title = "Cleanup"
menuTitle = "Cleanup"
date = 2020-08-28T08:56:14-05:00
weight = 70
chapter = true
pre = "<b>6. </b>"
+++


After playing with the environment to Cleanup the resources:

-  disable or delete all the [CloudWatch schedules](https://us-west-2.console.aws.amazon.com/cloudwatch/home?region=us-west-2#cw:dashboard=Home) created to avoid creating new data;

- empty your c360view [S3 buckets](https://s3.console.aws.amazon.com/s3/home?region=us-west-2);

- go to CloudFormation console to delete the whole c360view stack
  - this will delete your transactional database RDS, EMR cluster and all the other resources.
