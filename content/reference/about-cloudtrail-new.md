# Configure AWS CloudTrail Log Collection

[ENG-17219](https://alertlogic.atlassian.net/browse/ENG-17219): We are missing contextual information and information about requirements for CloudTrail. Much of this can go into this doc:

A customer recently had a huge charge on their AWS account due to CloudTrail and was looking for someplace in the documentation where that is noted. It is not clear.

Questions to answer:

* What all do we need the customer to have set up?
* How does our collection work?
* How could it possibly result in customer charges (ie, we turn on the default CloudTrail on their accounts)

AWS CloudTrail is an Amazon Web Services (AWS)  service that logs all of your AWS account activity. AWS CloudTrail records actions taken by a user, role, or AWS service as events. Recorded actions include those taken in the AWS Management Console, AWS Command Line Interface, and AWS SDKs and APIs.

AWS CloudTrail is enabled on your AWS account when you create it. AWS allows you to create additional trails to record events in specific regions and deliver them to a specified S3 bucket. For more information, see the AWS document [How CloudTrail Works](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/how-cloudtrail-works.html).

## How Alert Logic products work with AWS CloudTrail

Alert Logic products treat API activity data as any another data source to capture and manage. Alert Logic Network IDS and Alert Logic Log Management with LogReview integrate with AWS CloudTrail to collect API activity data within an AWS account, and then combines the data with log data from other applications and systems.

## AWS CloudTrail setup

When you create an AWS deployment in the Alert Logic console and set up your IAM roles with correct permissions, Alert Logic automatically starts collecting CloudTrail logs. Automatic collection requires that you provide access to your:

* S3 bucket that stores your CloudTrail logs
* SNS topic that receives notifications when log files are delivered
* SQS queue subscribed to the SNS topic for the CloudTrail

### Continual asset monitoring

When you create an AWS deployment in the Alert Logic console, you can configure the deployment with centralized AWS CloudTrail log collection to provide continual asset updates.

AWS allows you to use a separate, dedicated account with AWS CloudTrail enabled to centralize your AWS CloudTrail log collection, which requires a second IAM role to allow Alert Logic to access the AWS receiving account that collects AWS CloudTrail data. For more information, see [Should you centralize CloudTrail log collection?](../prepare/aws-cross-account-role-setup.md#ShouldyoucentralizeCloudTraillogcollection)

### Incident management

Amazon GuardDuty is a continuous security monitoring service that requires no customer-managed hardware or software. GuardDuty analyzes and processes VPC Flow Logs and AWS CloudTrail event logs. GuardDuty uses security logic and AWS usage statistics techniques to identify unexpected and potentially unauthorized and malicious activity, such as:

* Escalations of privileges
* Uses of exposed credentials
* Communication with malicious IPs, URLs, or domains

For more information, see [Integrate Amazon GuardDuty Findings into Alert Logic Incidents](../configure/integrate-guard-duty-findings.md#integrate-gd-findings).

### Compliance goals

Alert Logic uses AWS CloudTrail data to identify potential compliance issues or threats through our analytics and reporting features.

    The security and compliance goals of your organization could require you to create and configure additional trails. For example, you must configure separate AWS CloudTrail logs for discovery of your AWS assets, and for Log Management.    ## CloudTrail configuration monitoring and updates

Alert Logic periodically checks for CloudTrail configuration changes in your environment  and attempts to fix any issues. You can use the information in the following table to understand what happens automatically when your configuration changes and troubleshoot issues that cannot be detected and fixed automatically.

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
