# Vulnerabilities Reports

The **REPORTS** tab in the Alert Logic console provides access to data related to exposures and incidents Alert Logic found within your deployments. You can also view data related to your product usage within your accounts. For information on all the available report groups, see [Reports Guide](../reports.md).

The Vulnerability Reports provide convenient access to analysis, statistics, assessments, and trending data related to vulnerabilities discovered in your environment based on scanning outcomes. Alert Logic provides Vulnerabilities reports within the following categories:

* [Scan Schedule Breakdown](#ScanScheduleBreakdown)—Provide summary, detailed, and variance vulnerability results for  specific scan schedules.
* [Vulnerability Analysis](#vulnerabilityAnalysis)—Provide valuable summary, distribution and trending data for vulnerabilities discovered across your environment. You can gain insight into the effectiveness of your vulnerability management and prioritization efforts.
* [            Vulnerability Analysis - Full Reports](#full-report)—Provides valuable monthly and weekly summary insights into vulnerabilities and vulnerable assets found in your environment. You can gain insights into the effectiveness of your vulnerability management, help prioritize your efforts, and focus on specific areas.
* [Current Vulnerability Breakdown Reports](#Current)—Provide a breakdown of current vulnerability instances and vulnerable hosts ranked by count and severity with asset-level or vulnerability details. You can gain insights into the effectiveness of your vulnerability management, help prioritize your efforts, and focus on specific areas in your environment.
* [Vulnerability Variance Reports](#Vulnerab2)—Provide a valuable summary on vulnerability instances, trending and detailed lists for new, resolved, and unresolved vulnerabilities in your environment. You can gain insights into the effectiveness of your vulnerability management and remediation efforts.
* [Current Vulnerability Finder](#Current2)—Provide valuable summary data and tabular lists for specific vulnerabilities and vulnerability instances found within your environment. You can export these reports and use them for further analysis.
* [Vulnerability List](#Vulnerab)—Provides a tabular list of vulnerabilities discovered within your scoped environments. You can export these reports and use them for further analysis.
* [Current Vulnerability Breakdown](#Current3)—Provide a per deployment breakdown of vulnerabilities, ranked by count and severity, with asset level detail.

To access the Vulnerability reports, in the Alert Logic console,  click the menu icon (![](../../../Resources/Images/dashboard/menu-icon.png)), and then click ![](../../../Resources/Images/dashboard/validate-icon.png)**Validate**. Click **Reports**, and then click **Vulnerabilities**.

Each report allows you to share its data by email, or download the report as an image, data, crosstab, PDF, or PowerPoint files. To learn how to download reports, see [Report Download Option](../download-option.md).

You can also schedule a report to run periodically and subscribe users or an integration (such as a webhook) to receive a notification when the report is generated.   From the Downloads tab on the Reports page, you can download and manage reports generated from your schedules. For more information, see [Scheduled Reports and Notifications](../../../configure/notifications/report.md).

## Filtering reports

You can  filter your reports quickly to refine your results and generate relevant information you need. Each report has a set of filters located at the top that you can select or clear for the filters you want to see. Alert Logic also allows you to add or remove some or all values in a filter you want to see.

### Filter the report using drop-down menus

By default, Alert Logic includes **(All)** filter values in the report.

**To add or remove filter values: **

1. Click the drop-down menu in the filter, and then select or clear values.
2. Click **Apply**.

## Scan Schedule Breakdown

You can run the following reports that provide summary, detailed, and variance vulnerability results for  specific scan schedules:

* **Scan Host Summary**: Provides a breakdown of vulnerable hosts and vulnerability instances found by the selected scan with asset-level detail. To learn more about this report, see [Scan Host Summary](scan-schedule-breakdown/scan-host-summary.md).
* **Scan Details List**: Provides a detailed list of each vulnerability found by the selected scan with  information on  vulnerability name, CVSS score, severity, affected assets, host name, IP address, protocol, port, first seen, and last scanned. To learn more about this report, see [Scan Details List](scan-schedule-breakdown/scan-details-list.md).
* **Scan Variance**: Provides a comparison of new, resolved, and unresolved vulnerability instances  found by the selected scan. To learn more about this report, see [Scan Variance](scan-schedule-breakdown/scan-variance.md).

## Vulnerability Analysis

You can run the following reports that provide information for vulnerabilities discovered across your environment.

* **Monthly Vulnerability Summary:** Provides a summary of the month to month vulnerabilities found in your environment, including vulnerability and host counts, severity and age distribution, exportable vulnerability list, and categorized trends. To learn more about this report, see [Monthly Vulnerability Summary](vulnerability-analysis/vulnerability-summary.md).
* **Weekly Vulnerability Summary:** Provides a summary of the week to week vulnerabilities found in your environment, including vulnerability and host counts, severity and age distribution, exportable vulnerability list, and categorized trends. To learn more about this report, see [Weekly Vulnerability Summary](vulnerability-analysis/weekly-vulnerability-summary.md).
* **Monthly Top 10 Vulnerability Lists:** Provides top 10 lists for your most vulnerable hosts by total count and by severity, oldest critical vulnerabilities, and frequent vulnerabilities. To learn more about this report, see [Monthly Top 10 Vulnerability Lists](vulnerability-analysis/vulnerability-top-ten.md).
* **Weekly Top 10 Vulnerability Lists:** Provides top 10 lists for your most vulnerable hosts by total count and by severity, oldest critical vulnerabilities, and frequent vulnerabilities. To learn more about this report, see [Weekly Top 10 Vulnerability Lists](vulnerability-analysis/weekly-vulnerability-top-ten.md).
* **Monthly Vulnerability Host Explorer:** Provides a summary of the most vulnerable assets, including total host and vulnerability counts, hosts by CVSS severity ratings, and top ten lists. To learn more about this report, see [Monthly Vulnerable Hosts Explorer](vulnerability-analysis/vulnerability-host-explorer.md).
* ** Monthly Vulnerable Hosts Change Trends:** Contains sections that show the percentage or count, and trend of vulnerable host changes over the selected time period. To learn more about this report, see [Monthly Vulnerable Hosts Change Trends](vulnerability-analysis/vulnerable-hosts-trends.md).
* **Monthly Vulnerable Distribution Explorer:** Provides insights into patterns in your vulnerabilities, including vulnerability distribution and trends categorized by status, exploitability, severity, age, operating system, and asset type. To learn more about this report, see [Monthly Vulnerability Distribution Explorer](vulnerability-analysis/vulnerability-distribution-explorer.md).
* **Weekly Vulnerable Distribution Explorer:** Provides insights into patterns in your vulnerabilities, including vulnerability distribution and trends categorized by status, exploitability, severity, age, operating system, and asset type. To learn more about this report, see [Weekly Vulnerability Distribution Explorer](vulnerability-analysis/weekly-vulnerability-distribution-explorer.md).
* **Monthly Vulnerability Change Trends:** Provides  a summary of the percentage and count changes of vulnerabilities, and trend  by total and severity. To learn more about this report, see [Monthly Vulnerability Change Trends](vulnerability-analysis/vulnerability-change-trends.md).

##             Vulnerability Analysis - Full Reports

You can run the following reports that provide summary information for vulnerabilities discovered across your environment:

* **Monthly Vulnerability Analysis**: Provides insights into vulnerabilities and vulnerable assets found in your environment, including vulnerabilities by severity and age, vulnerability trends, vulnerabilities by day and severity, and top vulnerable hosts, networks, and deployment lists for the selected month. To learn more about this report, see [Monthly Vulnerability Analysis ](vulnerability-analysis/monthly-vulnerability.md).
* **Weekly Vulnerability Analysis**: Provides insights into vulnerabilities and vulnerable assets found in your environment, including vulnerabilities by severity and age, vulnerability trends, vulnerabilities by day and severity, and top vulnerable hosts, networks, and deployment lists for the selected week. To learn more about this report, see [Weekly Vulnerability Analysis](vulnerability-analysis/weekly-vulnerability.md).

## Current Vulnerability Breakdown Reports

You can run the following reports that provide a breakdown of the current vulnerability instances and vulnerable hosts:

* **Current Vulnerable Hosts Breakdown**: Provides a breakdown of current vulnerability instances and vulnerable hosts ranked by count severity with asset-level detail. To learn more about this report, see [Current Vulnerable Hosts Breakdown](current-vulnerable-hosts-breakdown.md).
* **Current Vulnerabilities Breakdown**: Provides a breakdown of current vulnerable hosts and vulnerability instances ranked by count severity with vulnerability detail. To learn more about this report, see [Current Vulnerabilities Breakdown](current-vulnerabilities-breakdown.md).
* **Last Scanned Breakdown**:  Provides visibility into when your assets were last scanned for vulnerabilities. To learn more about this report, see [Last Scanned Breakdown](last-scanned-breakdown.md).

## Vulnerability Variance Reports

You can run the following reports that provide a summary, trending and detailed lists for new, resolved and unresolved vulnerabilities in your environment:

* **Daily Vulnerability Variance**: Provides a comparison of total unresolved, new, and resolved vulnerability instances in your environment from the previous day. To learn more about this report, see [Daily Vulnerability Variance](daily-vulnerability-variance.md).
* **Weekly Vulnerability Variance**: Provides a comparison of total unresolved, new, and resolved vulnerability instances in your environment from the previous week. To learn more about this report, see [Weekly Vulnerability Variance](weekly-vulnerability-variance.md).
* **Monthly Vulnerability Variance**: Provides a comparison of total unresolved, new, and resolved vulnerability instances in your environment from the previous month. To learn more about this report, see [Monthly Vulnerability Variance](monthly-vulnerability-variance.md).

## Current Vulnerability Finder

You can run the following report that provides lists for specific vulnerabilities and vulnerability instances found within your environment:

* **Current Vulnerability Finder**: Provides insights into current vulnerabilities found in your environment matching specific criteria and the detailed breakdown of vulnerability instances on impacted assets. To learn more about this report, see [Current Vulnerability Finder Report](current-vulnerability-finder.md).

## Vulnerability List

You can run the following report that provides a list of vulnerabilities discovered within your scoped environments:

* **List of Vulnerabilities:** Displays a tabular list of all current vulnerabilities, details about each vulnerability, and information about the assets affected by the vulnerability. To learn more about this report, see [List of Vulnerabilities](vulnerability-analysis/vulnerability-lists.md).

## Current Vulnerability Breakdown

You can run the following report that provides a breakdown for specific vulnerabilities and vulnerability instances found within your environment:

* **Current Vulnerability Breakdown**: Provides a per-deployment breakdown of vulnerabilities, ranked by count and severity, with asset-level detail, and allows you to download data.
