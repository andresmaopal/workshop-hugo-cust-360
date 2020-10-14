+++
title = "Data Load and Orchestration"
menuTitle = "Load Data"
date = 2020-08-28T08:56:14-05:00
weight = 10
chapter = true
pre = "<b>2. </b>"
+++

You will use lambda functions to generate data via schedulers in CloudWatch, AWS Lake Formation to catalog, load and manage your Data lake.

![bp 1](/images/lakeformation/hhug-load-data.png)

You are going to generate some synthetic data using Scheduled AWS Lambda functions.

AWS Lambda lets you run code without provisioning or managing servers. You pay only for the compute time you consume. On this case the code is in Python to generate synthetic data.


AWS Lake Formation is a service that makes it easy to set up a secure data lake in days. Creating a data lake with Lake Formation is as simple as defining data sources and what data access and security policies you want to apply. Lake Formation then helps you collect and catalog data from databases and object storage, move the data into your new Amazon S3 data lake, clean and classify your data using machine learning algorithms, and secure access to your sensitive data.


![bp 1](/images/lakeformation/palacan-pic-lf00.png)
