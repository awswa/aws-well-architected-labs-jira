---
title: "Catalog the workload data"
date: 2021-03-24T15:16:08+10:00
chapter: false
weight: 2
pre: "<b>2. </b>"
---

AWS Glue is a fully managed extract, transform, and load (ETL) service that makes it easy to prepare and load your data for analytics. AWS Glue provides crawlers to determine the schema and stores the metadata in the [ ](https://docs.aws.amazon.com/glue/latest/dg/components-overview.html#data-catalog-intro).

#### Create the Crawler

1.  Open the AWS Glue console, and from the left navigation pane, choose **Crawlers**.
2.  Select **Add crawler** and name the crawler `well-architected-reporting` select **Next**.
3.  Select **Add a data source**.
    1.  Under **S3 path** Click **Browse** and select the S3 bucket where you will store the extracted AWS Well-Architected data e.g. `s3://well-architected-reporting-blog`. Select the radio button next to the path where you stored the workload data, e.g. `WorkloadReports` and select **Choose**
4.  Select **Add S3 data source** and then **Next** on **Choose data sources**.
5.  Select **Create an IAM role** and provide a name, e.g. `well-architected-reporting` , select **Next**.
6.  Select **Run on demand** as the schedule frequency. Select **Next**.
7.  Next select **Add database**, and fill-in a name e.g. `war-reports`. Select **Create** and then **Next**.
8.  Review the configuration and select **Finish** to create the Crawler.

![Image of Crawler configuration.](/Well-ArchitectedTool/300_Labs/300_Building_custom_AWS_Well-Architected_reports_with_Amazon_Athena_and_Amazon_QuickSight/Images/fig-5-glue-crawler-config.png)


#### Run the Crawler

1.  Find the crawler that was just created, select it, and then choose **Run Crawler**.
2.  Wait for the crawler to complete running, which should take approximately one minute.
3.  From the left navigation pane, choose **Databases**.
4.  Find the database that was created during the Crawler creation, select it and choose **View Tables**.
5.  In the **Name** field, you should see "workloadreports". Select this and examine the metadata that was discovered during the crawler run, as shown in Figure 6. ![The workloadreports table details include fields for database, classification, location, last updated, input format, table properties, and more. The Schema section of the page displays columns for column name, data type, partition key, and comment.](/Well-ArchitectedTool/300_Labs/300_Building_custom_AWS_Well-Architected_reports_with_Amazon_Athena_and_Amazon_QuickSight/Images/fig-6-workloadsreport-table.png)


{{< prev_next_button link_prev_url="../" link_next_url="../3_query_data/" />}}
