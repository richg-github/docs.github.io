# About AWS CloudTrail and Alert Logic

AWS CloudTrail is an Amazon Web Services (AWS)  service that logs all of your AWS account activity. CloudTrail records actions taken by a user, role, or AWS service as events. Recorded actions include those taken in the AWS Management Console, AWS Command Line Interface, and AWS SDKs and APIs.

AWS CloudTrail is enabled on your AWS account when you create it. AWS allows you to create additional trails to record events in specific regions and deliver them to a specified S3 bucket. For more information, see the AWS document [How CloudTrail Works](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/how-cloudtrail-works.html).

[ENG-17219](https://alertlogic.atlassian.net/browse/ENG-17219): We are missing contextual information and information about requirements for CloudTrail. Much of this can go into this doc:

A customer recently had a huge charge on their AWS account due to CloudTrail and was looking for someplace in the documentation where that is noted. It is not clear.

Questions to answer:

* What all do we need the customer to have set up?
* How does our collection work?
* How could it possibly result in customer charges (ie, we turn on the default CloudTrail on their accounts)

## How Alert Logic products work with AWS CloudTrail

Alert Logic products treat AWS API activity data as any other data source to capture and manage. Alert Logic Network IDS and Alert Logic Log Management with LogReview integrate with AWS CloudTrail to collect API activity data within an AWS account, and then combines the data with log data from other applications and systems.

### Continual asset monitoring

When you create an AWS deployment in the Alert Logic console, you can configure the deployment with centralized AWS CloudTrail log collection to provide continual asset updates.

AWS allows you to use a separate, dedicated account with AWS CloudTrail enabled to centralize your AWS CloudTrail log collection, which requires a second IAM role to allow Alert Logic to access the AWS receiving account that collects AWS CloudTrail data. For more information, see [Should you centralize CloudTrail log collection?](../prepare/aws-cross-account-role-setup.md#ShouldyoucentralizeCloudTraillogcollection).

### Log Management

You can create an AWS CloudTrail that Alert Logic can use to collect, store, and make searchable for any type of operational activity. For more information, see [Log Sources](../deploy/log-sources.md).

If you  have an Alert Logic MDR Professional or Alert Logic MDR Enterprise subscription with the Log Management add-on and configured the AWSdeployment with centralized AWS CloudTrail log collection, Alert Logic collects CloudTrail log messages automatically. For more information, see [Should you centralize CloudTrail log collection?](../prepare/aws-cross-account-role-setup.md#ShouldyoucentralizeCloudTraillogcollection).

The collected CloudTrail event logs are available for log search and log correlations. For more information, see [Search: Log Messages](../analyze/log-message-search.md) and [Correlations and Notifications](../configure/notifications/log-correlation.md).

### Incident management

Amazon GuardDuty is a continuous security monitoring service that requires no customer-managed hardware or software. GuardDuty analyzes and processes VPC Flow Logs and CloudTrail event logs. GuardDuty uses security logic and AWS usage statistics techniques to identify unexpected and potentially unauthorized and malicious activity, such as:

* Escalations of privileges
* Uses of exposed credentials
* Communication with malicious IPs, URLs, or domains

For more information, see [Integrate Amazon GuardDuty Findings into Alert Logic Incidents](../configure/integrate-guard-duty-findings.md#integrate-gd-findings).

### Compliance goals

Alert Logic uses CloudTrail data to identify potential compliance issues or threats through our analytics and reporting features.

    The security and compliance goals of your organization could require you to create and configure additional trails. For example, you must configure separate AWS CloudTrail logs for discovery of your AWS assets, and for Log Management.    ## CloudTrail setup

If you configure an AWS deployment in Automatic Mode with full permission, Alert Logic sets up CloudTrail for you automatically. For technical details about how Alert Logic sets up CloudTrail and responds if your CloudTrail configuration changes, see [How Alert Logic sets up CloudTrail](cloudtrail-setup.md).
