# Service Reports

The **REPORTS** page in the Alert Logic console provides access to data related to exposures and incidents Alert Logic found within your deployments. You can also view data related to your product usage within your accounts. For information on all the available report groups, see [Reports Guide](../reports.md).

The Service reports provide convenient access to data related to entitlements, capability usage, users and security content for your subscribed products and services. Alert Logic provides Service reports within the following categories:

* [Entitlement](#Entitlement)—Provide daily summaries, and valuable insights and trending data for entitlement and usage.
* [Capability Usage](#Capability)—Provide valuable summary and trending data on your actual use of deployed security product and service capabilities.
* [Health ](#Health)—Provide valuable summary and trending data on the health status of protected networks and assets collecting log or network data.
* [Users](#Users)—Provide valuable insight into key customer contacts and user accounts provisioned in the Alert Logic console for your subscribed services.
* [Cloud Insight](#Cloud)—Provide information regarding the billable size of your scoped deployments, which correlate to the amount billed for a given usage period.

To access the Service reports, in the Alert Logic console,  click the menu icon (![](../../../Resources/Images/dashboard/menu-icon.png)), and then click ![](../../../Resources/Images/dashboard/validate-icon.png)**Validate**. Click **Reports**, and then click **Service**.

Each report allows you to share its data by email, or download the report as an image, data, crosstab, PDF, or PowerPoint files. To learn how to download reports, see [Report Download Option](../download-option.md).

You can also schedule a report to run periodically and subscribe users or an integration (such as a webhook) to receive a notification when the report is generated.   From the Downloads tab on the Reports page, you can download and manage reports generated from your schedules. For more information, see [Scheduled Reports and Notifications](../../../configure/notifications/report.md).

## Filtering reports

You can  filter your reports quickly to refine your results and generate relevant information you need. Each report has a set of filters located at the top that you can select or clear for the filters you want to see. Alert Logic also allows you to add or remove some or all values in a filter you want to see.

### Filter the report using drop-down menus

By default, Alert Logic includes **(All)** filter values in the report.

**To add or remove filter values: **

1. Click the drop-down menu in the filter, and then select or clear values.
2. Click **Apply**.

## Entitlement

You can run the following reports that provide information on your entitlement, and insights on your usage:

* **Entitlement Summary**: Provides a daily summary of your entitlement and usage, including count and percentage of node used, node remaining and list of protected node counts.To learn more about this report, see [Entitlement Summary](entitlement/entitlement-summary.md).
* **Entitlement Usage Trends**: Provides a summary of your entitlement usage, including nodes used trends and entitlement change trends. To learn more about this report, see [Entitlement Usage Trends](entitlement/entitlement-usage-trends.md).

## Capability Usage

You can run the following reports that provide information on your actual use of deployed security product and service capabilities:

* **Monthly Service Review:** Provide summary information and visibility into product configuration, product status, and security outcomes from your subscribed services.
* **Log Collection**: Provides visibility into log collection volume and log messages processed in your environment, including log collection  per day measured by GB, EPS or log messages, and a collector list with volumes and total messages. To learn more about this report, see [Log Collection](capability-usage/log-collection.md).
* **Log Collection**: Provides visibility into log collection volume and log messages processed in your environment, including log collection per day and a list of collectors with volume by GB, EPS or log messages. To learn more about this report, see [Log Collection](capability-usage/log-collection.md).
* **Top 10 Log Collectors**: Provides visibility into the log collector volume with top ten collector lists measured by GB, EPS or log messages. To learn more about this report, see [Top 10 Log Collectors](capability-usage/top-ten-log-collectors.md).
* Network IDS** Traffic**: Provides visibility into Network IDS traffic volume and collections processed in your environment, including Network IDS traffic per day, a list of collectors with traffic packets and megabytes, and a top ten collector list. To learn more about this report, see [IDS Traffic](capability-usage/network-ids-traffic.md).
* **IDS Traffic**: Provides visibility into IDS traffic volume in your environment, including affected assets and IDS traffic per day listed by packets or megabytes. To learn more about this report, see [IDS Traffic](capability-usage/network-ids-traffic.md).
* **Top 10 IDS Assets**: Provides lists of the top 10 assets in your environment, measured by packets and megabytes. To learn more about this report, see [Top 10 IDS Assets](capability-usage/top-10-ids-assets.md).
* **WAF Traffic:**Provides visibility into WAF traffic volume and requests processed in your environment, including WAF traffic per day measured by requests or megabytes, and an appliance list with traffic requests and megabytes. To learn more about this report, see [ WAF Traffic](capability-usage/waf-traffic.md).
        
## Health 

You can run the following reports that provide insights into the statuses of networks, agents, and appliances, and specific remediations to improve the level of protection in your environment:

* **Network Health Status Digest:** Provides insight into the daily issues related to protected networks in your environment, including a comparison of health statuses, top ten lists, and total number of open remediations for each network. To learn more about this report, see [Network Health Status Digest](health/network-health-digest.md).
* **Collection Issues Digest:** Provides insight into the daily issues related to log data collection and Network IDS traffic, including a comparison of health statuses, top five lists, and a list of open remediations to fix configuration issues. To learn more about this report, see [Collection Issues Digest](health/collection-issues-digest.md).
* **Missing Agent Digest**: Provides insight into the daily issues related to hosts that are missing agents, including a comparison of missing agent statuses, top ten lists, and a list of hosts with missing agents. To learn more about this report, see [Missing Agent Digest](health/missing-agent-digest.md).
* **Daily Health Summary**: Provides insight into the daily issues in your environment related to your protected network health status, data collection and network IDS traffic, and hosts missing agents. To learn more about this report, see [Daily Health Summary](health/daily-health-summary.md).
* **SSL Certification Expiration Status**: Provides insights into the statuses of SSL keys and certificates that are used on Alert Logic appliances to decrypt network traffic. To learn more about this report, see [SSL Certification Expiration Status](health/current-ssl-certificates-status.md).

## Users

You can run the following reports that provides key customer contacts and user accounts:

* **Current Users:** Provides a visual overview of the users in your customer account by active or inactive status, user role, or multi-factor authentication settings. The report also provides a list of account details for each user. To learn more about this report, see [Current Users](users/current-users.md).
* **Customer Contacts:** Provides tabular lists of your escalation, notification and incidents notification contacts.
* **Escalation Contacts**: Provides a list of your escalation contacts. These are the primary and secondary contacts designated to receive notification from Alert Logic staff for high-priority security or service incidents.
* **Notification Contacts**: Provides a list of your notification contacts. These are contacts set up to receive automated email notifications from the [Notifications](../../../configure/notifications.md) page.
* **Subscribed Notification Users**: Provides a list of users subscribed to receive notifications for specified customer accounts from the [Notifications](../../../configure/notifications.md) page. To learn more about this report, see [Subscribed Notification Users](users/subscribed-notification-users.md).
* **Incident Notification Contacts**:  Provides a list of your incident notification contacts. These are contacts set up to receive automated email notifications from the [Incidents](../../incidents.md) page.
* **User Login Trends:** Provides a visual overview and a detailed list of the users who log into the Alert Logic console, how often and when. To learn more about this report, see [User Login Trends](users/login-trends.md).

## Cloud Insight

You can run the following reports that provide information regarding the billable size of your scoped deployments:

* **Deployments Usage by Day:** Displays the number of deployments in your account, by day, for the specified date range.
* **Host Usage by Day:** Displays billable product usage over time, by deployment, and with the option to filter to a specific time period. The report presents results by day, and as a sum over the selected time period.
* **Host Usage by Hour:** Displays billable product usage over time, by deployment, and with the option to filter to a specific time period. The report presents results by day and by hour over the selected time period.
