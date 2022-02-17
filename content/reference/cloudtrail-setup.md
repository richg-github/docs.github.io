# How Alert Logic sets up CloudTrail

If you configure an AWS deployment in Automatic Mode with the Alert Logic CloudFormation template, Alert Logic sets up AWS CloudTrail for you automatically as explained in this document.

For information about how to configure an AWS deployment to take advantage of automatic setup, see [Configure AWS Full Permission Deployment](../prepare/aws-full-permission-deployment.md).

## AWS account types

Explanations that follow refer to these types of AWS accounts:

* **Protected account**—The account protected by Alert Logic

* **Receiving account**—The account that owns the S3 bucket where a CloudTrail trail is configured to store its log files

Full permission deployment allows CloudTrail setup in either the protected account or in the separate receiving account (master account for a CloudTrail organization trail). Alert Logic sets up the CloudTrail  in the receiving account if the user chooses to configure centralized CloudTrail log collection during deployment configuration.

## Requirements for automatic setup

If you want Alert Logic to set up CloudTrail automatically, you must configure a full permission AWS deployment as explained in [Configure AWS Full Permission Deployment](../prepare/aws-full-permission-deployment.md).

CloudTrail setup in a receiving account requires that you choose the option for configuring centralized log collection and then provide cross-account credentials, which is also explained  in [Configure AWS Full Permission Deployment](../prepare/aws-full-permission-deployment.md).

Full permission deployment grants Alert Logic permissions to make these changes to your environment:

* Enable or modify AWS CloudTrail settings
* Create an Amazon SQS queue and an Amazon SNS topic
* Modify permissions

Organization trails have additional requirements:

* An organization trail must have an existing S3 bucket and SNS topic. If either is missing, setup fails with an error message.
* Alert Logic can only reuse an organization trail  for multiple regions. Single-region organization trails are not supported. An error occurs and Alert Logic does not attempt to reuse any other available trail.

When you create an AWS deployment in the Alert Logic console and set up your IAM roles with correct permissions, Alert Logic automatically starts collecting CloudTrail logs. Automatic collection requires that you provide access to your:

* S3 bucket that stores your CloudTrail logs
* SNS topic that receives notifications when log files are delivered
* SQS queue subscribed to the SNS topic for the CloudTrail

## Alert Logic trail installation

If you already have a CloudTrail trail set up in your AWS account, Alert Logic tries to reuse the existing trail. If your account does not have a trail set up for delivering CloudTrail events to an Amazon S3 bucket, Alert Logic creates an "AlertLogicCT" trail in your account for you.

Alert Logic picks a CloudTrail trail for reuse among existing trails according to the following priorities:

1. ControlTower organizational trail
2. Any other organizational trail
3. Trail named "AlertLogicCT"
4. Multiregion trail named "Default"
5. Any other multiregion cloud trail
6. Trail named "Default"
7. The first trail from the list sorted by name

The following table describes how Alert Logic creates trails, depending on combinations of whether:

* A trail exists and the type of trail
* An S3 bucket  exists and if it is for the protected or receiving account
* An SNS topic exists and if it is for the protected or receiving account
* Cross-account credentials for centralized log collection exist

| No.  | Existing Trail | Existing S3 Bucket | Existing SNS Topic | Centralized log collection | Alert Logic S3 Bucket | Alert Logic SNS Topic | Alert Logic SQS Queue |
|---|---|---|---|---|---|---|---|
| 1 | No | X | X | No | protected | protected | protected |
| 2 | No | X | X | Yes | receiving | receiving | receiving |
| 3 | Yes | protected | X | No | reuse | protected | protected |
| 4 | Yes | protected | X | Yes | reuse | protected | protected |
| 5 | Yes | protected | protected | No | reuse | reuse | protected |
| 6 | Yes | protected | protected | Yes | reuse | reuse | protected |
| 7 | Yes | receiving | any | No | Missing credentials error | X | X |
| 8 | Yes | receiving | X | Yes | reuse | receiving | receiving |
| 9 | Yes | receiving | receiving | Yes | reuse | reuse | receiving |
| 10 | Yes | receiving | protected | Yes | reuse | reuse | receiving |
| 11 | Yes | protected | receiving | No | Missing credentials error | X | X |
| 12 | Yes | protected | receiving | Yes | protected | receiving | protected |
| 13 | Yes (organizational) | X | No | Org. trail without topic error | X | X | X |
| 14 | Yes (organizational single region) | Org. trail single region error | X | X | X | X | X |
| 15 | Yes (organizational) | Yes | Yes | Yes | reuse | reuse | master |
| 16 | Yes (organizational) | Yes | Yes | No | Missing credentials error | X | X |
| 17 | Yes (ControlTower) | Yes | Yes | Yes | reuse | reuse | receiving |

For organizational trails, an existing S3 bucket and SNS topic are required. If either is missing, setup fails with an error message.

Alert Logic always installs the SQS queue in the same AWS account where the S3 bucket for storing CloudTrail events is located.

### CloudTrail setup if a trail does not exist 

If no CloudTrail trail exists in the target AWS account, Alert Logic sets up CloudTrail as follows.

In these steps, Alert Logic replaces placeholder information as follows:

* The customer's account ID replaces `[CustomerAccountId]`. An example  is 12345678.
* The native AWS account on which the resources exist replaces `[AWSAccountId]`. An example is 123456789012.

Alert Logic sets all permissions within the IAM role policy for the associated AWS resource.

1. If an S3 bucket named `outcomesbucket-[CustomerAccountId]` does not already exist, Alert Logic creates it (see the AWS document [Creating a bucket](https://docs.aws.amazon.com/AmazonS3/latest/gsg/CreatingABucket.html)), ensuring the following permissions are set:| <<"s3:ListBucket">> |
| <<"s3:GetBucketLocation">> |
| <<"s3:GetObject">> |
| <<"s3:GetBucket*">> |
| <<"s3:GetLifecycleConfiguration">> |
| <<"s3:GetObjectAcl">> |
| <<"s3:GetObjectVersionAcl">> |
2. If an SNS topic named `outcomestopic` does not already exist, Alert Logic creates it (see the AWS document [Getting started with Amazon SNS](https://docs.aws.amazon.com/sns/latest/dg/sns-getting-started.html)), ensuring the following permissions are set:| <<"sns:ListSubscriptions">> |
| <<"sns:ListSubscriptionsByTopic">> |
| <<"sns:ListTopics">> |
| <<"sns:GetEndpointAttributes">> |
| <<"sns:GetSubscriptionAttributes">> |
| <<"sns:GetTopicAttributes">> |
3. Alert Logic creates a trail to publish data to the S3 bucket and send notifications to the SNS topic (see the AWS document [Creating a Trail For Your AWS Account](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-create-and-update-a-trail.html)).
4. If an SQS queue named `outcomesbucket-[CustomerAccountId]` does not already exist, Alert Logic creates it, ensuring the following permissions are set (see the AWS document [What is Amazon Simple Queue Service?](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/welcome.html)).
Alert Logic creates the SQS queue in the AWS us-east-1 region. If the region needs to be changed, a deployment config must be updated first.| <<"sqs:GetQueueAttributes">> |
| <<"sqs:ReceiveMessage">> |
| <<"sqs:DeleteMessage">> |
| <<"sqs:GetQueueUrl">> |
| <<"sqs:ListQueues">> |
5. Alert Logic configures the IAM policies for the above resources as follows (see the AWS document ).

## When to contact Alert Logic about CloudTrail configuration changes

If you disable a CloudTrail trail that Alert Logic uses and configure a new one, contact Technical Support and let them know that you want Alert Logic to use the new trail.

Alert Logic re-creates a deleted trail, so it Alert Logic always tries to reuse an existing CloudTrail trail to reduce AWS costs. associated with multiple trails.

## CloudTrail configuration monitoring and updates

If you configured AWS with full permissions, Alert Logic periodically checks for CloudTrail configuration changes in your environment  and attempts to fix any issues. You can use the information in the following table to understand actions that occur automatically when your configuration changes and troubleshoot issues that cannot be detected and fixed automatically.

| If this happens | Alert Logic does this |
|---|---|
| CloudTrail configuration that Alert Logic used is deleted | Reinstalls a new CloudTrail or reuses an existing one |
| S3 bucket [for CloudTrail collection?] is reassigned | Picks this configuration and reads messages from the new bucket |
| S3 bucket inline policy is changed | Alert Logic does not validate an existing CloudTrail bucket policy. Alert Logic only applies the default S3 bucket CloudTrail policy if a protected AWS account does not have CloudTrail set up |
| S3 bucket is deleted | Creates a default bucket named ` outcomes-<AWS account id>` |
| SNS topic is changed | Picks up this configuration |
| SNS topic inline policy is changed | Applies default SNS policy if new one fails `aws_validator:match()` |
| SNS topic is deleted | Re-creates a default topic `outcomestopic` |
| SQS subscription is removed | This case cannot be detected. |
| SQS inline policy is changed | If the new policy fails, applies the default SQS policy  `aws_validator:match()` |
| SQS is deleted | Re-creates the queue |
