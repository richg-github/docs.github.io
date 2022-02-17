# Migration Prechecks

Before you upgrade to Managed Detection and Response (MDR), Alert Logic performs a migration precheck to identify issues in your environment that can block your upgrade or affect its success. The following information explains the  issues that the precheck can find, when the issues must be resolved, and how to resolve them.

You can use the information to prevent each issue, or you can wait for the precheck results and use the information to resolve specific issues that Alert Logic notifies you about.

## Must resolve before migration

The following issues block a successful migration and must be resolved before your upgrade.

* [Outdated AWS IAM role](#OutdatedAWSIAMrole)
* [AWS deployments with no credentials](#AWSdeploymentswithnocredentials)
* [Azure deployments with no credentials](#Azuredeploymentswithnocredentials)
* [Cloud deployments that are not in OK status](#ClouddeploymentsthatarenotinOKstatus)
* [Alert Logic agent version outdated](#AlertLogicagentversionoutdated)

### Outdated AWS IAM role

AWS deployments must have the latest Alert Logic policy document attached to the IAM role. This issue indicates that a role is using an outdated policy document.

**To get the latest policy and update the IAM role:**

1. In the Alert Logic console, browse to the Deployments page, click the relevant deployment tile, and then click **AWS Instructions**.
2. Under Step 2e, click **Copy Policy**.
3. In the AWS console, replace the existing IAM policy  for the role in use for this deployment with the copied policy.

For more information, such as how to check for this issue and detailed instructions for replacing the policy in the AWS console, see [Update AWS IAM Roles to Prepare for Upgrade](../get-started/update-aws-roles-for-upgrade.md).

### AWS deployments with no credentials

AWS deployments must have an IAM role configured. This issue indicates that you need to finish configuring  a deployment in the Alert Logic console.

To check for this issue prior to the migration precheck, browse to the Deployments page in the Alert Logic console, click an AWS deployment tile, and then click **AWS Role**. If the **ARN** field is blank, you need to create an AWS IAM role.

**To create an AWS IAM role:**

1. In the Alert Logic console, browse to the Deployments page, click the relevant deployment tile, and then click **IAM Role Setup**.
2. Click **CLOUDFORMATION SETUP** (recommended) or **OR PROCEED WITH MANUAL SETUP**, and then follow the instructions on the page. If you choose the CloudFormation method, the CloudFormation template completes steps in the AWS console for you.
3. In the Alert Logic console, click **AWS Role** in the left navigation for the deployment, paste the newly created ARN into the field, and then click **SAVE**.

### Azure deployments with no credentials

Azure deployments must have Role-Based Access Control (RBAC) configured with an app registration. This issue indicates that RBAC is not configured or was configured with a user credential method that is no longer supported.

To check for this issue prior to the migration precheck, browse to the Deployments page in the Alert Logic console, click an Azure deployment tile, and then click Azure** Subscription**. If the **Active Directory ID** and/or **Application ID** field is blank, you need to configure app registration and RBAC for the deployment.

To fix this issue, see the instructions in [Configure App Registration and RBAC for Microsoft Azure Resources](../prepare/azure-rbac-role-setup.md).

### Cloud deployments that are not in OK status

The cause of this issue is typically one of these issues: [Outdated AWS IAM role](#OutdatedAWSIAMrole), [AWS deployments with no credentials](#AWSdeploymentswithnocredentials), or [Azure deployments with no credentials](#Azuredeploymentswithnocredentials). If those issues are fixed, the likely cause is Azure deployments with permission errors.

For information about how to check for and fix Azure permission errors, see [Troubleshoot permission errors](../get-started/update-azure-deployments-for-upgrade.md#Troubleshootpermissionerrors).

### Alert Logic agent version outdated

If your agent version is older than 2.9.9, Alert Logic cannot migrate it. This issue can occur if the update policy for the agent is set to Never, which does not allow Alert Logic to update the agent  automatically when a new version is available.

To check for and fix the issue, complete the procedure [Modify an updates policy](https://legacy.docs.alertlogic.com/userGuides/threat-manager-policies.htm#Modifyanupdatespolicy) to check the update policy, and then choose **Automatic** if necessary.

If your updates policy is set to Automatic, you can wait for results of the precheck, and then update the agent manually, if necessary.

To reinstall the agent manually, you must uninstall the old version, and then download and install the latest one. For more information, see:

* [Uninstall the Alert Logic Agent for Linux](../prepare/alert-logic-agent-linux-uninstall.md)
* [Install the Alert Logic Agent for Linux](../prepare/alert-logic-agent-linux.md)
* [Uninstall the Alert Logic Agent for Windows](../prepare/alert-logic-agent-windows-uninstall.md)
* [Install the Alert Logic Agent for Windows](../prepare/alert-logic-agent-windows.md)

## Recommended but not required to fix before upgrade

These configuration issues do not prevent your upgrade, but Alert Logic recommends that you fix them. They complicate the network creation part of the upgrade and lead to many configuration exposures on the [Health](../analyze/health.md) page. You can improve the upgrade process and reduce post-migration tasks significantly by ensuring your deployments are in a healthy state before your upgrade.

* [Deployments with unassigned agents](#Deploymentswithunassignedagents)
* [Protected hosts, log sources, or appliances that are not in OK status](#ProtectedhostslogsourcesorappliancesthatarenotinOKstatus)

### Deployments with unassigned agents

Alert Logic recommends that you assign all protected hosts to an appliance or archive them before your upgrade to avoid this issue. This task prevents the creation of duplicate networks and reduces post-migration cleanup significantly.

To check for this issue prior to the migration precheck, browse to each of your deployments, click  **Networks and Protected Hosts**, and then click the **Protected Hosts** tab. Check for protected hosts in new status. To review the list, you can scroll or select the **By Source Status** filter and then click **Hosts in New State** to narrow results.

If a host is listed as new, click the edit icon (![](../Resources/Images/pencil icon.png)),  select an Assignment Policy, and then click **SAVE**.

Or, if you do not want to monitor this host for threats or collect its network traffic, click the archive icon (![](../Resources/Images/archive.png)), and then click **ARCHIVE**.

### Protected hosts, log sources, or appliances that are not in OK status

Items that are not in OK status are some of the most important issues to resolve before your upgrade. Alert Logic recommends that you fix these issues in advance for a smoother upgrade and fewer cleanup tasks post-migration. After the upgrade, any items that are not fixed appear as configuration exposures on the [Health](../analyze/health.md) page.

To check for these issues prior to the migration precheck, browse to each of your deployments, and then click an item in the left navigation to open the relevant page. For example, to view the list of protected hosts, click **Networks and Protected Hosts**, and then click the **Protected Hosts** tab. To review the list, you can scroll or select a status filter to narrow results.

**Protected hosts, log sources, or appliances are offline**— If you do not expect  the offline hosts or log sources to be in use going forward, Alert Logic recommends that you archive or delete  the item before the upgrade. For appliances that need to be removed, you can work with your Alert Logic implementation engineer or contact Technical Support.

**Protected hosts or log sources  are in error**—Investigate why the item is in an error status. Alert Logic recommends that you resolve as many of the errors as possible.  If a host is associated with the incorrect assignment policy, for example, this issue creates duplicate networks that require cleanup after the upgrade.

## Post-migration reconfiguration

If the following issues apply to your environment, they cannot be fixed until after your upgrade. Alert Logic recommends that you plan to work on them after your upgrade to achieve the same or similar outcomes in MDR.

* [AWS deployments with scanning appliance usage](#AWSdeploymentswithscanningapplianceusage)
* [Webhook usage](#Webhookusage)
* [Collection alerts usage](#Collectionalertsusage)
* [Scheduled report usage](#Scheduledreportusage)

### AWS deployments with scanning appliance usage

If you perform vulnerability scanning in your AWS environment currently, you must deploy the scanning appliance after migration. For more information, see [Deploy scanning appliances](../deploy/aws-manual-pro-ent.md#Deployscanningappliances) and [Scan Functionality Upgrade](../get-started/scans-upgrade.md).

### Webhook usage

If your webhooks were created on the  Cloud Defender platform before the new webhook connector experience, your webhooks do not migrate to MDR and must be reconfigured after your upgrade.  For more information, see [Webhook and Email Connectors](../configure/connectors.md).

### Collection alerts usage

In MDR, a health summary report notification replaces your Cloud Defender collection alerts. If you  subscribe to receive collection alerts, Alert Logic schedules the [Daily Health Summary](../analyze/reports/service/health/daily-health-summary.md) report for you and subscribes the same recipients to receive a notification when the report is generated. You can change the schedule and recipients or unsubscribe. For more information, see [Scheduled Reports and Notifications](../configure/notifications/report.md).

### Scheduled report usage

Your existing scheduled reports cannot be migrated because the Reports offering is upgraded in MDR. For help finding similar information from Cloud Defender Scheduled reports in MDR, see [Managed Detection and Response Reports Upgrade](../get-started/upgrade-reports.md). For information about scheduling the reports, see [Scheduled Reports and Notifications](../configure/notifications/report.md).

## Deprecated or unavailable  features

The migration precheck detects whether the following features or services are present in your environment. Alert Logic informs you that they cannot be transferred to MDR because they are deprecated or an equivalent feature or service does not exist.

* Event Alert Rules (deprecated)
* Out-of-Band web application firewall (OOB WAF) (no equivalent feature available)
* Blocking policies (no equivalent feature available)

For more information, see [Deprecated or unsupported functionality](../get-started/upgrade-console.md#Deprecatedorunsupportedfunctionality).
