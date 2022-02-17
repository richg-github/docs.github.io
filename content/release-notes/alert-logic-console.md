# Alert Logic Console Release Notes

## Alert Logic console release notes

    2022    ### Release date: February ?, 2022

[Release note about the new Monthly Log Review Details report...]

Alert Logic also released enhancements to scheduled reports:

* For weekly and monthly report schedules, you can now schedule a report on a specific day of the week or month.
* A new Run Once option, available for non-interactive reports like the Monthly Log Review Details report, allows you to generate the report immediately instead of at a scheduled time.
* Some reports now have schedule windows. Limiting available schedule times avoids generating empty or incomplete reports, which occurred previously if affected reports were scheduled before the data refresh completed.
* New report options allow you to choose the report format and type of data to include in the generated report.

You may notice that Alert Logic adjusted some existing report schedules for you, either to comply with a valid time range or to use a report option that makes a report easier to consume. If you prefer a different time or report option, you can edit the report schedule.

For more information, see [Scheduled Reports and Notifications](../configure/notifications/report.md).

### Release date: January 24, 2022

Alert Logic released improvements to the Scan Now feature available from the Topology page. Now you can choose whether to scan a host or ports that are excluded from scanning in the deployment scope of protection. For more information, see [Topology](../analyze/topology.md).

    2021    ### Release date: December 15, 2021

Alert Logic added support for Cisco Firepower in the Alert Logic console where you can view generated firewall incidents and collected log data. For more information, see [Firewall Incidents and Log Configuration](../analyze/firewall-incidents.md).

### Release date: November 18, 2021

Alert Logic added support for these Amazon Web Services (AWS) regions:

| AWS Region Name | Region |
|---|---|
| Africa (Cape Town) | af-south-1 |
| Asia Pacific (Hong Kong) | ap-east-1 |
| Asia Pacific (Osaka-Local) | ap-northeast-3 |
| Europe (Stockholm) | eu-north-1 |
| Europe (Milan) | eu-south-1 |
| Middle East (Bahrain) | me-south-1 |

### Release date: November 17, 2021

#### Features

Alert Logic released agent-based vulnerability scanning.  Agent-based scanning enables users to leverage the vulnerability assessment coverage of authenticated network scanning without the need to manage credentials and with a reduction in network traffic and impact. To learn more, including how to enable this feature by deployment, see [Agent-Based Scanning](../analyze/manage-scans-and-results/agent-based-scan.md).

### Release date: November 10, 2021

#### Features

You can now use [AWS Systems Manager Distributor](https://docs.aws.amazon.com/systems-manager/latest/userguide/distributor.html)     to install the  Alert Logic agent on AWS Systems Manager instances. To learn more, see [Automate Alert Logic Agent Installation with AWS Systems Manager Distributor](../prepare/agent-install-automated-aws.md).

### Release date: October 21, 2021

#### Features

Alert Logic released [ Health Notifications](../configure/notifications/health.md) to the unified [Notifications](../configure/notifications.md) experience. Health notifications can alert you, subscribed users, or a configured connector when an agent, appliance, or API collector is not collecting data or offline (unhealthy).

### Release date: October 6, 2021

#### Features

Alert Logic improved the [Application Registry](../configure/application-registry.md) page  to make it easier for you to find and configure your collections. Alert Logic now displays collector integrations in tiles that correspond to its third-party application or product. Alert Logic also added a new collector that allows you to integrate and collect logs from CrowdStrike. For more information, see [Configure CrowdStrike Log Collector](../configure/collectors/crowdstrike.md).

### Release date: July 27, 2021

#### Features

Alert Logic released improvements  to the Evidence tab of the Investigation Report in the Incidents page for Log Review incidents  associated with anomaly or rule-based findings. You can download a CSV file of the observations findings or facts for an event related to an incident. Alert Logic also added the aggregator summary section to Log Review incidents which allows you to download evidence for specific aggregator types for compliance needs. For more information, see [Download evidence](../analyze/log-review-upgrade.md#Download) and [Investigation Report](../get-started/incidents-upgrade.md#investigationReport).

### Release date: July 1, 2021

#### Features

Alert Logic can detect and generate Endpoint Security Incidents from log data collected from third-party endpoint application resources. To learn more endpoint security incidents, see [Endpoint Security Incidents](../analyze/endpoint-incidents.md).

### Release date: June 3, 2021

#### Features

Alert Logic released an improved correlation experience that allows you to create powerful custom rules with  similar syntax structure as Search queries in the Search page. You can configure the correlation rule to generate a FIM notification, an observation notification, or an incident notification when the data Alert Logic receives matches the pattern for the data you specified in the correlation. To learn more about the improved correlation feature, see [Improved Correlations and Search](../analyze/search/search-correlation.md).

### Release date: May 11, 2021

#### Features

Alert Logic released nine new NIST 800-171 Audit compliance reports  in the Compliance tab of the Reports page in the Alert Logic console. The  reports provide guidance for demonstrating compliance  with the National Institute of Standards and Technology (NIST) Special Publication 800-171. For more information about each report, see:

* [NIST 800-171 3.1 - Access Control](../analyze/reports/compliance/NIST-800-171-3.1-access-control.md)
* [NIST 800-171 3.3 - Audit and Accountability](../analyze/reports/compliance/NIST-800-171-3.3-audit-and-accountability.md)
* [NIST 800-171 3.4 - Configuration Management](../analyze/reports/compliance/NIST-800-171-3.4-configuration-management.md)
* [NIST 800-171 3.5 - Identification and Authentication](../analyze/reports/compliance/NIST-800-171-3.5-identification-and-authentication.md)
* [NIST 800-171 3.6 - Incident Response](../analyze/reports/compliance/NIST-800-171-3.6-incident-response.md)
* [NIST 800-171 3.11 - Risk Assessment](../analyze/reports/compliance/NIST-800-171-3.11-risk-assessment.md)
* [NIST 800-171 3.12 - Security Assessment](../analyze/reports/compliance/NIST-800-171-3.12-security-assessment.md)
* [NIST 800-171 3.13 - System and Communications Protection](../analyze/reports/compliance/NIST-800-171-3.13-system-and-communications.md)
* [NIST 800-171 3.14 - System and Information Integrity](../analyze/reports/compliance/NIST-800-171-3.14-system-and-information-integrity.md)

### Release date: April 6, 2021

#### Features

Alert Logic added an enhancement to your scope of protection capability for Data Center deployments. You can now define your protection  at a subnet level. To learn how to change your scope of protection, see [Change Protection Level of an Asset](../deploy/change-protection.md).

### Release date: March 25, 2021

#### Features

Alert Logic released three new vulnerability reports in the Vulnerabilities tab of the Reports page in the Alert Logic console. The Scan Summary Breakdown reports provide summary, detailed, and variance vulnerability results for  specific scan schedules. These reports can be downloaded  as an image, data (CSV), crosstab, PDF, or PowerPoint file. For more information about each report, see:

* [Scan Host Summary](../analyze/reports/Vulnerabilities/scan-schedule-breakdown/scan-host-summary.md)
* [Scan Details List](../analyze/reports/Vulnerabilities/scan-schedule-breakdown/scan-details-list.md)
* [Scan Variance](../analyze/reports/Vulnerabilities/scan-schedule-breakdown/scan-variance.md)

### Release date: March 18, 2021

#### Features

Alert Logic released an upgraded of the Log Review incident process, Machine Learning Log Review. The new machine learning algorithms allows Alert Logic to deliver a higher level of security value by automatically detecting many log-based anomaly types based on unique patterns and trends learned from your organization. For more information, see [Machine Learning Log Review Upgrade](../analyze/log-review-upgrade.md).

Alert Logic also released an upgraded version of the Incidents page for an enhanced and improved experience   to maximize your ability to manage incidents, and also view Log Review incidents.  This upgrade includes enhancements to see relevant and important information quickly, page customization, improvements to the investigation report, and more. For more information, see [Incidents Upgrade ](../get-started/incidents-upgrade.md).

Log Review incidents can also be found in the [Monthly Log Review Report](../analyze/reports/threats/log-review-analysis/monthly-log-review.md) report and in the improved version of the [Incident Daily Digest](../analyze/reports/threats/incident-analysis/incident-daily-digest.md) report to evaluate daily incidents by threat level, classification, top attackers, and top targets.

### Release date: February 4, 2021

#### Features

You can now deploy the Alert Logic Agent Container in Amazon Elastic Container Service (ECS) environments that run Amazon Web Services (AWS) Fargate. This solution enables the Alert Logic Agent Container to run as a sidecar to any Fargate Task Definition you wish to protect. This does include an update to the IAM Role policy with read-only List and Describe calls. To learn more, see [Deploy the Alert Logic Agent Container for AWS Fargate](../prepare/agent-container-fargate.md).

You can also now deploy the Alert Logic Protected Host Agent on AWS Workspaces workloads. This does include an update to the IAM Role policy with read-only List and Describe calls.

### Release date: February 3, 2021

#### Features

Alert Logic released a new Search experience for the Managed Detection and Response customers that allows you to  perform basic and advanced searches in Expert and Simple modes for different data types. You can  start a query in Simple mode,  and then switch to Expert mode to add more logic or complex functions. The Search experience now offers the following new features:

* Schedule search notifications
* Saved  searches and schedule searches
* Download search results
* Apply settings to your search, such as selecting a timezone
* Use search tabs to execute and switch between multiple searches
* Load saved searches into the query

To learn more, see [Get Started with Search](../get-started/search-a.md).

### Release date: January 28, 2021

#### Features

Alert Logic released the following enhancements to scan schedules for the Managed Detection and Response platform:

* For internal and external vulnerability scans, you can now specify the ports to scan. You can choose ports in predefined groups or define a custom list of ports to scan.
* You can also specify ports  to exclude from internal and external vulnerability scans.

To learn more, see [Manage Scan Schedules](../analyze/manage-scans-and-results/schedules.md).

    2020    ### Release date: December 17, 2020

#### Features

Alert Logic released the following enhancements to the Exposures page and the Health page for the Managed Detection and Response platform:

* For remediations, the Threat Risk Index score now appears in the list view.
* When you export a list of disposed remediations or exposures, notes added about the disposal now appear in the CSV file.
* When you restore a disposed or concluded item, you can now select specific assets for which to restore the exposure or remediation.

To learn more, see [Exposures](../analyze/exposures.md) and [Health](../analyze/health.md).

Alert Logic also released five new GDPR Audit compliance reports  in the Compliance tab of the Reports page in the Alert Logic console. The  reports provide guidance for demonstrating compliance  with the General Data Protection Regulation (GDPR). For more information about each report, see:

* [GDPR Article 25: Data Protection by Design and by Default](../analyze/reports/compliance/GDPR-article-25-data-protection.md)
* [GDPR Article 32: Security of Processing](../analyze/reports/compliance/GDPR-article-32-security-of-processing.md)
* [GDPR Article 33: Notification of Personal Data Breach](../analyze/reports/compliance/GDPR-article-33-notification-personal-data-breach.md)
* [GDPR Article 34: Communication of a Personal Data Breach](../analyze/reports/compliance/GDPR-article-34-comm-data-breach.md)
* [GDPR Article 35: Data Protection Impact Assessment](../analyze/reports/compliance/GDPR-article-35-data-protection-impact-assessment.md)

### Release date: December 7, 2020

#### Features

Alert Logic released a new compliance report in the Compliance tab of the Reports page in the Alert Logic console. The report provides guidance on how to use and access your File Integrity Monitoring (FIM) features to help you demonstrate compliance with HIPAA 164.312(c)(1). For more information, see [HIPAA 164.312(c)(1)—Integrity Controls](../analyze/reports/compliance/HIPAA-164.312-integrity-controls.md).

### Release date: November 18, 2020

#### Features

Alert Logic added two new log collectors to the Application Registry:* You can now integrate with the new Amazon Web Services (AWS) Network Firewall to collect alerts  generated by events that match Alert Logic firewall rules and that are sent to an Amazon Simple Storage Service (S3) bucket. To learn more, see [Configure AWS Network Firewall Log Collector](../configure/collectors/aws_network_firewall.md).
* You can now integrate with Amazon S3 to collect the following types of logs from an Amazon S3 bucket:
To learn more, see [Configure Amazon S3 Log Collector](../configure/collectors/amazon-s3.md).
   * Elastic Load Balancing: Application Load Balancer, Classic Load Balancer, and Network Load Balancer
   * Amazon Redshift: Connection, User, and User Activity
   * Amazon S3 Audit
   * Amazon VPC Flow Logs

Alert Logic released two incident account summary reports in the Threats tab of the Reports page of the Alert Logic console. The incident account summary reports provide the current distribution and trending data for incidents detected across your customer accounts and deployments. To learn more, see [Weekly Incident Account Summary](../analyze/reports/threats/incident-account-summary/weekly-incident-account.md) and [Monthly Incident Account Summary](../analyze/reports/threats/incident-account-summary/monthly-incident-account.md).

Alert Logic now allows customers with Data Center deployments to set their protection level for individual subnets. For instructions on how to set your scope of protection, see [Change Protection Level of an Asset](../deploy/change-protection.md).

### Release date: November 9, 2020

#### Features

Alert Logic is offering an enhanced and improved Reports feature for customers  upgrading from Cloud Defender to the Managed Detection and Response platform. The upgrade includes changes to the Cloud Defender Scheduled reports. You can find the same or similar information from Cloud Defender Scheduled reports in the Managed Detection and Response Alert Logic console. For more information, see [Managed Detection and Response Reports Upgrade](../get-started/upgrade-reports.md).

### Release date: October 7, 2020

#### Features

Alert Logic released the following enhancements to the Exposures page for Managed Detection and Response customers:

* The Exposures page now only lists security-related exposures detected by internal and external vulnerability scans   to help you narrow your focus. Health-related configuration and connection exposures continue to be available on the Health page, but were removed from the Exposures page.
* You can now sort the lists by various criteria and change to ascending or descending order.
* The total number of open exposure instances  that match selected filters appears next to each filter.
* Counts of affected assets and exposure instances now appear for each listed item.
* Disposed items now show the disposal expiration date.
* You can export selected items in a list.
* You can open the detail page for a remediation or exposure in a separate browser tab.
* Concluding and disposing exposures or remediations for affected assets is now more flexible. You can dispose or conclude a single, multiple, or all affected assets. For the dispose action, you can also select to dispose all future assets that match selected filters.

To learn more, see [Exposures](../analyze/exposures.md).

The Health page was also enhanced:

* You can now sort the lists by various criteria and change to ascending or descending order.
* The total number of open exposure instances  that match selected filters appears next to the Unhealthy filter.
* In the views for Exposures and Remediations, counts of affected assets and exposure instances now appear for each listed item.
* Disposed items now show the disposal expiration date.
* You can open the detail page for a remediation or exposure in a separate browser tab.
* Concluding and disposing exposures or remediations for affected assets is now more flexible. You can dispose or conclude a single, multiple, or all affected assets. For the dispose action, you can also select to dispose all future assets that match selected filters.

To learn more, see [Health](../analyze/health.md).

Alert Logic also released the Subscribed Notification Users report in the Service tab in the Reports page for Managed Detection and Response customers.  The report is a list of users set up to receive automated email notifications from the [Notifications](../configure/notifications.md) page. To learn more, see [Subscribed Notification Users](../analyze/reports/service/users/subscribed-notification-users.md).

### Release date: September 15, 2020

#### Features

Alert Logic released the following enhancements to  scan scheduling:

* A quarterly scan option is now available for internal and external vulnerability scans.
* For monthly scans, you can now choose to scan during a certain week on a certain day.

Alert Logic is also releasing the Last Scanned Breakdown report in the Vulnerabilities tab of the Reports page. The report provides visibility into when your assets were last scanned for vulnerabilities. To learn more, see [Last Scanned Breakdown](../analyze/reports/Vulnerabilities/last-scanned-breakdown.md).

### Release date: September 2, 2020

#### Features

Alert Logic released the following features to enhance your experience in the Alert Logic console:

* File Integrity Monitoring allows you to monitor changes to files and directories of assets associated with your Alert Logic deployments. You can configure monitoring or exclusions for specific file paths or entire directories  in your Windows and Linux systems. To learn more, see [File Integrity Monitoring ](../configure/file-integrity-monitoring.md).
* Alert Logic is also releasing two new compliance reports to provide guidance on how to use and access File Integrity Monitoring features to demonstrate compliance with PCI Requirement 11.5 and PCI Requirement 10.5.5 in the Compliance tab of the Reports page. For more information, see [PCI Requirement 11.5](../analyze/reports/compliance/PCI-requirement-11.5.md) and [PCI Requirement 10.5.5](../analyze/reports/compliance/PCI-requirement-10.5.5.md).
* Web Log Analytics (WLA) is a log-based application attack detection solution that protects your web applications from common application vulnerabilities. WLA is available for Professional or Enterprise Managed Detection and Response customers. To learn more about WLA, see [About Alert Logic Web Log Analytics (WLA)](../get-started/about-wla.md).
* The Authentication Management Security dashboard is available for Managed Detection and Response customers. The Authentication Management Security dashboard provides a summary of your authentication security activity in your environment. To learn more, see [Authentication Management Security](../analyze/dashboard/authentication-management-security.md).
* Connectors  allow you to send security data directly to a third-party application in near real time. When  you set up a notification and subscribe a connector, the connector can send a message or generate an IT service management (ITSM) ticket  automatically. For more information, see [Webhook and Email Connectors](../configure/connectors.md).
* The Alert Logic DevNet developer portal enables you to build automation and integrations to extend and embed the Alert Logic platform. This developer portal includes a comprehensive toolkit of command-line tools and programming language integrations, as well as a rich library of use cases so you can get started quickly. The portal is located at [developer.alertlogic.com](http://developer.alertlogic.com/).

### Release date: August 19, 2020

#### Features

Alert Logic is releasing SOC 2 Audit reports in the Compliance tab of the Reports page. The reports help demonstrate compliance with the Trust Services Criteria established  by the American Institute of Certified Public Accountants (AICPA) and include the following:

* [SOC 2 Common Criteria 6.2 User Registration](../analyze/reports/compliance/SOC2-CC-6.2-user-registration.md)
* [SOC 2 Common Criteria 6.3 Access Modification and Removal](../analyze/reports/compliance/SOC2-CC-6.3-access-modification-and-removal.md)
* [SOC 2 Common Criteria 6.6 Boundary Protection](../analyze/reports/compliance/SOC2-CC-6.6-boundary-protection.md)
* [SOC 2 Common Criteria 6.8 Unauthorized and Malicious Code Protection](../analyze/reports/compliance/SOC2-CC-6.8-unauthorized-and-malicious-code-protection.md)
* [SOC 2 Common Criteria 7.1 Configuration and Vulnerability Management](../analyze/reports/compliance/SOC2-CC-7.1-configuration-and-vulnerability-management.md)
* [SOC 2 Common Criteria 7.2 Security Event and Anomaly Detection](../analyze/reports/compliance/SOC2-CC-7.2-security-event-anomaly-detection.md)
* [SOC 2 Common Criteria 7.3 Incident Detection and Response](../analyze/reports/compliance/SOC2-CC-7.3-incident-detection-reponse.md)
* [SOC 2 Common Criteria 7.4 Incident Containment and Remediation](../analyze/reports/compliance/SOC2-CC-7.4-incident-containment-remediation.md)

### Release date: August 8, 2020

#### Features

Alert Logic released enhancements to scan scheduling. Default scan schedules are available  that you can edit, or you can create additional schedules for all or selected assets in your deployment. The improved Scan Schedules page is available from your deployments. To learn more, see [Manage Scan Schedules](../analyze/manage-scans-and-results/schedules.md).

You can now also optimize scan performance from the Topology page in the Alert Logic console. To learn more, see [Adjust scan performance](../analyze/manage-scans-and-results/adjust-settings.md#Adjustscanperformance).

### Release date: August 5, 2020

#### Features

Alert Logic is releasing the Authentication Management Summary dashboard for Managed Detection and Response customers. The Authentication Management Summary dashboard provides a summary of your authentication management activities observed in your environment. To learn more, see [Authentication Management Summary](../analyze/dashboard/authentication-management-summary.md).

### Release date: July 14, 2020

#### Features

Alert Logic is releasing the SSL Certification Expiration Status report to the Service tab of the Reports page. The  report provides insights into the statuses of SSL keys and certificates that are used on Alert Logic appliances to decrypt network traffic. For more information, see [SSL Certification Expiration Status](../analyze/reports/service/health/current-ssl-certificates-status.md).

### Release date: July 8, 2020

#### Features

Alert Logic is releasing enhancements to the Health page:

* You can now view healthy and unhealthy SaaS application collectors integrated through the Application Registry.
* New Healthy views allow you to see your assets that are connected and configured correctly.
* You can now see the exposure and remediation for an unhealthy asset without leaving the Health page.
* Detail pages for healthy and unhealthy assets now include extensive information about the asset.
* An exposure and remediation is now generated for any SSL key and certificate that is within 30 days or less of expiration.

For more information about the updated Health page, see [Health](../analyze/health.md).

Alert Logic is releasing HITRUST CSF reports in the Compliance tab of the Reports page. The reports demonstrate compliance with specific control categories of HITRUST CSF and include the following:

* [HITRUST CSF 01.0 Access Control](../analyze/reports/compliance/HITRUST-CSF-01.md)
* [HITRUST CSF 03.0 Risk Management](../analyze/reports/compliance/HITRUST-CSF-03.0.md)
* [HITRUST CSF 06.0 Compliance](../analyze/reports/compliance/HITRUST-CSF-06.0.md)
* [HITRUST CSF 09.0 Communications and Operations Management](../analyze/reports/compliance/HITRUST-CSF-09.0.md)
* [HITRUST CSF 10.0 Information Systems Acquisition, Development, and Maintenance](../analyze/reports/compliance/HITRUST-CSF-10.0.md)
* [HITRUST CSF 11.0 Information Security Incident Management](../analyze/reports/compliance/HITRUST-CSF-11.0.md)

Alert Logic is also enhancing your vulnerability management capabilities by releasing the Vulnerability Variance reports to the Vulnerability tab in the Reports page. The Vulnerability Variance reports  provide a valuable summary, trending and detailed lists for new, resolved, and unresolved vulnerabilities in your environment. The Vulnerability Variance reports  include the following:

* [Daily Vulnerability Variance](../analyze/reports/Vulnerabilities/daily-vulnerability-variance.md)
* [Weekly Vulnerability Variance](../analyze/reports/Vulnerabilities/weekly-vulnerability-variance.md)
* [Monthly Vulnerability Variance](../analyze/reports/Vulnerabilities/monthly-vulnerability-variance.md)

Alert Logic now supports automatic deployment through AWS Control Tower. For more information, see [Deployment with AWS Control Tower](../deploy/aws-control-tower.md).

### Release date: July 7, 2020

#### Features

Alert Logic can detect and generate Authentication Application Security Incidents from log data collected from third-party authentication application resources. To learn more authentication security incidents, see [Authentication Application Security Incidents](../analyze/security-incidents.md).

### Release date: June 18, 2020

#### Features

Alert Logic is releasing the Current Vulnerability Breakdown reports to the Vulnerability tab in the Reports page, which  provide a breakdown of current vulnerability instances and vulnerable hosts ranked by count and severity with asset-level or vulnerability details. The Current Vulnerability Breakdown reports include the following:

* [Current Vulnerable Hosts Breakdown](../analyze/reports/Vulnerabilities/current-vulnerable-hosts-breakdown.md)
* [Current Vulnerabilities Breakdown](../analyze/reports/Vulnerabilities/current-vulnerabilities-breakdown.md)

### Release date: June 3, 2020

#### Features

Alert Logic is releasing the Threat Risk Index (TRI) Summary Dashboard for Managed Detection and Response customers. The TRI Summary dashboard provides insights into the recent threat risk index TRI scores of your environment. To learn more about TRI Summary Dashboard, see [Threat Risk Index Summary](../analyze/dashboard/tri-summary.md).

### Release date: May 5, 2020

#### Features

Alert Logic is releasing a new unified notifications experience in a phased rollout starting May 5, 2020 and ending May 11, 2020. The upgraded Notifications feature updates [incident notifications](../configure/notifications/incident.md) and adds two new notification types:

* [Log correlations](../configure/notifications/log-correlation.md)—You can now set up and save a log correlation rule and configure it to create an observation or an incident and send a notification when a match occurs.
* [Scheduled reports](../configure/notifications/report.md)—You can set up and save a report schedule to generate a report periodically  and send a notification when the report is generated. If you are a Managed Detection and Responsecustomer and previously set up a Health Status notification, Alert Logic upgraded it as a scheduled report. After a scheduled report is generated, Alert Logic saves it for viewing and download.

You can subscribe both email recipients and configured integrations such as a webhook to receive notifications.

For more information about the Notifications feature, how to create and manage notifications, and to learn how Alert Logic upgraded your existing notifications, see:

* [Notifications](../configure/notifications.md)
* [Manage Notifications](../configure/notifications/manage.md)
* [Notifications Upgrade](../get-started/notifications-upgrade.md)

### Release date: April 2, 2020

#### Features

Alert Logic is releasing the following features to enhance your experience in the Alert Logic console, and add administrative and security value to your organization: * Application Registry is a repository of  multiple third-party application integrations that can generate log data which Alert Logic can collect. Application Registry is only available for Managed Detection and Response Professional and Enterprise customers. To learn more about Application Registry, see [Application Registry](../configure/application-registry.md).
* Application Log is a new configuration experience with functional APIs specific to the applications you want to configure. The Application Log feature streamline workflow with specific templates applications that currently supports flat file logs. For more information, see [Application Logs for Flat File Configuration](../configure/application-logs.md).
* Alert Logic can detect and generate Firewall Security Incidents and observations from log data collected from third-party firewall application resources. To learn more firewall security incidents, see [Firewall Incidents and Log Configuration](../analyze/firewall-incidents.md).
* Alert Logic is also releasing the following dashboards in combination with firewall incidents for customers with configured firewall application resources and log collection instances:
   * The Firewall Log Volume Analysis dashboard provides insights into the volume of firewall log messages, firewall security incidents and observations in your environment. To learn more about this dashboard, see [Firewall Log Volume Analysis Dashboard](../analyze/dashboard/firewall-log-volume-dashboard.md).
   * The Firewall Log Security Analysis dashboard provides insights into the firewall security incidents generated from analyzing firewall logs in  your environment. To learn more about this dashboard, see [Firewall Log Security Analysis Dashboard](../analyze/dashboard/firewall-log-security-dashboard.md).
* Alert Logic now expanded the health information int the Reports page for Managed Detection and Response customers. The Daily Health Summary and Weekly Health Summary reports provides insights into issues in your environment related to your protected networks, data collection, and agents. To learn more about the Daily Health Summary report, see [Daily Health Summary](../analyze/reports/service/health/daily-health-summary.md). To learn more about the Weekly Health Summary report, see [Weekly Health Summary](../analyze/reports/service/health/weekly-health-summary.md).

### Release date: March 31, 2020

#### Features

Alert Logic now offers Managed Detection and Response partners and customers with managed accounts two additional dashboards. For more information, see the following:

* The Managed Accounts Health Summary dashboard summarizes and provides insights into the health status of the accounts you manage from the previous day. For more information about this dashboard, see [Managed Accounts Health Summary Dashboard](../analyze/dashboard/managed-accounts/managed-accounts-health-summary.md).
* The Managed Accounts Security Summary dashboard provides insights into the recent security status of the accounts you manage. For more information about this dashboard, see [Managed Accounts Security Summary Dashboard](../analyze/dashboard/managed-accounts/managed-accounts-security-summary.md).

### Release date: February 27, 2020

#### Features

Alert Logic now offers Managed Detection and Response customers monthly and weekly reports for the following vulnerability reports: * The Vulnerability Summary reports provide summary headline, distribution, and trending data for vulnerabilities found across your environment:
   * [Monthly Vulnerability Summary](../analyze/reports/Vulnerabilities/vulnerability-analysis/vulnerability-summary.md)
   * [Weekly Vulnerability Summary](../analyze/reports/Vulnerabilities/vulnerability-analysis/weekly-vulnerability-summary.md)
* The Top 10 Vulnerability Lists reports provide top 10 lists for your most vulnerable hosts by total count and by severity, oldest critical vulnerabilities, and frequent vulnerabilities:
   * [Monthly Top 10 Vulnerability Lists](../analyze/reports/Vulnerabilities/vulnerability-analysis/vulnerability-top-ten.md)
   * [Weekly Top 10 Vulnerability Lists](../analyze/reports/Vulnerabilities/vulnerability-analysis/weekly-vulnerability-top-ten.md)
* The Vulnerability Distribution Explorer reports provide insights into patterns from the vulnerabilities that include vulnerability distribution and trends categorized by status, exploitability, severity, age, operating system, and asset type:
   * [Monthly Vulnerability Distribution Explorer](../analyze/reports/Vulnerabilities/vulnerability-analysis/vulnerability-distribution-explorer.md)
   * [Weekly Vulnerability Distribution Explorer](../analyze/reports/Vulnerabilities/vulnerability-analysis/weekly-vulnerability-distribution-explorer.md)

### Release date: February 19, 2020

#### Features

Alert Logic has taken further security measures and now requires customers with Azure deployments to grant extra permissions. This will allow  Alert Logic to perform benchmark checks on your Azure deployments that expose vulnerabilities. See  the following documentation for more information:

* For customers who are configuring an Azure deployment for the first time, or customers who have Azure deployments but do not have an Azure app registration set up, see [Configure App Registration and RBAC for Microsoft Azure Resources](../prepare/azure-rbac-role-setup.md).
* If you have existing Azure deployments, and already have an app registration set up, see [Update your Azure Deployment for CIS Foundation Benchmarks ](../prepare/azure-benchmark-deployment-configuration.md).

### Release date: February 14, 2020

#### Features

Alert Logic has released Dashboards, a new home page that centralizes information in interactive visuals and simplifies navigation to other pages in the Alert Logic console. You can now try Dashboards and become familiar with the new and improved experience. For more information about Dashboards and how to try it, see [Dashboards](../analyze/dashboards.md). For more information about the new Dashboards navigation, see [Managed Detection and Response Navigation Menu Updates](../analyze/dashboard/navigation.md).

    2019    ### Release date: December 19, 2019

#### Features

* Alert Logic has added more compliance reports, located in the Compliance tab of the Reports page, to help you demonstrate compliance with requirements of the Payment Card Industry Data Security Standard (PCI DSS) and the Health Insurance Portability and Accountability Act (HIPAA) and Health Information Technology for Economic and Clinical Health (HITECH) Security Audit.
   * The following are the four recently added PCI DSS Audit reports:
      * [PCI Requirement 10.7](../analyze/reports/compliance/PCI-requirement-10.7.md)
      * [PCI Requirement 10.8](../analyze/reports/compliance/PCI-requirement-10.8.md)
      * [PCI Requirement 11.2.1](../analyze/reports/compliance/PCI-requirement-11.2.1.md)
      * [PCI Requirement 11.2.2](../analyze/reports/compliance/PCI-requirement-11.2.2.md)
   * The following are the three recently added HIPAA-HITECH Security Audit reports:
      * [HIPAA 164.308(a)(1)(ii)(B)—Risk Management](../analyze/reports/compliance/HIPAA-164.308-risk-management.md)
      * [HIPAA 164.312(b)—Audit Controls](../analyze/reports/compliance/HIPAA-164.312-audit-controls.md)
      * [HIPAA 164.308(a)(5)(ii)(B)—Protection from Malicious Software](../analyze/reports/compliance/HIPAA-164.308-protection-from-malicious-software.md)
* Alert Logic now offers Managed Detection and Response customers monthly and weekly reports of their features, capabilities, and state of their environment:
   * The Enterprise Risk reports provide valuable insights and analysis of your incidents, events, and vulnerabilities:
      * [Monthly Enterprise Risk](../analyze/reports/risk/enterprise-risk/monthly-enterprise.md)
      * [Weekly Enterprise Risk](../analyze/reports/risk/enterprise-risk/weekly-enterprise.md)
   * The Incident Analysis reports provide visibility into threats and incidents in your environment.
      * [Monthly Incident Analysis ](../analyze/reports/threats/incident-analysis/monthly-incident.md)
      * [Weekly Incident Analysis](../analyze/reports/threats/incident-analysis/weekly-incident.md)
   * The Event Analysis reports provide visibility into Network IDS events processed in your environment.
      * [Monthly Event Analysis](../analyze/reports/threats/event-analysis/monthly-event-analysis.md)
      * [Weekly Event Analysis](../analyze/reports/threats/event-analysis/weekly-event-analysis.md)
   * The Vulnerability Analysis reports provide insights into vulnerabilities and vulnerable assets found in your environment.
      * [Monthly Vulnerability Analysis ](../analyze/reports/Vulnerabilities/vulnerability-analysis/monthly-vulnerability.md)
      * [Weekly Vulnerability Analysis](../analyze/reports/Vulnerabilities/vulnerability-analysis/weekly-vulnerability.md)

### Release date: December 11, 2019

#### Features

Alert Logic has released an improved version of the PCI Scan Disputes page. You can use the PCI Scan Dispute to submit disputes for vulnerabilities  in non-compliant scan policies. For more information, see [PCI Scan Disputes](../configure/pci-scan-dispute.md).

### Release date: December 3, 2019

#### Features

Alert Logic now includes the option to configure webhooks, which allows Alert Logic incident notifications to be sent to any public-facing web server configured to handle HTTP callbacks. For more information, see [Webhooks](../configure/webhooks.md).

### Release date: November 6, 2019

#### Features

For Azure-based deployments, Alert Logic now supports the ability for customers to use client credentials, defined by role-based access control within the Azure console. Microsoft recommends this method of authentication to reduce service interruptions due to stale username/password combinations. All new users will only be able to use client credentials going forward. Existing customers can continue using their existing username/password combinations until they reset them. For more information on creating the appropriate RBAC roles, see [Configure App Registration and RBAC for Microsoft Azure Resources](../prepare/azure-rbac-role-setup.md).

Alert Logic has split multi-page reports into single-page reports to allow customers direct access to information. The reports were divided as follows:

| Original Report Name | New Report Names |
|---|---|
| Vulnerable Host Explorer | [Vulnerable Hosts Explorer](../analyze/reports/Vulnerabilities/vulnerability-analysis/vulnerability-host-explorer.md) |
| [Vulnerable Hosts Change Trends](../analyze/reports/Vulnerabilities/vulnerability-analysis/vulnerable-hosts-trends.md) |
| Vulnerability Distribution Explorer | [Vulnerability Distribution Explorer](../analyze/reports/Vulnerabilities/vulnerability-analysis/vulnerability-distribution-explorer.md) |
| [Vulnerability Change Trends](../analyze/reports/Vulnerabilities/vulnerability-analysis/vulnerability-change-trends.md) |
| Network IDS Events Explorer | [Network IDS Events Explorer](../analyze/reports/threats/event-analysis/network-ids-events-explorer.md) |
| [Top Events Sources and Destinations](../analyze/reports/threats/event-analysis/top-sources-destinations.md) |
| Log Collection | [Log Collection](../analyze/reports/service/capability-usage/log-collection.md) |
| [Top 10 Log Collectors](../analyze/reports/service/capability-usage/top-ten-log-collectors.md) |
| IDS Traffic | [IDS Traffic](../analyze/reports/service/capability-usage/network-ids-traffic.md) |
| [Top 10 IDS Assets](../analyze/reports/service/capability-usage/top-10-ids-assets.md) |
| Customer Contacts | [Escalation Contacts](../analyze/reports/reports.md#Users) |
| [Notification Contacts](../analyze/reports/reports.md#Users) |
| [Incident Notification Contacts](../analyze/reports/reports.md#Users) |
| Vulnerability Summary | [Vulnerability Summary](../analyze/reports/Vulnerabilities/vulnerability-analysis/vulnerability-summary.md) |
| [Top 10 Vulnerability Lists](../analyze/reports/Vulnerabilities/vulnerability-analysis/vulnerability-top-ten.md) |
| [Vulnerabilities List](../analyze/reports/Vulnerabilities/vulnerability-analysis/vulnerability-lists.md) |
| TRI Summary | [TRI Summary](../analyze/reports/risk/tri-summary.md) |
| [Top 10 TRI Lists](../analyze/reports/risk/top-ten-TRI-list.md) |

### Release date: October 10, 2019

#### Feature

Alert Logic updated the Saved Searches functionality to expand the options for setting notifications. Users can add one or more users from the same customer account to the list of notification recipients in the saved search panel. For more information, see [Create Saved and Scheduled Log Searches](../analyze/log-search/save-schedule.md).

### Release date: September 24, 2019 

#### Feature

Alert Logic released a new feature for customers with Essentials and Professional subscriptions.

The new Extended Endpoint Protection functionality from Alert Logic helps you control threats and manage incidents from employee workstations, points of sale, servers, and more. For more information, see [About Alert Logic Extended Endpoint Protection](../get-started/about-extended-endpoint-protection.md) and [Get Started with Alert Logic Extended Endpoint Protection](../get-started/endpoint-protection.md).

### Release date: September 17, 2019 

#### Feature

Alert Logic added a new feature to the scanning functionality, Scan Now. If you need to run a scan immediately, you can use the Scan Now feature on the Topology page. This scans the selected asset right away or as soon as possible, outside of the normal schedule. See [Scan Now](../analyze/manage-scans-and-scan-results.md#ScanNow) for more information.

### Release date: September 13, 2019

#### Feature

* Alert Logic added five new compliance reports, located in the Compliance tab of the Reports page, that provide  guidance   for performing log searches to help demonstrate compliance with some 10.2 requirements of the  Payment Card Industry Data Security Standard (PCI DSS):
   * [PCI Requirement 10.2.2](../analyze/reports/compliance/PCI-requirement-10.2.2.md)
   * [PCI Requirement 10.2.4](../analyze/reports/compliance/PCI-requirement-10.2.4.md)
   * [PCI Requirement 10.2.5](../analyze/reports/compliance/PCI-requirement-10.2.5.md)
   * [PCI Requirement 10.2.6](../analyze/reports/compliance/PCI-requirement-10.2.6.md)
   * [PCI Requirement 10.2.7](../analyze/reports/compliance/PCI-requirement-10.2.7.md)
* Alert Logic added a new report, Missing Agent Digest, to the Health report group in the Service tab of the Reports page. The Missing Agent Digest report provides insight into the daily issues related to hosts that are missing agents, including a comparison of missing agent statuses, top ten lists, and a list of hosts with missing agents. To learn more about this report, see [Missing Agent Digest](../analyze/reports/service/health/missing-agent-digest.md).

### Release date: July 10, 2019

#### Feature

* Alert Logic has revamped the following three compliance reports, located in the Compliance tab of the Reports page, to help you demonstrate compliance with some requirements of the Payment Card Industry Data Security Standard (PCI DSS):
   * The PCI Requirement 6.6 report provides WAF deployments, traffic, incidents, and attacks that help demonstrate compliance with Requirement 6.6. For more information about this report, see [PCI Requirement 6.6](../analyze/reports/compliance/PCI-requirement-6.6.md).
   * The PCI Requirement 10.5.1 report provides a list of the current log management users that help you demonstrate compliance with Requirement 10.5.1.For more information about this report, see [PCI Requirement 10.5.1](../analyze/reports/compliance/PCI-requirement-10.5.1.md).
   * The PCI Requirement 11.4 report shows Network IDS incidents and customer escalation contacts that help you demonstrate compliance with Requirement 11.4. For more information about this report, see [PCI Requirement 11.4](../analyze/reports/compliance/PCI-requirement-11.4-new.md).
* Alert Logic added four new compliance reports, located in the Compliance tab of the Reports page, that provide available documentation and compliance artifacts to help demonstrate compliance with some requirements of the PCI DSS and the Health Insurance Portability and Accountability Act (HIPAA) Security Audit, which include the following:
   * The PCI Requirement 10.6.1 report provides log review incidents and log management incidents that help you demonstrate compliance with Requirement 10.6.1. For more information about this report, see [PCI Requirement 10.6.1](../analyze/reports/compliance/PCI-requirement-10.6.1.md).
   * The HIPAA 164.308(a)(1)(ii)(D)—Information System Activity Review report provides the log review and log management incidents that help demonstrate compliance with HIPAA 164.308(a)(1)(ii)(D). For more information about this report, see [HIPAA 164.308(a)(1)(ii)(D)—Information System Activity Review](../analyze/reports/compliance/HIPAA-164.308-is-activity-review.md).
   * The HIPAA 164.308(a)(6)(ii)—Response and Reporting report provides available documentation and compliance artifacts that help you demonstrate compliance with requirements of  HIPAA 164.308(a)(6)(ii).  For more information about this report,  see [HIPAA 164.308(a)(6)(ii)—Response and Reporting](../analyze/reports/compliance/HIPAA-164.308-response-reporting.md).
   * The HIPAA 164.308(a)(5)(ii)(C)—Login Monitoring report provides available documentation and compliance artifacts that help you demonstrate compliance with requirements of HIPAA 164.308(a)(5)(ii)(C).  For more information about this report,   see [HIPAA 164.308(a)(5)(ii)(C)—Login Monitoring](../analyze/reports/compliance/HIPAA-164.308-login-monitoring.md).
* Alert Logic added the Health report group, which includes two new reports, to the Service tab of the Reports page. The Health reports provide valuable summary and trending data on the health status of protected networks and assets collecting log or network data, which include the following:
   * The Network Health Status Digest report provides insight into the daily issues related to protected networks in your environment, including a comparison of health statuses, top ten lists, and total number of open remediations for each network. For more information about this report, see [Network Health Status Digest](../analyze/reports/service/health/network-health-digest.md).
   * The Collection Issues Digest report provides insight into the daily issues related to log data collection and Network IDS traffic, including a comparison of health statuses, top five lists, and a list of open remediations to fix configuration issues. For more information about this report, see [Collection Issues Digest](../analyze/reports/service/health/collection-issues-digest.md).

### Release date: June 12, 2019

#### Feature

Alert Logic manual mode deployments now include a Cross-Network Protection option, which allows networks to connect and use resources from a network with an assigned appliance for Network IDS or scanning. This centralizes the appliances that provide protection to your account, which allows your organization to reduce infrastructure costs. For more information, see [Cross-Network Protection](../deploy/cross-network-protection.md).

### Release date: May 28, 2019

#### Features

Alert Logic added significant updates to the Log Search functionality, including the following features:

* You can organize saved searches into groups. For more information, see [Group options](../analyze/log-search/save-schedule.md#group-options).
* After you move searches to trash, you can restore or permanently delete them. For more information, see [Restore or permanently delete a saved search](../analyze/log-search/save-schedule.md#Restoreorpermanentlydeleteasavedsearch).

### Release date: April 25, 2019

#### Feature

* Alert Logic added the Health console, which consist of pages on the summary of your environment, detailed health information of your networks, appliances, and agents with suggested configuration remediations, and the option to subscribe to health summary alerts. For more information, see [Health](../analyze/health.md).
* Alert Logic deployments now include a Network IDS Whitelist option that allows you to select networks for whitelisting. For customers who were previously subscribed to Alert Logic legacy products, and have upgraded to Managed Detection and Response, your Network IDS whitelist will be migrated to the new experience.
* Alert Logic added an Expedite Scan Capability in topology which expedites scans on individual assets  when your organization requires specific assets to be scanned immediately. Alert Logic moves expedited scans ahead of their schedule to the next available time. For more information about expedite scans, see [Topology](../analyze/topology.md#Expedite).
* Alert Logic added a new report, the PCI Requirement 10.6 (Incidents) report, which provides log review and log management incidents to help demonstrate compliance to Requirement 10.6 of PCI DSS. For more information about this report, see [PCI Requirement 10.6 (Incidents)](../analyze/reports/compliance/PCI-requirement-10.6-incidents.md).
* Alert Logic added a new report, the PCI Requirement 11.4 report, which provides Network IDS incidents and customer escalation contacts to help you demonstrate compliance to Requirement 11.4 of the PCI DSS. For more information about this report, see [PCI Requirement 11.4](../analyze/reports/compliance/PCI-requirement-11.4a.md).

### Release date: April 9, 2019

#### Feature

* Alert Logic updated scan frequency and scheduling to allow you to schedule internal vulnerability scans and external vulnerability scans separately. For more information, see [Manage Scans and Scan Results](../analyze/manage-scans-and-scan-results.md#Scan).
* When you add assets to a Data Center deployment, you can now inform Alert Logic that your network equipment is configured to SPAN or another port mirroring feature. If you select this option, you avoid duplicating Network IDS traffic reported to Alert Logic while allowing Alert Logic to analyze the traffic passing through the port mirroring feature. For more information about Data Center assets, see [Add assets](../deploy/data-center-essentials.md#Add_Assets).

### Release date: April 5, 2019

#### Feature

* Alert Logic updated the CIS AWS Foundations Benchmark report in the Alert Logic console to support Level 1 and Level 2 of the latest version (1.2.0) of the CIS AWS Foundations Benchmark. Users can now asses  their AWS accounts against the latest CIS AWS Foundations Benchmark guidelines, including multi-factor authentications, AWS Config auditing, review of VPC peering network rules, review of IAM policies, access key rotation, and other improvements. For more information about the CIS AWS Foundations Benchmark report, see [Reports Guide](../analyze/reports/reports.md#CISbenchmark).
* Alert Logic updated the incident notes in the Incidents page to include the name of the Alert Logic analyst who provided the notes and the name of the user who has updated the incident. The notes appear in the Audit Log of the Investigation Report and Recommendation pages, and in the Evidence page. For more information about incident notes, see [Investigation Report](../analyze/incidents.md#investigationReport).
* Alert Logic now includes Alert Logic analyst notes in email notifications for incident escalations. This allows users to see the analyst notes provided in the Incidents page immediately without having to log into the Alert Logic console.  For information about incident notifications in the Alert Logic console, see [Incident notifications](../analyze/incidents.md#Notifications).

### Release date: April 2, 2019

#### Feature

Alert Logic added notifications for incidents originating from Amazon GuardDuty findings. GuardDuty is a threat detection service that continuously monitors for malicious activity and unauthorized behavior to protect your AWS accounts and workloads. The Alert LogicAmazon GuardDuty integration lets you view GuardDuty findings in the Alert Logic console Incidents page.

The Incidents page allows you to configure notifications for incidents based on their threat levels. With the added notification support, all GuardDuty incidents are available by their threat levels. For guidance and information about GuardDuty findings severity, which corresponds to Alert Logic threat level, see [Amazon documentation for GuardDuty findings and severity](https://docs.aws.amazon.com/guardduty/latest/ug/guardduty_findings.html#guardduty_findings-severity). For information about incident notifications in the Alert Logic console, see [Incident notifications](../analyze/incidents.md#Notifications)

### Release date: March 12, 2019

#### Features

* Alert Logic updated scan scheduling to allow more control of your scan schedules. You can schedule how often and when to perform vulnerability scans and discovery scans for each of your deployments. For more information, see [Manage Scans and Scan Results](../analyze/manage-scans-and-scan-results.md#Scan).
* For customers who were previously subscribed to Alert Logic legacy products, and have upgraded to Managed Detection and Response, you can access your legacy scan results and archived reports. For more information, see [Manage Scans and Scan Results](../analyze/manage-scans-and-scan-results.md#View2).
* Alert Logic added a new report, Network IDS Traffic, which provides visibility into the Network IDS traffic volume and collections processed in your environment. For more information, see [IDS Traffic](../analyze/reports/service/capability-usage/network-ids-traffic.md).
* Alert Logic updated the IAM Role policy documents for Amazon Web Services (AWS) deployments. If your customer account provides the Managed Detection and Response products, Alert Logic recommends you update your existing deployments to use IAM roles created with the most current policy documents. For more information, see [Update your IAM roles](../prepare/aws-cross-account-role-setup.md#update-roles)

### Release date: February 26, 2019

#### Features

* Alert Logic now offers  Log Review service with Managed Detection and Response. Log Review creates incidents, which appear on the [Incidents](../analyze/incidents.md) page and in notification emails. Some Log Review incidents are escalated by an Alert Logic security analyst, and the rest appear as info level incidents.
* Alert Logic added a new report, Monthly Log Review, which provides a monthly summary analysis of your Log Review incidents. For more information, see [Monthly Log Review Report](../analyze/reports/threats/log-review-analysis/monthly-log-review.md).

    2018    ### Release date: November 28, 2018

#### Features

Alert Logic has launched an integration with the new Security Hub offering from AWS. See [Integration with AWS Security Hub](../configure/aws-security-hub.md) for more information.

### Release date: April 25, 2018

#### Bug fixes

* This release resolves an issue with updating agent policies. The issue is resolved and users can create and update agent policies as normal.
* This release resolves an issue with events, incidents, and blocking alert rules. To access the pages, click **CONFIGURATION**, then click **Notifications**, and then select the type of alert rule you want to create.
* This release resolves cosmetic issues with page layout on several configuration screens, and the Zones and Host Groups screens.
* This release resolves an issue that redirected users when they clicked a link to an incident.
* This release resolves an issue with updating block requests in the incidents panel.
* This release updates an error message that appears when a read-only user tries to access unauthorized tools or content.
* This release resolves an issue with list filters on the sources pages. All filters appear as intended now.
* This release resolves an issue with a link in the PCI Dispute system.

#### Features

* This release adds a time zone selection field to the **New Source** menu. You must choose a time zone to create a source.

### Release date: April 20, 2018

#### Bug fixes

* This release resolves an issue where Azure deployments did not show protected hosts associated with the deployment.
* This release resolves cosmetic issues with page sizing and scrolling.
* This release resolves an issue in the menu to add a new certificate. For some users, the menu timed out before they were done filling in all the information. This issue has been resolved.
* This release resolves an issue with the **Save** button on the correlation policy and flat file log sources screens for certain deployments. The Save button now displays and works as expected.

#### Features

* This release adds a feature that displays the full name of the account you are viewing in the Alert Logic console.

### Release date: April 17, 2018

#### Bug fixes

* This release resolves an issue with user time zone settings.
* This release resolves an issue where the host metadata displayed the private IP as a public IP.
* This release resolves an issue with viewing log messages within cases.
* This release resolves compatibility issues with Internet Explorer version 11.
* This release resolves an issue that caused the Alert Logic console to display an error when users tried to turn a host into a protected host.
* This release resolves an issue with appliances and agents filtering on Azure deployments.
* This release resolves an issue where metadata was missing on some log sources.
* This release resolves an issue with the **Save** button on the correlation policy editing screen.

#### Features

* This release adds a feature that allows users to select the customer account they want to use in the **Statistics** tab of **Scans**.

### Release date: week of April 9-13, 2018

#### Bug fixes

* This release resolves an issue with retrieving SSL certifications.
* This release resolves an issue with the search function.
* This release resolves a cosmetic issue with the layout of the **Scans****Dashboard** page.
* This release resolves an issue with the reporting system in the Alert Logic console. All users can now access reports normally.
* This release resolves an issue with the forgotten password link on the login page.
* This release resolves an issue with incident and event counts on the dashboard pages. All counts are now accurate.
* This release resolves an issue with cached pages causing certain links to redirect users. The issue is resolved, and all links and navigation tools work as expected.
* This release resolves issues where the Alert Logic console did not work normally for users who accessed it from certain browsers. The issue is resolved, though if you continue to experience issues, use Google Chrome.
* This release resolves an issue where an internal Alert Logic feature appeared to customers as a dead link. The link no longer appears for non-Alert Logic users.
* This release resolves an issue where users could view data on the **Scan** dashboard for all accounts for which the user had access. The issue is resolved, and customers now only see data for the selected account.

#### Features

* This release adds multiple ID numbers to identify incidents and events.
* This release adds a feature that allows allowing users to easily share links to events.
   * In the Alert Logic console, click **SEARCH**, and then click **Events**. In the list that appears, find the event you want to share, and then click the share icon (![](../Resources/Images/Icons/share.png)) in the **Share** column. A new browser tab opens and shows event details. The URL in the new tab is a direct link to the event details page.
   * You may also click an event to view the event details page. From the event details page, click the share icon (![](../Resources/Images/Icons/share.png)) at the top of the page. The A new browser tab opens, and the URL in the new tab is a direct link to the event details page.

### Release date: April 7, 2018

#### Features

Alert Logic updated the Alert Logic console to provide a single login and universal navigation for all products and subscriptions.                This update allows you to easily find everything you need in one place across the entire Alert Logic portfolio. The top-level navigation is organized around functional categories (incidents, remediations, search, reports), and is subscription-aware, which means you see only the content relevant to your organization. In addition, you can access all of your Alert Logic products, across all your data-residencies, within one portal. Other features in this release include:

* The upgraded reporting console provides richer, interactive reports. The new reporting console is intuitively organized and easily searchable. Incident Analysis reports provide valuable insights and trending data for incidents created from all subscribed detection sources (Network IDS, Log Management, Web App IDS, and Amazon GuardDuty). Service Summary reports provide summary information and visibility into product configuration, product status, and security outcomes from your subscribed services.
* Enhanced portal navigation improves your ability to find everything you need across the entire Alert Logic portfolio. The top-level navigation is organized around functional categories (incidents, remediations, search, reports), and is subscription-aware, so you see only the content relevant to your organization.
* Streamlined Deployments page the Deployments page provide a single menu to create, view, and edit deployments for all Alert Logic products. In addition, for Cloud Insight Essentials customers:
   * You can use CloudFormation templates to easily create the IAM roles necessary to create Cloud Insight and Cloud Insight Essentials.
   * Deployment tiles clearly display the level of assessment chosen for your deployments.
   * You can use the new Guided Mode to create Cloud Insight deployments for which you determine where to deploy scanning instances in your infrastructure.
* Role-based user permissions allow you to quickly and easily provision new users and modify existing permission levels using an industry standard, role-based model. This enhancement allows you to assign users to one of five of the following roles
   * Administrator
   * Owner
   * Power User
   * Support/Care
   * Read-only
* Multi-factor authentication (MFA) adds a second layer of protection to your login. This opt-in feature enables you to further protect your organization from compromised credentials. MFA gives you the option to decide to enable the feature either at the account level if you wish to make MFA mandatory, or on a per individual user level. Alert Logic leverages Google Authenticator on mobile phones as the technology for the hardware-based authentication.

    2017    ### Release date: May 30, 2017

#### Bug fixes

None

#### Features

* Alert Logic updated the Alert Logic console for the Cloud Defender suite of products, specifically for Log Manager and Threat Manager.  Access to the Classic UI and the ability to switch between the two is currently available.  For more information, click [Improved Experience for Cloud Defender Console | Software Updates](https://support.alertlogic.com/hc/en-us/articles/115002610906).

#### Security

None

#### Changes

None

#### Notice

None

## Release date 

March 16, 2017

## Bug fixes

* N/A

## Features

The Alert Logic login page now allows you to reset your password. An update to the login page includes color scheme modifications and a highly requested feature  – the ability to reset your password.

**NOTE:** If you lock your user interface account after multiple failed login attempts, you cannot use the password reset function to unlock your account. You must contact your service provider or the Alert Logic help desk to unlock your account.

## Security

* N/A

## Changes

* N/A

## Notice

* N/A

## Release date 

February 16, 2017

## Bug fixes

* N/A

## Features

* This release adds a customer selector that allows you to select one customer or a parent customer and all of its child customers.
* This release decouples the page load from query execution.

## Security

* N/A

## Changes

* N/A

## Notice

* N/A

    2016    ## Release date 

June 6, 2016

## Bug fixes

* N/A

## Features

* This release provides a new web technology update and a new web CSS theme that is applied to the current web portal. This does not affect navigation, menu, or workflow, as this is only a web skin update.
* This release provides a new task and notification bar, as well as an AWS account IDs page for Threat Manager customers with agents and appliances installed within an AWS account.

## Security

* N/A

## Changes

* A new CSS theme applied to the current NGUI
* A new operating system (from Debian Squeeze to CentOS 6.7)
* PHP version upgraded to 5.6.20
* Support to the latest version of TLS (TLS 1.2)

## Notice

* N/A
