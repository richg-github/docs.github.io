# Configure Custom AWS CloudTrail Log Collector/Collection?

This is the topic that will explain that CloudTrail is already configured if they set up their deployment with the correct permissions and how to check.

    CloudTrail logs are automatically collected through the deployment role. To confirm that Alert Logic is collecting CloudTrail logs from your environment, click here. For more information about how Alert Logic automatically integrates with CloudTrail, see [About AWS CloudTrail and Alert Logic](../../reference/about-cloudtrail.md)
In some cases, you may want to configure custom CloudTrail logs:

* You have set up additional Trails that you want Alert Logic to monitor.
* 

If you see a check mark, check Configured Applications, or check the Health page?

AWS CloudTrail is an Amazon Web Services (AWS)  service that logs all of your AWS account activity. AWS CloudTrail records actions taken by a user, role, or AWS service as events. AWS allows you to create trails to record events in specific regions and deliver them to a specified S3 bucket.

When you create an AWS deployment in the Alert Logic console and set up your IAM roles with correct permissions, Alert Logic automatically starts collecting CloudTrail logs with no further configuration required.

If your AWS deployment is configured with centralized log collection as explained in [Configure AWS Full Permission Deployment](../../prepare/aws-full-permission-deployment.md), no further configuration is required.

You can find  CloudTrail logs collected with keyword search in the Alert Logic console[Search: Log Messages](../../analyze/log-message-search.md) page. Alert Logic also generates security incidents from AWS Network Firewall logs in the [Incidents](../../analyze/incidents.md) page. For more information about authentication application security content, see [Authentication Application Security Incidents](../../analyze/security-incidents.md).

## Requirements for CloudTrail log collection

CloudTrail log collection requires that you provide access to your:

* S3 bucket that stores your CloudTrail logs
* SNS topic that receives notifications when log files are delivered
* SQS queue subscribed to the SNS topic for the CloudTrail

If your deployment was configured in Automatic Mode with full permissions and centralized log collection (see ), Alert Logic collects CloudTrail logs automatically.

The deployment can also be set up manually

Automatic collection of CloudTrail logs occurs if:

as explained in [Configure AWS Full Permission Deployment](../../prepare/aws-full-permission-deployment.md).

choose the option for configuring centralized log collection and then provide cross-account credentials, which is also explained  in [Configure AWS Full Permission Deployment](../../prepare/aws-full-permission-deployment.md).

If you configured the deployment in Manual Mode,

### Additional resources

To learn more about Alert Logic and CloudTrail, see:

* [About AWS CloudTrail and Alert Logic](../../reference/about-cloudtrail.md)—Defines Alert Logic scan types, recommends best practices for vulnerability scans, and lists originating IP addresses for scans.
* [How Alert Logic sets up CloudTrail](../../reference/cloudtrail-setup.md)—Explains default scan schedules and how to create and manage scan schedules, stop a scan in progress, and exclude assets from vulnerability scanning.
* [Adjust Scan Settings](../../analyze/manage-scans-and-results/adjust-settings.md)—Explains how to manage credentials, adjust scan performance, and use Scan Now to perform an immediate scan on an asset.
* [Analyze Scan Results](../../analyze/manage-scans-and-results/analyze-results.md)—Explains how to analyze scan results by viewing vulnerability reports and by viewing exposures, along with remediations for the exposures, that Alert Logic generates for detected vulnerabilities.
* [Alert Logic Scanning Technical Description](../../reference/scans-technical-description.md)—Explains host discovery and each segment of the scanning process. It provides other important details about handling of complex passwords, scanning depth, handling of backported patches, vulnerabilities detected by the scanning system, and the vulnerability and exposure library that Alert Logic uses.

### Continual asset monitoring

When you create an AWS deployment in the Alert Logic console, you can configure the deployment with centralized AWS CloudTrail log collection to provide continual asset updates.

AWS allows you to use a separate, dedicated account with AWS CloudTrail enabled to centralize your AWS CloudTrail log collection, which requires a second IAM role to allow Alert Logic to access the AWS receiving account that collects AWS CloudTrail data. For more information, see [Should you centralize CloudTrail log collection?](../../prepare/aws-cross-account-role-setup.md#centralize-ct-collection)

### Incident management

Amazon GuardDuty is a continuous security monitoring service that requires no customer-managed hardware or software. GuardDuty analyzes and processes VPC Flow Logs and AWS CloudTrail event logs. GuardDuty uses security logic and AWS usage statistics techniques to identify unexpected and potentially unauthorized and malicious activity, such as:

* Escalations of privileges
* Uses of exposed credentials
* Communication with malicious IPs, URLs, or domains

For more information, see [Integrate Amazon GuardDuty Findings into Alert Logic Incidents](../integrate-guard-duty-findings.md#integrate-gd-findings).
