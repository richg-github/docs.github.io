# Managed Detection and Response Reports Upgrade

The Alert Logic Managed Detection and Response platform offers an enhanced and improved experience  for customers  upgrading from Cloud Defender, which includes upgrades to the Reports feature. This document is intended to help you find similar information from Cloud Defender Scheduled reports in the Managed Detection and Response Alert Logic console.

The Reports feature is available to all Managed Detection and Response product subscriptions. The Alert Logic console shows only the tabs and pages associated with your product subscription. This document describes all possible tabs and pages, but specifies the subscriptions that generate the tabs and pages.  For more information about Alert Logic subscriptions and other features included with each subscription, see [Get Started with Alert Logic   Subscriptions and Add-ons](subscriptions-addons.md).

## Changes to your Reports experience

Your Report experience includes most of the information that was available to you in the Cloud Defender reports. Some reports have been moved to other report groups or are under other report categories in the same report group. Other Cloud Defender reports have been deprecated from the Managed Detection and Response.  You can find similar information that was contained in Cloud Defender reports in other parts of the Alert Logic console.

Alert Logic will also release new reports to the Reports feature in the future, as indicated in the  reports mapping sections.

This document includes the following sections:

* [About the Reports page in the Alert Logic console](#About)—Find the Reports page and learn about its content
* [Report mapping from Cloud Defender to Managed Detection and Response](#Report)—Find the new location of your reports
   * [Universal reports mapping](#Universa)
      * [Deprecated reports](#Deprecat)
      * [Future reports ](#Future)
   * [Incident reports mapping](#Incident)
      * [Deprecated reports](#Deprecat2)
      * [Future reports ](#Future2)
   * [Event reports mapping](#Event)
      * [Deprecated reports](#Deprecat3)
   * [Vulnerability reports mapping](#Vulnerab)
   * [Log reports mapping](#Log)
      * [Deprecated Log reports](#Deprecat4)
      * [Future Log reports](#Future3)
   * [Compliance reports mapping](#Complian)
      * [Future reports](#Future4)

## About the Reports page in the Alert Logic console

To access the Reports page in the Alert Logic console, click the menu icon (![](../Resources/Images/dashboard/menu-icon.png)), and then click ![](../Resources/Images/dashboard/validate-icon.png)**Validate**. Click **Reports**. On the Reports page, the following report categories are available, which have reports associated with that report category:

* [Risk Reports](../analyze/reports/risk/reports.md#Risk)—Provide convenient access to analysis, statistics, assessments, and trending data related to your security and health posture, threat risk index, and enterprise risks. All subscriptions see this content.
* [Threats Reports](../analyze/reports/threats/reports.md#Threats)—Provide convenient access to analysis, statistics, assessments, and trending data related to threats and incidents detected from your subscribed products and services. This content requires a Professional or Enterprise subscription.
* [Vulnerabilities Reports](../analyze/reports/Vulnerabilities/reports.md#Vulnerabilities)—Provide convenient access to analysis, statistics, assessments, and trending data related to vulnerabilities discovered in your environment based on scanning outcomes.   All subscriptions see this content.
* [Remediations Reports](../analyze/reports/remediations/reports.md#Remediations)—Provide convenient access to analysis, statistics, assessments, and trending data related to configuration issues and security exposures from your subscribed products and services. All subscriptions see this content.
* [Compliance Reports](../analyze/reports/compliance/reports.md#Compliance)—Provide convenient access to analysis, statistics, and trending data related to compliance assessment status and audit preparedness from your subscribed products and services. All subscriptions see this content.
* [Service Reports](../analyze/reports/service/reports.md#Service)—Provide convenient access to data related to entitlements, capability usage, users and security content for your subscribed products and services. This content requires a Professional or Enterprise subscription.

Each report allows you to  download the report as an image, data, crosstab, PDF, or PowerPoint file. To learn how to download reports, see [Report Download Option](../analyze/reports/download-option.md).

You can also schedule a report to run periodically and subscribe users to receive a notification when the report is generated.   For more information, see [Scheduled Reports and Notifications](../configure/notifications/report.md).

For a complete guide to reports types, categories, descriptions, and features offered in the Reports page, see [Reports Guide](../analyze/reports/reports.md).

## Report mapping from Cloud Defender to Managed Detection and Response

Cloud Defender  reports are separated into the following categories:

* [Universal reports mapping](#Universa)
* [Incident reports mapping](#Incident)
* [Event reports mapping](#Event)
* [Vulnerability reports mapping](#Vulnerab)
* [Log reports mapping](#Log)
* [Compliance reports mapping](#Complian)

Case reports are not applicable in the Managed Detection and Response platform.

### Universal reports mapping

Use the following table to find the information from the Universal reports.

| Universal Report | Managed Detection and Response Report Replacement | Location in the Reports page |
|---|---|---|
| Enterprise Report | [Monthly Enterprise Risk](../analyze/reports/risk/enterprise-risk/monthly-enterprise.md) and [Weekly Enterprise Risk](../analyze/reports/risk/enterprise-risk/weekly-enterprise.md) | Click   the **Risk** tab, and then click **Enterprise Risk**. Click **VIEW**. |
| CIO Threat Report |
| CIO Threat Trend Report | [Incident Daily Digest Trends](../analyze/reports/threats/incident-analysis/incident-daily-digest-trends.md) | Click  **Threats** tab, and then click **Incident Analysis**. Click **VIEW**, and then click **Incident Daily Digest Trends**. |
| Threat Security Report | [Monthly Security Posture Report](../analyze/reports/risk/monthly-security-posture.md) | Click   the **Risk** tab, and then click **Security Posture**. Click **VIEW**, and then click **Monthly Security Posture**. |
| Active Users Report | [Current Users](../analyze/reports/service/users/current-users.md) | Click   the **Service** tab, and then click Users. Click **VIEW**, and then click **Current Users**. |

#### Deprecated reports

You can find similar information from the deprecated Universal reports  in other parts of the Alert Logic console. The following Universal reports have been deprecated.

| Deprecated Report | Alert Logic console location | Location in the Alert Logic console page |
|---|---|---|
| Blocked Hosts Report | Blocking hosts is not supported in Managed Detection and Response. You can find other information for log sources, appliances, and hosts in the [Health](../analyze/health.md) page. | Click the menu icon (![](../Resources/Images/dashboard/menu-icon.png)), and then click ![](../Resources/Images/dashboard/respond-icon.png)**Respond**. Click **Health**. |
| Active Sources Report | You can find information for log sources, appliances, and hosts in the [Health](../analyze/health.md) page. | Click the menu icon (![](../Resources/Images/dashboard/menu-icon.png)), and then click ![](../Resources/Images/dashboard/respond-icon.png)**Respond**. Click **Health**. |

#### Future reports 

For reports that will be available in the future, you can still find related information in the Alert Logic console.

For the User's Actions Log report, you can find the information related to a user's activity in  the User Login Trends report in the Reports page.  To learn more about this report, see [User Login Trends](../analyze/reports/service/users/login-trends.md).

To access the User Logins Trends report, click   the **Service** tab, and then click Users. Click **VIEW**, and then click **User Login Trends**.

### Incident reports mapping

Use the following table to find the information from the Incident reports.

| Incident Report | Managed Detection and Response Report Replacement | Location in the Reports page |
|---|---|---|
| Executive Summary | [Monthly Incident Account Summary](../analyze/reports/threats/incident-account-summary/monthly-incident-account.md) and [Weekly Incident Account Summary](../analyze/reports/threats/incident-account-summary/weekly-incident-account.md) | Click   the **Threats** tab, and then click **Incident Account Summary**. Click **VIEW**. |
| Full Report | [Monthly Incident Analysis ](../analyze/reports/threats/incident-analysis/monthly-incident.md) and [Weekly Incident Analysis](../analyze/reports/threats/incident-analysis/weekly-incident.md) | Click   the **Threats** tab, and then click **Incident Analysis**. Click **VIEW**. |
| Incidents By Status | [Incident Daily Digest](../analyze/reports/threats/incident-analysis/incident-daily-digest.md) and [Incident Distribution Explorer](../analyze/reports/threats/incident-analysis/incident-dist-explorer.md) | Click   the **Threats** tab, and then click **Incident Analysis**. Click **VIEW**. |
| Incidents by Classification |
| Incidents by Threat Level |
| Incidents By Time |
| Incidents by Summary | [Monthly Incident Analysis ](../analyze/reports/threats/incident-analysis/monthly-incident.md) and [Weekly Incident Analysis](../analyze/reports/threats/incident-analysis/weekly-incident.md) | Click   the **Threats** tab, and then click **Incident Analysis**. Click **VIEW**. |
| Top Hosts Triggering Incidents | [Incident Target Explorer Report](../analyze/reports/threats/incident-analysis/incident-target-explorer.md) | Click   the **Threats** tab, and then click **Incident Analysis**. Click **VIEW**, and then click **Incident Target Explorer**. |

#### Deprecated reports

The information that was found in the deprecated Incident reports are no longer applicable to the Managed Detection and Response platform. The following Incidents reports have been deprecated with no plan for replacement:

* Internal vs External
* Incident/Block/Rollback Trends

For incident information and other data, you can refer to the [Incidents](../analyze/incidents.md) page, and also [Incident Analysis](../analyze/reports/threats/reports.md#incidentAnalysis) reports.

#### Future reports 

For reports that will be available in the future, you can still find related information in the Alert Logic console. For the Incident Details report, you can also find information for incidents in the [Incidents](../analyze/incidents.md) page. To access the Incidents page,  click the menu icon (![](../Resources/Images/dashboard/menu-icon.png)), and then ![](../Resources/Images/dashboard/respond-icon.png)**Respond**. Click **Incidents**.

### Event reports mapping

Use the following table to find the information from the Event reports.

| Event Report | Managed Detection and Response Report Replacement | Location in the Reports page |
|---|---|---|
| Executive Summary | [Network IDS Events Explorer](../analyze/reports/threats/event-analysis/network-ids-events-explorer.md#Incident3) | Click   the **Threats** tab, and then click **Event Analysis**. Click **VIEW**, and then click Network IDS** Events Explorer**. |
| Full Report | [Monthly Event Analysis](../analyze/reports/threats/event-analysis/monthly-event-analysis.md#Incident3) and [Weekly Event Analysis](../analyze/reports/threats/event-analysis/weekly-event-analysis.md) | Click   the **Threats** tab, and then click **Event Analysis**. Click **VIEW**, and then click **Monthly Event Analysis** or **Weekly Event Analysis**. |
| Event By Time |
| Events by Classification | [Network IDS Events Explorer](../analyze/reports/threats/event-analysis/network-ids-events-explorer.md#Incident3) | Click   the **Threats** tab, and then click **Event Analysis**. Click **VIEW**, and then click **Network IDS Events Explorer**. |
| Top Signatures | [Top Event Sources and Destinations](../analyze/reports/threats/event-analysis/top-sources-destinations.md) | Click   the **Threats** tab, and then click **Event Analysis**. Click **VIEW**, and then click **Top Event Sources and Destinations**. |
| Top Source Addresses |
| Top Source Ports |
| Top Destination Addresses |
| Top Destination Ports |
| Top Source/Destination Combinations |
| Events Per Second By Customer | [IDS Traffic](../analyze/reports/service/capability-usage/network-ids-traffic.md) | Click   the **Service** tab, and then click **Capability Usage**. Click **VIEW**, and then click **IDS Traffic**. |

#### Deprecated reports

The information that was found in the deprecated Incident reports are no longer applicable to the Managed Detection and Response platform. The following Event reports have been deprecated with no plan for replacement:

* Events by Threat Level
* Internal vs. External Events

The following Events reports have been deprecated and the information that was found in these reports exists in other part of the Alert Logic console.

| Event Report | Alert Logic console location | Location in the Alert Logic console page |
|---|---|---|
| Events - Detail | You can find information for events in the Events page. | Click the menu icon (![](../Resources/Images/dashboard/menu-icon.png)), and then click ![](../Resources/Images/dashboard/investigate-icon.png)**Investigate**. Click **Search**, and then click **Events**. |
| Event Export By Malware and SQL Injection | You can find information for events in the Events page. | Click the menu icon (![](../Resources/Images/dashboard/menu-icon.png)), and  then click ![](../Resources/Images/dashboard/investigate-icon.png)**Investigate**. Click **Search**, and then click **Events**. |

### Vulnerability reports mapping

Use the following table to find the information from the Vulnerability reports.

| Vulnerability Report | Managed Detection and Response Report Replacement | Location in the Reports page |
|---|---|---|
| Executive Summary | [Monthly Vulnerability Summary](../analyze/reports/Vulnerabilities/vulnerability-analysis/vulnerability-summary.md#Incident3) and [Weekly Vulnerability Summary](../analyze/reports/Vulnerabilities/vulnerability-analysis/weekly-vulnerability-summary.md) | Click   the **Vulnerabilities** tab, and then click **Vulnerability Analysis**. Click **VIEW**, and then click **Monthly Vulnerability Summary** or **Weekly Vulnerability Summary**. |
| Full Report | [Monthly Vulnerability Analysis ](../analyze/reports/Vulnerabilities/vulnerability-analysis/monthly-vulnerability.md) and [Weekly Vulnerability Analysis](../analyze/reports/Vulnerabilities/vulnerability-analysis/weekly-vulnerability.md) | Click   the **Vulnerabilities** tab, and then click **Vulnerability Analysis**. Click **VIEW**, and then click **Monthly Vulnerability Analysis** or **Weekly Vulnerability Analysis**. |
| Historical View of Vulnerabilities | [Monthly Vulnerability Summary](../analyze/reports/Vulnerabilities/vulnerability-analysis/vulnerability-summary.md#Incident3) and [Weekly Vulnerability Summary](../analyze/reports/Vulnerabilities/vulnerability-analysis/weekly-vulnerability-summary.md) | Click   the **Vulnerabilities** tab, and then click **Vulnerability Analysis**. Click **VIEW**, and then click **Monthly Vulnerability Summary** or **Weekly Vulnerability Summary**. |
| Top 10 Vulnerabilities | [Monthly Top 10 Vulnerability Lists](../analyze/reports/Vulnerabilities/vulnerability-analysis/vulnerability-top-ten.md) and [Weekly Top 10 Vulnerability Lists](../analyze/reports/Vulnerabilities/vulnerability-analysis/weekly-vulnerability-top-ten.md) | Click   the **Vulnerabilities** tab, and then click **Vulnerability Analysis**. Click **VIEW**, and then click **Monthly Top 10 Vulnerability Lists** or **Weekly Top 10 Vulnerability Lists**. |
| Vulnerabilities by Age | [Monthly Vulnerability Summary](../analyze/reports/Vulnerabilities/vulnerability-analysis/vulnerability-summary.md#Incident3) and [Weekly Vulnerability Summary](../analyze/reports/Vulnerabilities/vulnerability-analysis/weekly-vulnerability-summary.md) | Click   the **Vulnerabilities** tab, and then click **Vulnerability Analysis**. Click **VIEW**, and then click **Monthly Vulnerability Summary** or **Weekly Vulnerability Summary**. |
| Vulnerabilities by Risk Level |
| Most Vulnerable Zones | [Monthly Vulnerability Analysis ](../analyze/reports/Vulnerabilities/vulnerability-analysis/monthly-vulnerability.md) and [Weekly Vulnerability Analysis](../analyze/reports/Vulnerabilities/vulnerability-analysis/weekly-vulnerability.md) | Click   the **Vulnerabilities** tab, and then click **Vulnerability Analysis**. Click **VIEW**, and then click **Monthly Vulnerability Analysis** or **Weekly Vulnerability Analysis**. |
| Most Vulnerable Host Groups |
| Most Vulnerable Service Types |
| Hosts By Vulnerabilities | [Current Vulnerabilities Breakdown](../analyze/reports/Vulnerabilities/current-vulnerabilities-breakdown.md) | Click **Vulnerabilities** tab, and then click **Current Vulnerability Breakdown**. Click **VIEW**, and then click **Current Vulnerabilities Breakdown**. |
| Detailed Hosts By Vulnerabilities |
| Vulnerabilities by Hosts | [Current Vulnerable Hosts Breakdown](../analyze/reports/Vulnerabilities/current-vulnerable-hosts-breakdown.md) | Click **Vulnerabilities** tab, and then click **Current Vulnerable Hosts Breakdown**. Click **VIEW**, and then click **Current Vulnerable Hosts Breakdown**. |
| Detailed Vulnerabilities by Host |

### Log reports mapping

Use the following table to find the information from the Log reports.

| Log Report | Managed Detection and Response Report Replacement | Location in the Reports page |
|---|---|---|
| Executive Summary | [Top 10 Log Collectors](../analyze/reports/service/capability-usage/top-ten-log-collectors.md) | Click   the **Service** tab, and then click **Capability Usage**. Click **VIEW**, and then click **Top 10 Log Collectors**. |
| Full Report | [Log Collection](../analyze/reports/service/capability-usage/log-collection.md) | Click   the **Service** tab, and then click **Capability Usage**. Click **VIEW**, and then click **Log Collection**. |

#### Deprecated Log reports

The Log reports have been deprecated and the information that was found in these reports exist in the [Search: Log Messages](../analyze/log-message-search.md) page in the Alert Logic console. You can use the [Examples of Common Log Message Searches](../analyze/log-search/log-search-examples.md) to generate search results that were found in the following reports:

* Invalid Credential Report
* No Hosts on Appliance
* No Windows Logs
* No Logs
* Log Source Last Collected
* Error Sources Status History
* Log Collection Health

To access the Log Search page,  click the menu icon (![](../Resources/Images/dashboard/menu-icon.png)), and then click ![](../Resources/Images/dashboard/investigate-icon.png)**Investigate**. Click **Search**.

#### Future Log reports

For the Log Source Activity report, you can use the [Examples of Common Log Message Searches](../analyze/log-search/log-search-examples.md) to generate search results from the [Search: Log Messages](../analyze/log-message-search.md) page. To access the Log Search page,  click the menu icon (![](../Resources/Images/dashboard/menu-icon.png)), and then click ![](../Resources/Images/dashboard/investigate-icon.png)**Investigate**. Click **Search**.

You can also find information for log collection statuses in the [Health](../analyze/health.md) page. To access the Health page, click the menu icon (![](../Resources/Images/dashboard/menu-icon.png)), and then click ![](../Resources/Images/dashboard/respond-icon.png)**Respond**. Click **Health**.

### Compliance reports mapping

Use the following table to find the information from the Compliance reports.

| Compliance Report | Managed Detection and Response Report Replacement | Location in the Reports page |
|---|---|---|
| PCI Reports - Executive Summary | [PCI DSS Audit](../analyze/reports/compliance/reports.md#PCI_DSS_Audit) | Click   the **Compliance** tab, and then click **PCI DSS Audit**. Click **VIEW**. |
| PCI Reports - Full Report |
| HIPAA Reports - Executive Summary | [HIPAA-HITECH Security Audit](../analyze/reports/compliance/reports.md#HIPAASecurityAudit) | Click   the **Compliance** tab, and then click **HIPAA-HITECH Security Audit**. Click **VIEW**. |
| HIPAA Compliance - Full Report |

#### Future reports

The following Compliance reports will be replaced in the future:

* GLB Compliance - Executive Summary
* GLB Compliance - Full Report
* SOX Reports - Executive Summary
* SOX Compliance - Full Report
