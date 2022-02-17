# Risk Reports

The **REPORTS** page in the Alert Logic console provides access to data related to exposures and incidents Alert Logic found within your deployments. You can also view data related to your product usage within your accounts. For information on all the available report groups, see [Reports Guide](../reports.md).

The Risk reports group provide convenient access to analysis, statistics, assessments, and trending data related to your security and health posture and threat risk index.

Alert Logic provides Risk reports within the following categories:

* [Security Posture ](#Security)—Provide comparative trending analysis to help you improve your overall security posture, reduce threat risk index scores, and optimize the security product and service capabilities deployed in your environment.
* [Threat Risk Index ](#Threat-Risk)—Provide valuable summary and trending data for the threat risk index scores for the deployments and networks in your environment. You can gain insight into emerging threats and learn which assets in your environment are most at risk.
* [Enterprise Risk](#Enterpri)—Provides valuable insights and analysis of your incidents, events, and vulnerabilities. You can evaluate threats and incidents and your response efforts, validate events and focus your efforts, and gain insights into the effectiveness of your vulnerability management.

To access the Risk reports, in the Alert Logic console,  click the menu icon (![](../../../Resources/Images/dashboard/menu-icon.png)), and then click ![](../../../Resources/Images/dashboard/validate-icon.png)**Validate**. Click **Reports**, and then click **Risk**.

Each report allows you to share its data by email, or download the report as an image, data, crosstab, PDF, or PowerPoint files. To learn how to download reports, see [Report Download Option](../download-option.md).

You can also schedule a report to run periodically and subscribe users or an integration (such as a webhook) to receive a notification when the report is generated.   From the Downloads tab on the Reports page, you can download and manage reports generated from your schedules. For more information, see [Scheduled Reports and Notifications](../../../configure/notifications/report.md).

## Filtering reports

You can  filter your reports quickly to refine your results and generate relevant information you need. Each report has a set of filters located at the top that you can select or clear for the filters you want to see. Alert Logic also allows you to add or remove some or all values in a filter you want to see.

### Filter the report using drop-down menus

By default, Alert Logic includes **(All)** filter values in the report.

**To add or remove filter values: **

1. Click the drop-down menu in the filter, and then select or clear values.
2. Click **Apply**.

## Security Posture 

You can run the following reports that information your overall security posture:

* **Monthly Security Posture: **Provides the current and historic security risk and health posture of your environment, including configuration remediations and risk posture overviews, vulnerabilities assessment, and threat analysis. To learn more about this report, see [Monthly Security Posture Report](monthly-security-posture.md).

## Threat Risk Index 

You can run the following reports that provide valuable summary and trending data for the threat risk index scores:

* **TRI Summary:** Provides the current threat risk index (TRI) scores of your environment, including the overall TRI score and trends, score details, risk index asset distribution charts, and top ten lists. To learn more about this report, see [TRI Summary](tri-summary.md).
* **TRI Summary:** Provides the current threat risk index (TRI) scores of your environment, including the overall TRI score and trends, score details, and risk index asset distribution charts. To learn more about this report, see [TRI Summary](tri-summary.md).
* **Top 10 TRI Lists**: Provides  top 10 lists of your most vulnerable hosts by TRI score, and the top 10 vulnerabilities by TRI score. To learn more about this report, see [Top 10 TRI Lists](top-ten-TRI-list.md).
* **TRI Trends:** Provides insights into threat risk index (TRI) averages and trends in reducing risks, including TRI scores, total vulnerability and host counts, internet-facing vulnerabilities, exploit availability, and last scanned age. To learn more about this report, see [TRI Trends Report](tri-trends.md).

## Enterprise Risk

You can run the following reports that provide insights into your incidents, events, vulnerabilities:

* **Monthly Enterprise**: Provides valuable monthly insights and analysis of your incidents, events, and vulnerabilities in your environment.To learn more about this report, see [Monthly Enterprise Risk](enterprise-risk/monthly-enterprise.md).
* **Weekly Enterprise**: Provides valuable monthly insights and analysis of your incidents, events, and vulnerabilities in your environment.To learn more about this report, see [Weekly Enterprise Risk](enterprise-risk/weekly-enterprise.md).
