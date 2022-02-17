# Reports Guide

The  Reports page in the Alert Logic console provides access to data related to exposures and incidents Alert Logic found within your deployments. You can also view data related to your product usage within your accounts.

Report data is cached and refreshed at regular intervals. As a result, periodic delays to reflect the latest data in the console can occur.

Depending on your Alert Logic subscriptions, you will see some or all of the following report types:

* [Risk Reports](risk/reports.md#Risk)—Provide convenient access to analysis, statistics, assessments, and trending data related to your security and health posture, threat risk index, and enterprise risks. Each report provides interactive filtering options, visual representations of the data, and informative tooltips. All subscriptions see this content.
* [Threats Reports](threats/reports.md#Threats)—Provide convenient access to analysis, statistics, assessments, and trending data related to threats and incidents detected from your subscribed products and services. Each report provides interactive filtering options, visual representations of the data, and informative tooltips. This content requires a Professional or Enterprise subscription.
* [Vulnerabilities Reports](Vulnerabilities/reports.md#Vulnerabilities)—Provide convenient access to analysis, statistics, assessments, and trending data related to vulnerabilities discovered in your environment based on scanning outcomes. Each report provides interactive filtering options, visual representations of the data, and informative tooltips.  All subscriptions see this content.
* [Remediations Reports](remediations/reports.md#Remediations)—Provide convenient access to analysis, statistics, assessments, and trending data related to configuration issues and security exposures from your subscribed products and services. Each report provides interactive filtering options, visual representations of the data, and informative tooltips.  All subscriptions see this content.
* [Compliance Reports](compliance/reports.md#Compliance)—Provide convenient access to analysis, statistics, and trending data related to compliance assessment status and audit preparedness from your subscribed products and services. Each report provides interactive filtering options, visual representations of the data, and informative tooltips. All subscriptions see this content.
* [Service Reports](service/reports.md#Service)—Provide convenient access to data related to entitlements, capability usage, users and security content for your subscribed products and services. Each report provides interactive filtering options, visual representations of the data, and informative tooltips. This content requires a Professional or Enterprise subscription.
* [WAF Reports](WAF/reports.md) —Provide convenient access to activity and policy information for the Alert Logic Managed Web Application Firewall (WAF) service. This content requires WAF purchased as an add-on.

Each report allows you to share its data by email, or download the report as an image, data, crosstab, PDF, or PowerPoint files. To learn how to download reports, see [Report Download Option](download-option.md).

You can also schedule a report to run periodically and subscribe users or an integration (such as a webhook) to receive a notification when the report is generated.   From the Downloads tab on the Reports page, you can download and manage reports generated from your schedules. For more information, see [Scheduled Reports and Notifications](../../configure/notifications/report.md).

## Filtering reports

You can  filter your reports quickly to refine your results and generate relevant information you need. Each report has a set of filters located at the top that you can select or clear for the filters you want to see. Alert Logic also allows you to add or remove some or all values in a filter you want to see. Some reports also support filtering by visuals.

### Filter the report using drop-down menus

By default, Alert Logic includes **(All)** filter values in the report.

**To add or remove filter values: **

1. Click the drop-down menu in the filter, and then select or clear values.
2. Click **Apply**.

### Filter the report using visuals

To refine your findings, click an item within a visual. To filter by multiple items, hold down **Ctrl** or **Command**, and then click each item in a visual that you want  to use to apply a filter. You can filter using visuals and items  selected in different sections. Click on an item again to remove a filter.

* **Bar graph example text**: To filter the report, click on a bar or hold **Ctrl** or **Command** and click  multiple bars to filter all sections by the selected Threat Level(s).
* **Line graph example text**: To filter the report, click on a point or choose an area on the line graph to filter the other sections by the selected week(s). Click a point or area on the line to filter all sections by your selection.
* **Pie chart**: To filter the report, select one or more sector to filter all sections on the page by your selection.
* **Histogram chart example text**: To filter the report, click on a bar or hold **Ctrl** or **Command** and click  multiple bars to filter all sections by the selected date(s).

## Risk 

The Risk reports provide convenient access to analysis, statistics, assessments, and trending data related to your security and health posture and threat risk index.

Alert Logic provides Risk reports within the following categories:

* [Security Posture ](#Security)—Provide comparative trending analysis to help you improve your overall security posture, reduce threat risk index scores, and optimize the security product and service capabilities deployed in your environment.
* [Threat Risk Index ](#Threat-Risk)—Provide valuable summary and trending data for the threat risk index scores for the deployments and networks in your environment. You can gain insight into emerging threats and learn which assets in your environment are most at risk.
* [Enterprise Risk](#Enterpri)—Provides valuable insights and analysis of your incidents, events, and vulnerabilities. You can evaluate threats and incidents and your response efforts, validate events and focus your efforts, and gain insights into the effectiveness of your vulnerability management.

To access the Risk reports, in the Alert Logic console, click the **Reports** tab, and then click **Risk**.

### Security Posture 

You can run the following reports that information your overall security posture:

* **Monthly Security Posture: **Provides the current and historic security risk and health posture of your environment, including configuration remediations and risk posture overviews, vulnerabilities assessment, and threat analysis. To learn more about this report, see [Monthly Security Posture Report](risk/monthly-security-posture.md).

### Threat Risk Index 

You can run the following reports that provide valuable summary and trending data for the threat risk index scores:

* **TRI Summary:** Provides the current threat risk index (TRI) scores of your environment, including the overall TRI score and trends, score details, risk index asset distribution charts, and top ten lists. To learn more about this report, see [TRI Summary](risk/tri-summary.md).
* **TRI Summary:** Provides the current threat risk index (TRI) scores of your environment, including the overall TRI score and trends, score details, and risk index asset distribution charts. To learn more about this report, see [TRI Summary](risk/tri-summary.md).
* **Top 10 TRI Lists**: Provides  top 10 lists of your most vulnerable hosts by TRI score, and the top 10 vulnerabilities by TRI score. To learn more about this report, see [Top 10 TRI Lists](risk/top-ten-TRI-list.md).
* **TRI Trends:** Provides insights into threat risk index (TRI) averages and trends in reducing risks, including TRI scores, total vulnerability and host counts, internet-facing vulnerabilities, exploit availability, and last scanned age. To learn more about this report, see [TRI Trends Report](risk/tri-trends.md).

### Enterprise Risk

You can run the following reports that provide insights into your incidents, events, vulnerabilities:

* **Monthly Enterprise**: Provides valuable monthly insights and analysis of your incidents, events, and vulnerabilities in your environment.To learn more about this report, see [Monthly Enterprise Risk](risk/enterprise-risk/monthly-enterprise.md).
* **Weekly Enterprise**: Provides valuable monthly insights and analysis of your incidents, events, and vulnerabilities in your environment.To learn more about this report, see [Weekly Enterprise Risk](risk/enterprise-risk/weekly-enterprise.md).

## Threats 

The Threats reports provide convenient access to analysis, statistics, assessments, and trending data related to threats and incidents detected from your subscribed products and services. Alert Logic provides Threats reports within the following categories:

* [Incident Analysis](#incidentAnalysis) — Provides valuable insights and trending data for incidents created from all subscribed detection sources (Network IDS, Log Management, Amazon GuardDuty).
* [AWS Incident Analysis ](#AWSincident)— Provide valuable insights and trending data for incidents discovered in your AWS environments from Network IDS and incidents generated by Amazon GuardDuty security findings.
* [Azure Incident Analysis ](#Azureincident)— Provides valuable insights and trending data for incidents in your Azure environments created from Network IDS detection sources.
* [Log Review Analysis](#Log)— Provide valuable insights and trending data for incidents that are reviewed daily by Alert Logic security analysts.
* [ Web Application Analysis](#Web) — Provide valuable summary, distribution, and trending data for policy violations from your Alert Logic Managed Web Application Firewall (WAF).
* [Event Analysis](#Event) — Provides valuable insights and trending data for security events that were detected and processed in your environment from Network IDS sources.

To access the Threats reports, in the Alert Logic console, click the **Reports** tab, and then click **Threats**.

### Incident Analysis

You can run the following reports that provide information about incidents in your  environments created from all subscribed detection sources (Network IDS, Log Management, Web App IDS, Amazon GuardDuty):

* **Monthly Incident Analysis**: Provides visibility into threats and incidents in your environment, including incident statuses, threat levels, classification, daily incident count, and top ten lists for the selected month.To learn more about this report, see [Monthly Incident Analysis ](threats/incident-analysis/monthly-incident.md).
* **Weekly Incident Analysis**: Provides visibility into threats and incidents in your environment, including incident statuses, threat levels, classification, daily incident count, and top ten lists for the selected week. To learn more about this report, see [Weekly Incident Analysis](threats/incident-analysis/weekly-incident.md).
* **Incident Daily Digest:** Presents the incidents detected on the previous day for the selected detection types. You can view visualizations and list of incidents by threat level, by classification, or by incident type. You can filter the report by detection source, status, previous days, or customer account. You can check **ALL** to see all values available in a filter, or select only specific ones.
* **Incident Daily Digest Trends:** Presents a histogram chart that allows you to focus on the daily incident digests results within the specified date range. You can view visualizations and list of incidents by threat level, by classification, or by incident type. You can filter the report by detection source, status, previous days, or customer account. You can check **ALL** to see all values available in a filter, or select only specific ones.
* **Incident Distribution Explorer:** Presents incidents by threat level, classification, and incident type for the selected detection sources, statuses, and a specified time period. You can filter the report by detection source, status, previous days, or customer account. You can check **ALL** to see all values available in a filter, or select only specific ones.
* **Incident Target Explorer:** Displays the top 10 targets, with visualizations and lists of incidents by threat level, by classification, or by incident type. You can filter the report by detection source, status, previous days, or customer account. You can check **ALL** to see all values available in a filter, or select only specific ones.
* **Incident Attacker Explorer:** Displays the top 10 attackers and geolocations, with visualizations and lists of incidents by threat level, by classification, or by incident type. You can filter the report by detection source, status, previous days, or customer account. You can check **ALL** to see all values available in a filter, or select only specific ones.
* **Incident Workflow Explorer:**Evaluates workflow actions performed in response to incidents, including total incidents by action count and percentage, total daily workflow actions, closed and updated incidents by reason, and trends. You can filter the report by detection source, status, previous days, or customer account. You can check **ALL** to see all values available in a filter, or select only specific ones.

### AWS Incident Analysis 

You can run the following reports that provide information about incidents in your AWS environments generated by Network IDS:

* **AWS Incident Daily Digest:** Displays the incidents received the previous day for the selected deployments. You can view the List of Incidents by threat level, classification type, or by GuardDuty findings. You can filter this report by deployment, VPC, container image, and detection source. You can check **ALL** to see all values available in a filter, or select only specific ones.
* **AWS Incident Daily Digest Trends:** Allows you to view a histogram chart that displays the incident daily digests for specified date range, and by deployment, VPC, container image, and detection source. You can check **ALL** to see all values available in a filter, or select only specific ones.
* **AWS Incident Distribution Explorer:** Displays incidents by threat level, classification, and incident type for a specified time period. You can filter the report by date range, detection source, deployment, and AWS account ID, container image, subnet, security group, and tag. You can check **ALL** to see all values available in a filter, or select only specific ones.
* **AWS Targeted Deployment Explorer:** Displays the GuardDuty and Network IDS incident distribution for a specified target (AWS account ID, regions, VPC, container image, security group or subnet), filtered by AWS account ID, date range, detection source, deployment, and AWS asset within your deployments. You can check **ALL** to see all values available in a filter, or select only specific ones.
* **AWS Targeted Deployment Trends:** Displays an interactive graph depicting incident distribution for a specified time period, by account ID, AWS region, and AWS asset. You can check **ALL** to see all values available in a filter, or select only specific ones.

### Azure Incident Analysis 

You can run the following reports that provide information about incidents in your Azure environments generated by Network IDS

* Azure **Incident Daily Digest:** Displays Network IDS incidents received the previous day for the selected deployments. You can view the List of Incidents by threat level, classification, or incident type. You can filter this report by deployment, VNET, container image, and detection source. You can check **ALL** to see all values available in a filter, or select only specific ones.
* Azure **Incident Daily Digest Trends:** Allows you to view a histogram chart that displays the Azure daily incident digests for specified date range, customer account, by deployment, VNET, container image, and detection source. You can check **ALL** to see all values available in a filter, or select only specific ones.
* Azure **Incident Distribution Explorer:** Displays incidents by threat level, classification, and incident type for a specified time period. You can filter the report by date range, customer account, detection source, deployment, native account ID, container image name, subnet, security group, and tag. You can check **ALL** to see all values available in a filter, or select only specific ones.
* Azure **Targeted Deployment Explorer:** Displays the Network IDS incident distribution for a specified target (Native Account ID, regions, VNET, container image, security group or subnet), filtered by Native Account ID, date range, detection source, deployment, and other Azure assets within your deployments. You can check **ALL** to see all values available in a filter, or select only specific ones.
* Azure **Targeted Deployment Trends:** Displays an interactive graph depicting the Network IDS incident distribution for a specified time period, by Native Account ID, VNET, containers,  and other Azure assets within your deployment. You can check **ALL** to see all values available in a filter, or select only specific ones.

### Log Review Analysis

You can run the following report that provides insight into your Log Review incidents created in the Incidents page:

* **Monthly Log Review**: Provides a monthly summary analysis of your Log Review incidents, including count and percentage of total incidents of each status, a daily histogram chart, and a comparison to the previous month. To learn more about this report, see [Monthly Log Review Report](threats/log-review-analysis/monthly-log-review.md).

###  Web Application Analysis

You can run the following report that provides information for policy violations from your inline Alert Logic Managed Web Application Firewall (WAF).

* WAF** Violation Explorer:** Provides visibility into blocked WAF requests and attempted web app attacks, including total and blocked WAF policy violations counts, violations by day, operating mode, risk level, attack class, and type. To learn more about this report, see [WAF Violation Explorer Report](threats/web-application-analysis/waf-violation-explorer.md).
* **WAF Violation Trends:** Provides insights into patterns in your WAF violations, including violation distribution and trends categorized by action, risk level, attack class, violation type, response code, method, and protocol. To learn more about this report, see [WAF Violation Trends](threats/web-application-analysis/waf-violation-trends.md).

### Event Analysis

You can run the following report that provides insights for security events that were processed from Network IDS sources:

* Network IDS** Events Explorer**: Provides visibility into Network IDS events processed in your environment, including events per day, visualizations by payload and classification, top signatures, and top source and destination IP addresses and ports. To learn more about this report, see [Network IDS Events Explorer](threats/event-analysis/network-ids-events-explorer.md).
* **Monthly Event Analysis**: Provides visibility into Network IDS events processed in your environment, including event classification, top signatures, and events per day for the selected month.To learn more about this report, see [Monthly Event Analysis](threats/event-analysis/monthly-event-analysis.md).
* **Weekly Event Analysis**: Provides visibility into Network IDS events processed in your environment, including event classification, top signatures, and events per day for the selected weekly.To learn more about this report, see [Weekly Event Analysis](threats/event-analysis/weekly-event-analysis.md).
* Network IDS** Events Explorer**: Provides visibility into Network IDS events processed in your environment, events per day, visualizations by payload and classification, and top signatures. To learn more about this report, see [Network IDS Events Explorer](threats/event-analysis/network-ids-events-explorer.md).
* **Top Event Sources and Destinations**: Lists the top source and destination IP addresses and ports for IDS events in your environment. To learn more about this report, see [Top Event Sources and Destinations](threats/event-analysis/top-sources-destinations.md).

## Vulnerabilities 

The Vulnerability Reports provide convenient access to analysis, statistics, assessments, and trending data related to vulnerabilities discovered in your environment based on scanning outcomes. Alert Logic provides Vulnerabilities reports within the following categories:

* [Vulnerability Analysis](#vulnerabilityAnalysis)—Provide valuable summary, distribution and trending data for vulnerabilities discovered across your environment. You can gain insight into the effectiveness of your vulnerability management and prioritization efforts.
* [                Vulnerability Analysis - Full Reports]()—Provides valuable monthly and weekly summary insights into vulnerabilities and vulnerable assets found in your environment. You can gain insights into the effectiveness of your vulnerability management, help prioritize your efforts, and focus on specific areas.
* [Current Vulnerability Breakdown Reports](#currentvulnerabilitybreakdownreport)—Provide a breakdown of current vulnerability instances and vulnerable hosts ranked by count and severity with asset-level or vulnerability details.
* [Current Vulnerability Finder](#Current)—Provide valuable summary data and tabular lists for specific vulnerabilities and vulnerability instances found within your environment. You can export these reports and use them for further analysis.
* [Vulnerability List](#Vulnerab)—Provides a tabular list of vulnerabilities discovered within your scoped environments. You can export these reports and use them for further analysis.
* [Current Vulnerability Breakdown](#Current2)—Provide a per deployment breakdown of vulnerabilities, ranked by count and severity, with asset level detail.

To access the Vulnerability reports, in the Alert Logic console, click the **Reports** tab, and then click **Vulnerabilities**.

### Vulnerability Analysis

You can run the following reports that provide information for vulnerabilities discovered across your environment.

* **Monthly Vulnerability Summary:** Provides a summary of the month to month vulnerabilities found in your environment, including vulnerability and host counts, severity and age distribution, exportable vulnerability list, and categorized trends. To learn more about this report, see [Monthly Vulnerability Summary](Vulnerabilities/vulnerability-analysis/vulnerability-summary.md).
* **Weekly Vulnerability Summary:** Provides a summary of the week to week vulnerabilities found in your environment, including vulnerability and host counts, severity and age distribution, exportable vulnerability list, and categorized trends. To learn more about this report, see [Weekly Vulnerability Summary](Vulnerabilities/vulnerability-analysis/weekly-vulnerability-summary.md).
* **Monthly Top 10 Vulnerability Lists:** Provides top 10 lists for your most vulnerable hosts by total count and by severity, oldest critical vulnerabilities, and frequent vulnerabilities. To learn more about this report, see [Monthly Top 10 Vulnerability Lists](Vulnerabilities/vulnerability-analysis/vulnerability-top-ten.md).
* **Weekly Top 10 Vulnerability Lists:** Provides top 10 lists for your most vulnerable hosts by total count and by severity, oldest critical vulnerabilities, and frequent vulnerabilities. To learn more about this report, see [Weekly Top 10 Vulnerability Lists](Vulnerabilities/vulnerability-analysis/weekly-vulnerability-top-ten.md).
* **Monthly Vulnerability Host Explorer:** Provides a summary of the most vulnerable assets, including total host and vulnerability counts, hosts by CVSS severity ratings, and top ten lists. To learn more about this report, see [Monthly Vulnerable Hosts Explorer](Vulnerabilities/vulnerability-analysis/vulnerability-host-explorer.md).
* ** Monthly Vulnerable Hosts Change Trends:** Contains sections that show the percentage or count, and trend of vulnerable host changes over the selected time period. To learn more about this report, see [Monthly Vulnerable Hosts Change Trends](Vulnerabilities/vulnerability-analysis/vulnerable-hosts-trends.md).
* **Monthly Vulnerable Distribution Explorer:** Provides insights into patterns in your vulnerabilities, including vulnerability distribution and trends categorized by status, exploitability, severity, age, operating system, and asset type. To learn more about this report, see [Monthly Vulnerability Distribution Explorer](Vulnerabilities/vulnerability-analysis/vulnerability-distribution-explorer.md).
* **Weekly Vulnerable Distribution Explorer:** Provides insights into patterns in your vulnerabilities, including vulnerability distribution and trends categorized by status, exploitability, severity, age, operating system, and asset type. To learn more about this report, see [Weekly Vulnerability Distribution Explorer](Vulnerabilities/vulnerability-analysis/weekly-vulnerability-distribution-explorer.md).
* **Monthly Vulnerability Change Trends:** Provides  a summary of the percentage and count changes of vulnerabilities, and trend  by total and severity. To learn more about this report, see [Monthly Vulnerability Change Trends](Vulnerabilities/vulnerability-analysis/vulnerability-change-trends.md).

###                 Vulnerability Analysis - Full Reports

You can run the following reports that provide summary information for vulnerabilities discovered across your environment:

* **Monthly Vulnerability Analysis**: Provides insights into vulnerabilities and vulnerable assets found in your environment, including vulnerabilities by severity and age, vulnerability trends, vulnerabilities by day and severity, and top vulnerable hosts, networks, and deployment lists for the selected month. To learn more about this report, see [Monthly Vulnerability Analysis ](Vulnerabilities/vulnerability-analysis/monthly-vulnerability.md).
* **Weekly Vulnerability Analysis**: Provides insights into vulnerabilities and vulnerable assets found in your environment, including vulnerabilities by severity and age, vulnerability trends, vulnerabilities by day and severity, and top vulnerable hosts, networks, and deployment lists for the selected week. To learn more about this report, see [Weekly Vulnerability Analysis](Vulnerabilities/vulnerability-analysis/weekly-vulnerability.md).

### Current Vulnerability Breakdown Reports

You can run the following reports that provide a breakdown of the current vulnerability instances and vulnerable hosts:

* **Current Vulnerable Hosts Breakdown**: Provides a breakdown of current vulnerability instances and vulnerable hosts ranked by count severity with asset-level detail. To learn more about this report, see [Current Vulnerable Hosts Breakdown](Vulnerabilities/current-vulnerable-hosts-breakdown.md).
* **Current Vulnerabilities Breakdown**: Provides a breakdown of current vulnerable hosts and vulnerability instances ranked by count severity with vulnerability detail. To learn more about this report, see [Current Vulnerabilities Breakdown](Vulnerabilities/current-vulnerabilities-breakdown.md).

### Current Vulnerability Finder

You can run the following report that provides lists for specific vulnerabilities and vulnerability instances found within your environment:

* **Current Vulnerability Finder**: Provides insights into current vulnerabilities found in your environment matching specific criteria and the detailed breakdown of vulnerability instances on impacted assets. To learn more about this report, see [Current Vulnerability Finder Report](Vulnerabilities/current-vulnerability-finder.md).

### Vulnerability List

You can run the following report that provides a list of vulnerabilities discovered within your scoped environments:

* **List of Vulnerabilities:** Displays a tabular list of all current vulnerabilities, details about each vulnerability, and information about the assets affected by the vulnerability. To learn more about this report, see [List of Vulnerabilities](Vulnerabilities/vulnerability-analysis/vulnerability-lists.md).

### Current Vulnerability Breakdown

You can run the following report that provides a breakdown for specific vulnerabilities and vulnerability instances found within your environment:

* **Current Vulnerability Breakdown**: Provides a per-deployment breakdown of vulnerabilities, ranked by count and severity, with asset-level detail, and allows you to download data.

## Remediations

The Remediations reports provide convenient access to analysis, statistics, assessments, and trending data related to configuration issues and security exposures from your subscribed products and services. Alert Logic provides Remediations reports within the following categories:

* [Configuration Remediations](#Configur)—Provide valuable summary, distribution, and trending data for your responsiveness of known product configuration and health issues in your environment. You can gain insight into configuration management patterns that improve prioritization and maximize your collection, scanning, detection, or response capabilities.
* [Security Remediations](#Security2)—Provide valuable summary, distribution, and trending data on your responsiveness of security exposures found in your environment. You can gain insight into security exposure management patterns that improve prioritization, and reduce the exposure of your assets to threats.

To access the Remediations reports, in the Alert Logic console, click the **Reports** tab, and then click **Remediations**.

### Configuration Remediations

You can run the following report that provides information on the responsiveness of known product configuration and health issues in your environment:

* **Configuration Remediations Trends**: Evaluates the responsiveness to issues that degrade your service capabilities, including mean time to plan and remediate issues, and categorized remediation age, status, and reason trends. To learn more about this report, see [Configuration Remediation Trends Report](remediations/configuration-remediation-trends.md).

### Security Remediations

You can run the following report that provides information on the responsiveness of security exposures found in your environment.

* **Security Remediations Trends:** Evaluates responses to issues that expose your assets to threats, including mean time to plan and remediate security exposures, and categorized remediation age, status, and reason trends. To learn more about this report, see [Security Remediation Trends](remediations/security-remediation-trends.md).

## Compliance 

The Compliance reports provide convenient access to analysis, statistics, and trending data related to compliance assessment status and audit preparedness from your subscribed products and services. Alert Logic provides Compliance reports within the following categories:

* [Reports Guide](#CISbenchmark)—Provide assessments of how your environment conforms to configuration guidelines developed by security experts.
* [PCI DSS Audit](#PCI%C2%A0DSS)—Provide available documentation and compliance artifacts that help you demonstrate compliance with requirements of the Payment Card Industry Data Security Standard (PCI DSS).
* [HIPAA-HITECH Security Audit](#HIPAASecurityAudit)—Provide documentation to help demonstrate compliance with requirements of the Health Insurance Portability and Accountability Act (HIPAA) and Health Information Technology for Economic and Clinical Health (HITECH) security audit.

To access the Compliance reports, in the Alert Logic console, click the **Reports** tab, and then click **Compliance**.

### CIS Benchmarks 

You can run the following report that provides information on assessments of how your environment conforms to Center for Internet Security (CIS) Foundations Benchmark:

* **CIS **Amazon Web Services (AWS)** Foundation Benchmark**: Provides an assessment of how your environment conforms to configuration guidelines developed by CIS experts.
* **CIS **Microsoft Azure** Foundation Benchmark**: Provides an assessment of how your environment conforms to configuration guidelines developed by CIS experts.

For more information about CIS Benchmarks, see the [CIS Benchmarks FAQ](https://www.cisecurity.org/cis-benchmarks/cis-benchmarks-faq/).

### PCI DSS Audit

You can run the following reports that demonstrate compliance to specific requirements of the Payment Card Industry Data Security Standard (PCI DSS):

* **PCI Requirement 6.6:** Shows Alert Logic Managed Web Application Firewall (WAF) deployments, traffic, incidents, and attacks to help you demonstrate compliance to Requirement 6.6. To learn more about this report, see [PCI Requirement 6.6](compliance/PCI-requirement-6.6.md).
* **PCI Requirement 10.2.2**: Provides guidance for performing log searches that help you demonstrate compliance with Requirement 10.2.2. To learn more about this report, see [PCI Requirement 10.2.2](compliance/PCI-requirement-10.2.2.md).
* **PCI Requirement 10.2.4**: Provides guidance for performing log searches that help you demonstrate compliance with Requirement 10.2.4. To learn more about this report, see [PCI Requirement 10.2.4](compliance/PCI-requirement-10.2.4.md).
* **PCI Requirement 10.2.5**: Provides guidance for performing log searches that help you demonstrate compliance with Requirement 10.2.5. To learn more about this report, see [PCI Requirement 10.2.5](compliance/PCI-requirement-10.2.5.md).
* **PCI Requirement 10.2.6**: Describes, and provides access to, log searches in the Alert Logic console that help demonstrate compliance with Requirement 10.2.6.To learn more about this report, see [PCI Requirement 10.2.6](compliance/PCI-requirement-10.2.6.md).
* **PCI Requirement 10.2.7**: Provides guidance for performing log searches that help you demonstrate compliance with Requirement 10.2.7. To learn more about this report, see [PCI Requirement 10.2.7](compliance/PCI-requirement-10.2.7.md).
* **PCI 10.5.1 Report**: Shows a list of the current log management users,  which helps you demonstrate compliance with Requirement 10.5.1. To learn more about this report, see [PCI Requirement 10.5.1](compliance/PCI-requirement-10.5.1.md).
* **PCI Requirement 10.6.1 Report:** Shows Log Review incidents and Log Management incidents that help you demonstrate compliance with Requirement 10.6.1. To learn more about this report, see [PCI Requirement 10.6.1](compliance/PCI-requirement-10.6.1.md).
* **PCI Requirement 10.7 Report**: Provides guidance for performing log searches that help you demonstrate compliance with Requirement 10.7. To learn more about this report, see [PCI Requirement 10.7](compliance/PCI-requirement-10.7.md).
* **PCI Requirement 10.8 Report**: Provides guidance to demonstrate you have implemented a process for the timely detection and reporting failures of critical security control systems, in compliance with Requirement 10.8. To learn more about this report, see [PCI Requirement 11.2.1](compliance/PCI-requirement-11.2.1.md).
* **PCI Requirement 11.2.1 Report**: Provides guidance to demonstrate  that quarterly internal vulnerability scans, "high-risk" vulnerabilities are rescanned, and performed by qualified personnel, in compliance with Requirement 11.2.1. To learn more about this report, see [PCI Requirement 11.2.1](compliance/PCI-requirement-11.2.1.md).
* **PCI Requirement 11.2.2 Report**: Provides guidance to demonstrate that quarterly external vulnerability scans and rescans are performed, in compliance with Requirement 11.2.2. To learn more about this report, see [PCI Requirement 11.2.2](compliance/PCI-requirement-11.2.2.md).
* **PCI Requirement 11.4**: Shows Network IDS incidents and customer escalation contacts to help you demonstrate compliance to Requirement 11.4 To learn more about this report, see [PCI Requirement 11.4](compliance/PCI-requirement-11.4-new.md).

### HIPAA-HITECH Security Audit

You can run the following reports that demonstrate compliance with specific requirements of the HIPAA security audit:

* **HIPAA 164.308(a)(1)(ii)(B)—Risk Management**: Provides information on security measures that reduce risk and vulnerabilities to a reasonable and appropriate level to help you demonstrate compliance with HIPAA 164.308(a)(1)(ii)(B). To learn more about this report, see [HIPAA 164.308(a)(1)(ii)(B)—Risk Management](compliance/HIPAA-164.308-risk-management.md).
* **HIPAA 164.308(a)(5)(ii)(B)—Protection from Malicious Software**:  Provides  information on guarding against, detecting, and reporting malicious software to help you demonstrate compliance with HIPAA 164.308(a)(5)(ii)(B). To learn more about this report, see [HIPAA 164.308(a)(5)(ii)(B)—Protection from Malicious Software](compliance/HIPAA-164.308-protection-from-malicious-software.md).
* **HIPAA 164.308(a)(1)(ii)(D)—Information System Activity Review**: Shows available documentation and compliance artifacts that help you demonstrate compliance with requirements of 164.308(a)(1)(ii)(D). To learn more about this report, see [HIPAA 164.308(a)(1)(ii)(D)—Information System Activity Review](compliance/HIPAA-164.308-is-activity-review.md).
* **HIPAA 164.308(a)(5)(ii)(C)—Login Monitoring**: Shows available documentation and compliance artifacts that help you demonstrate compliance with requirements of HIPAA 164.308(a)(5)(ii)(C). To learn more about this report, see [HIPAA 164.308(a)(5)(ii)(C)—Login Monitoring](compliance/HIPAA-164.308-login-monitoring.md).
* **HIPAA 164.308(a)(6)(ii)—Response and Reporting**: Shows available documentation and compliance artifacts that help you demonstrate compliance with requirements of HIPAA 164.308(a)(6)(ii). To learn more about this report, see [HIPAA 164.308(a)(6)(ii)—Response and Reporting](compliance/HIPAA-164.308-response-reporting.md).
* **HIPAA 164.312(b)—Audit Controls**: Provides information on the implemented software or procedural mechanisms that record and examine activity in information systems to help you demonstrate compliance with HIPAA 164.312(b). To learn more about this report, see [HIPAA 164.312(b)—Audit Controls](compliance/HIPAA-164.312-audit-controls.md).

## Service

The Service reports provide convenient access to data related to entitlements, capability usage, users and security content for your subscribed products and services. Alert Logic provides Service reports within the following categories:

* [Entitlement](#Entitlem)—Provide daily summaries, and valuable insights and trending data for entitlement and usage.
* [Capability Usage](#Capabili)—Provide valuable summary and trending data on your actual use of deployed security product and service capabilities.
* [Health ](#Health)—Provide valuable summary and trending data on the health status of protected networks and assets collecting log or network data.
* [Users](#Users)—Provide valuable insight into key customer contacts and user accounts provisioned in the Alert Logic console for your subscribed services.
* [Cloud Insight](#Cloud)—Provide information regarding the billable size of your scoped deployments, which correlate to the amount billed for a given usage period.

To access the Service reports, in the Alert Logic console, click the **Reports** tab, and then click **Service**.

### Entitlement

You can run the following reports that provide information on your entitlement, and insights on your usage:

* **Entitlement Summary**: Provides a daily summary of your entitlement and usage, including count and percentage of node used, node remaining and list of protected node counts.To learn more about this report, see [Entitlement Summary](service/entitlement/entitlement-summary.md).
* **Entitlement Usage Trends**: Provides a summary of your entitlement usage, including nodes used trends and entitlement change trends. To learn more about this report, see [Entitlement Usage Trends](service/entitlement/entitlement-usage-trends.md).

### Capability Usage

You can run the following reports that provide information on your actual use of deployed security product and service capabilities:

* **Monthly Service Review:** Provide summary information and visibility into product configuration, product status, and security outcomes from your subscribed services.
* **Log Collection**: Provides visibility into log collection volume and log messages processed in your environment, including log collection  per day measured by GB, EPS or log messages, and a collector list with volumes and total messages. To learn more about this report, see [Log Collection](service/capability-usage/log-collection.md).
* **Log Collection**: Provides visibility into log collection volume and log messages processed in your environment, including log collection per day and a list of collectors with volume by GB, EPS or log messages. To learn more about this report, see [Log Collection](service/capability-usage/log-collection.md).
* **Top 10 Log Collectors**: Provides visibility into the log collector volume with top ten collector lists measured by GB, EPS or log messages. To learn more about this report, see [Top 10 Log Collectors](service/capability-usage/top-ten-log-collectors.md).
* Network IDS** Traffic**: Provides visibility into Network IDS traffic volume and collections processed in your environment, including Network IDS traffic per day, a list of collectors with traffic packets and megabytes, and a top ten collector list. To learn more about this report, see [IDS Traffic](service/capability-usage/network-ids-traffic.md).
* **IDS Traffic**: Provides visibility into IDS traffic volume in your environment, including affected assets and IDS traffic per day listed by packets or megabytes. To learn more about this report, see [IDS Traffic](service/capability-usage/network-ids-traffic.md).
* **Top 10 IDS Assets**: Provides lists of the top 10 assets in your environment, measured by packets and megabytes. To learn more about this report, see [Top 10 IDS Assets](service/capability-usage/top-10-ids-assets.md).
* **WAF Traffic:** Provides visibility into WAF traffic volume and requests processed in your environment, including WAF traffic per day measured by requests or megabytes, and an appliance list with traffic requests and megabytes. To learn more about this report, see [ WAF Traffic](service/capability-usage/waf-traffic.md).
        
### Health 

You can run the following reports that provide insights into the statuses of networks, agents, and appliances, and specific remediations to improve the level of protection in your environment:

* **Network Health Status Digest:** Provides insight into the daily issues related to protected networks in your environment, including a comparison of health statuses, top ten lists, and total number of open remediations for each network. To learn more about this report, see [Network Health Status Digest](service/health/network-health-digest.md).
* **Collection Issues Digest:** Provides insight into the daily issues related to log data collection and Network IDS traffic, including a comparison of health statuses, top five lists, and a list of open remediations to fix configuration issues. To learn more about this report, see [Collection Issues Digest](service/health/collection-issues-digest.md).
* **Missing Agent Digest**: Provides insight into the daily issues related to hosts that are missing agents, including a comparison of missing agent statuses, top ten lists, and a list of hosts with missing agents. To learn more about this report, see [Missing Agent Digest](service/health/missing-agent-digest.md).

### Users

You can run the following reports that provides key customer contacts and user accounts:

* **Current Users:** Provides a visual overview of the users in your customer account by active or inactive status, user role, or multi-factor authentication settings. The report also provides a list of account details for each user. To learn more about this report, see [Current Users](service/users/current-users.md).
* **Customer Contacts:** Provides tabular lists of your escalation, notification and incidents notification contacts.
* **Escalation Contacts**: Provides a list of your escalation contacts. These are the primary and secondary contacts designated to receive notification from Alert Logic staff for high-priority security or service incidents.
* **Notification Contacts**: Provides a list of your notification contacts. These are contacts set up to receive automated email notifications from the [Notifications](../../configure/notifications.md)page.
* **Incident Notification Contacts**:  Provides a list of your incident notification contacts. These are contacts set up to receive automated email notifications from the [Incidents](../incidents.md) page.
* **User Login Trends:** Provides a visual overview and a detailed list of the users who log into the Alert Logic console, how often and when. To learn more about this report, see [User Login Trends](service/users/login-trends.md).

### Cloud Insight

You can run the following reports that provide information regarding the billable size of your scoped deployments:

* **Deployments Usage by Day:** Displays the number of deployments in your account, by day, for the specified date range.
* **Host Usage by Day:** Displays billable product usage over time, by deployment, and with the option to filter to a specific time period. The report presents results by day, and as a sum over the selected time period.
* **Host Usage by Hour:** Displays billable product usage over time, by deployment, and with the option to filter to a specific time period. The report presents results by day and by hour over the selected time period.
