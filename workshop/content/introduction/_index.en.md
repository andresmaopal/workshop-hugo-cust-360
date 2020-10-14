+++
title = "Build a 360 degree customer view"
chapter = true
weight = 1
+++

A very common use case is that organizations often look at their customers from different perspectives, such as Loyalty perspective, looking at metrics like: years of history,
frequency of interaction, or a demographic perspective like stage of life or income. We call them dimensions, and we will combine several dimensions about your customer to
give you more visibility of several perspectives at the same time.

In this blog we will explore a hypothetic financial services company, as there are
common dimensions for this industry and some dimensions that are also valid for any
service industry, like marketing and communications, customer history or demographic
dimension.

![cust_360_dimensions](/images/intro/cust_360_dimensions.png)


Workshop architecture diagram:
![cust_360_diagram](/images/intro/hhug_intro.png)

We use AWS Lake Formation blue prints to orchestrate the extraction from the relational database to Amazon S3, using AWS Glue connector and Glue jobs.
Then on the bottom we have the persistent layer on Amazon S3 the base for our Data lake strategy, with Raw, Stage and Analytics buckets.

For processing we are counting with Step Functions orchestrating AWS Lambda using Athena on the top, we also have AWS Glue Jobs, using Spark and Python, and Amazon EMR using Spark and Hive to transform and aggregate data.

To consume the data, we have Amazon Athena query engine console and API, and Amazon DynamoDB console and API.

In this workshop you will use different sources of data to build a 360-degree Customer view using powerful AWS tools for analytics.



| Domain	|Data source	|Source Format	|source column name
|---------|-------------|---------------|------------------
|Customer info	|CRM	|API - json	|client_id|
|   |   |    |age
|   |   |    |date_Of_Birth
|   |   |    |home_ownserhip_status
|   |   |    |occupation
|   |   |    |marital_Status
|   |   |    |head_of_household_flag
|   |   |    |client_created_date
|   |   |    |
|Transactions	|Mainframe sources	|Relational Database	|trans_id
|   |   |    |account_id
|   |   |    |date
|   |   |    |type
|   |   |    |operation
|   |   |    |amount
|   |   |    |balance
|   |   |    |
|Credit Card	|Card origination system	|Text file - from Mainframe	|card_id
|   |   |    |disp_id
|   |   |    |type
|   |   |    |issued_datetime
|   |   |    |
|Account	|Account origination system	|Text file - from Mainframe	|account_id
|   |   |    |branch_ID
|   |   |    |frequency
|   |   |    |creation_date
|   |   |    |
|General banking	|Dispositions Database	|Text file - from Mainframe	|disp_id
|   |   |    |client_id
|   |   |    |account_id
|   |   |    |type
|   |   |    |
|web_analytics	|Google Analytics	|json with nested fields	|client_id
|   |   |    |visitNumber
|   |   |    |visitId
|   |   |    |visitStartTime
|   |   |    |Date
|   |   |    |Totals
|   |   |    |trafficSource
|   |   |    |device
|   |   |    |geoNetwork
|   |   |    |customDimensions
|   |   |    |Hits
|   |   |    |fullVisitorId
|   |   |    |userId
|WebVisitor map	|Map web visitors to client_id	|Text file	|visitorId hash
|   |   |    |client_id
