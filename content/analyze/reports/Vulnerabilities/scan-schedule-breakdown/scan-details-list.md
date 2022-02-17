# Scan Details List

The Scan Details List report provides a detailed list of each vulnerability found by the selected scan with  information on  vulnerability name, CVSS score, severity, affected assets, host name, IP address, protocol, port, first seen, and last scanned. Use this report to investigate vulnerabilities detected in specific scans.

To access the Scan Details List report:

1. In the Alert Logic console, click the menu icon (![](../../../../Resources/Images/dashboard/menu-icon.png)), and then click ![](../../../../Resources/Images/dashboard/validate-icon.png)**Validate**.
2. Click **Reports**, and then click **Vulnerabilities**.
3. Under **Scan Schedule Breakdown**, click **VIEW**.
4. Click **Scan Details List**.

## View  the report

To view the report, you must select a single value for  **Customer Account**, **Deployment Name**, **Scan Schedule Name**, and **Scan Start Date**.

    The **Start Scan Time** for a specific scan will not appear until the data refresh following the final scan window defined in the schedule. To validate the most recent data refresh, see the **Last Updated Time** in the top right of the report window.    ## Filter the report

To refine your findings, filter your report by  **Severity**.

### Filter the report using drop-down menus

By default, Alert Logic includes **(All)** filter values in the report.

**To add or remove filter values: **

1. Click the drop-down menu in the filter, and then select or clear values.
2. Click **Apply**.

## Download the report

You can  download the Scan Details List report  as an image, data (CSV), crosstab, PDF, or PowerPoint file. To learn how to download reports, see [Report Download Option](../../download-option.md).

## CVSS scores and severity

Alert Logic assigns each vulnerability one of the following severities with corresponding icon based on the CVSS v2 score set by the National Institute of Standards and Technology, and reported to the National Vulnerability Database:

| Severity | CVSS base score |
|---|---|
| ![](../../../../Resources/Images/Icons/threat_critical_icon.png) High | 7.0 - 10.0 |
| ![](../../../../Resources/Images/Icons/threat_high_icon.png)Medium | 4.0 - 6.9 |
| ![](../../../../Resources/Images/Icons/threat_medium_icon.png)Low | 0.1 - 3.9 |
| ![](../../../../Resources/Images/Icons/threat_info_icon.png)Informational | 0.0 |

## Scan details list

The list provides details of the vulnerability instances found by the selected scan. The list is organized by  vulnerability name, CVSS score, severity,  affected assets, host name, IP address, protocol, port, first seen, and last scanned.

![](../../../../Resources/Images/Reports/scan-schedule-breakdown/scan-details-report.png)
