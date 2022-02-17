# Upgrades to S3 collection in Managed Detection and Response

    This document is intended for customers with an Alert LogicAlert Logic Cloud Defender who are preparing to upgrade  to Managed Detection and Response (MDR).    
Amazon Web Services (AWS) S3 collection performance, configuration, and efficacy have all been improved on the Managed Detection and Response (MDR) platform.

## Upgrades to Performance

The Cloud Defender S3 collection service used a poll-based mechanism to analyze objects in the S3 bucket, which required the repeated counting of all objects at the time of each poll. The calculation of new and missing objects (changes) could take a considerable amount of time for buckets with millions of objects. Polling frequency in Cloud Defender is every 15 minutes, which was in addition to any time added during the calculation of differences between polls.

Furthermore, S3 collection polling was done at the Alert Logic system level, meaning that the delays caused by customers with massive S3 buckets would lead to delays to other collectors that are waiting in queue.

The MDR S3 collection service is event based. It does not need to poll the entire S3 bucket and then calculate changes between the prvious and current poll. Polling frequency relies on notifications from SQS queues, which are dynamic and generally much more frequent.

Finally, the MDR collectors are deployed independent of one another, and the performance of customer's with massive S3 buckets will no longer affect other environments.

## Upgrades to configuration

The MDR S3 collector takes fewer steps to configure. Users are required to provide target bucket name and a valid IAM role only. From there, the bucket can be polled. Users can optionally set up an SQS queue for each bucket.

In the AWS console, users must configure an SNS topic with the correct policy and buckets notifications to be configured to send notifications to that topic in addition to the IAM role.

Only one SNS topic needs to be created for the MDR S3 collector, as multiple buckets can push their notifications to a single topic to consolidate collection. Cloud Defender S3 collectors required a queue per bucket approach, which added to the complexity of configuration.

## Upgrades to using S3 information in the Alert Logic console

MDR S3 collection feeds into the Health Console, which enables users to use Exposure and Remediation workflows to identify S3 collection issues and quickly resolve them.

The Alert Logic console supports an easier configuration experience. For more information, see [Configure Amazon S3 Log Collector](../configure/collectors/amazon-s3.md).
