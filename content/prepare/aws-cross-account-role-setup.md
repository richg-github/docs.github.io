# AWS Cross-account Role Setup

Alert Logic supports Amazon Web Services (AWS) cross-account roles. The  Deployments page in the Alert Logic console allows you to create deployments for your AWS accounts. On this page, you can edit an AWS deployment name, add and edit AWS credentials to provide Alert Logic with cross-account access to those accounts, and delete deployments. For more information about deployments, see [Get Started with Alert Logic Deployments](../get-started/deployments.md).

## Before you begin

Before Alert Logic can manage the protection of your AWS accounts, you must:

* Log into your AWS account to create a cross-account role to allow Alert Logic to access your AWS accounts. To learn how to create a cross-account role, see [Create a cross-account access role](iam-role-creation.md#top).
* Log into the Alert Logic console to configure credentials for each discovered AWS deployment.
* Determine whether you want to configure cross-account for centralized CloudTrail log collection. For more information about centralized log collection, see [Should you centralize CloudTrail log collection?](#ShouldyoucentralizeCloudTraillogcollection).

The use of centralized CloudTrail log collection affects how you configure cross-account access for your deployment. You should make this decision prior to configuration of your deployment. To learn more about CloudTrail, see [About AWS CloudTrail and Alert Logic](../reference/about-cloudtrail.md).

### About AWS cross-account roles

Cross-account roles allow Alert Logic to access your AWS account. AWS role creation requires that you provide an AWS policy, a document that specifies the permissions assigned to the AWS role you create for Alert Logic to access your AWS account.

When you create a role to provide Alert Logic cross-account access to your AWS accounts, you provide better protection for those accounts with:

* Improved agent lifecycle management
* Optimized appliance deployments
* Auto-detection of new assets and changed configurations

Alert Logic recommends that you configure your deployment with full permissions,  which allows Alert Logic to discover your AWS environment and  automate the setup of the required AWS services. However, you can choose from the following levels of permissions:

* (Recommended) [Configure AWS Full Permission Deployment](aws-full-permission-deployment.md#Configur)—Allows Alert Logic to make all the necessary changes to your AWS account.
* [Configure  AWS Minimal Permission Deployment in Manual Mode](aws-minimal-permission-deployment.md#top)—Allows you to maintain full control over the changes in your deployment, and requires you to perform any necessary actions manually.

The full permission policy document does not allow Alert Logic to:

* Retrieve secret keys or credentials from IAM
* Retrieve data from data stores other than S3
* Perform these actions from any other AWS account
* Grant access to the protected account to any other AWS account or user
* Modify IAM credentials or policies

To complete configuration or edit cross-account access in the Alert Logic console, click an AWS deployment tile on the Deployments page, and then provide your AWS role ARN and the External ID.

    If you create a deployment with one level of permissions, and then want to switch to another level of permissions, you can create another IAM role with the appropriate level of permissions (if you do not already have that role configured). Then, click **edit** on the deployment tile to change your deployment configuration to use the appropriate role.     ### Update your IAM roles

Periodically, Alert Logic updates the policy documents used for the IAM roles required for AWS deployments. These updates, which Alert Logic announces in [Alert Logic Console Release Notes](../release-notes/alert-logic-console.md), ensure you can successfully create deployments, and they ensure your existing deployments continue to monitor your AWS assets.

Before you update your IAM roles,  download and open the appropriate policy document below. Keep the document open so you can copy and paste information during IAM role creation.

* [Full-permission deployment policy document](../pdf-files/defender.json)
* [Minimum permission deployment policy document](../pdf-files/defender-min.json)

To update an IAM role, see [Update an IAM role](iam-role-creation.md#UpdateanIAMrole). Perform this procedure for every IAM role you need to update.

### Should you centralize CloudTrail log collection?

AWS allows you to use a separate, dedicated account with CloudTrail enabled to centralize your CloudTrail log collection, which requires a second IAM role to allow Alert Logic to access the AWS receiving account that collects CloudTrail data.

If you provide cross-account access to the AWS receiving account for centralized log collection, you get near-real-time updates about your assets. Without this cross-account access, the Alert Logic console refreshes information about your assets every 12 hours.

If you  have an Alert Logic MDR Professional or Alert Logic MDR Enterprise subscription with the Log Management add-on and provide cross-account access to the AWS receiving account, the collected CloudTrail event logs are also available for log search and log correlations. For more information, see [Search: Log Messages](../analyze/log-message-search.md) and [Correlations and Notifications](../configure/notifications/log-correlation.md).

    You must configure separate AWS CloudTrail logs for discovery of yourAWS assets and for Log Management. For more information, see LINKY.
