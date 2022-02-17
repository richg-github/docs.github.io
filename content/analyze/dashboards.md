# Dashboards

Dashboards is a new feature that introduces interactive, visual dashboards that summarize data, product capabilities, and the state of your environment. These dashboards are being released together with an easy way to  navigate through the Alert Logic console.

Dashboards allows you to easily view pertinent information  in  visuals that feed from live data in your environment. Most visuals allow you to click items to view the source of the data  in the visual. This allows you to drill down further into issues immediately  on the corresponding page in the Alert Logic console, and streamline your response actions.

    Alert Logic offers partners and customers with managed accounts two additional dashboards. For more information, see the following: * [Managed Accounts Health Summary Dashboard](dashboard/managed-accounts/managed-accounts-health-summary.md)
* [Managed Accounts Security Summary Dashboard](dashboard/managed-accounts/managed-accounts-security-summary.md)

## Navigate to other pages from Dashboards

The new navigation menu makes it easy to navigate through the Alert Logic console from the Dashboards page.

**To start navigating to other pages**:

1. Click the menu icon (![](../Resources/Images/dashboard/menu-icon.png)) to see the navigation menu.
2. Click on a navigation group (for example, **Respond**) to expand the options under that group.
3. Click on a navigation item (for example, **Incidents**) that you want to explore further.

Although all of the functionality of the current Alert Logic console is available, there are some differences in the Dashboard navigation menu and the current Alert Logic console. For more detailed information, see [Managed Detection and Response Navigation Menu Updates](dashboard/navigation.md#Navigation).

## About the dashboards

Alert Logic curated different dashboards, which are composed of visuals to present how you interact with data and capabilities in your environment, and quickly track existing issues.   The default dashboard view is Threat Summary. You can use the drop-down menu on the top left to view the other available dashboards. The following are some available dashboards:

* Threat Summary
* Vulnerability Summary
* TRI Summary
* Coverage and Health
* Endpoint Protection
* File Integrity Monitoring
* Web Log Analytics (WLA)
* Firewall Log Volume Analysis
* Firewall Log Security Analysis
* Authentication Management Summary
* Authentication Management Security

### Threat Summary dashboard

The Threat Summary dashboard provides visibility into threats and incidents in your environment, including open incidents, incident threat levels and trend, classes of, countries where incidents originate, most attacked deployments and hosts, top attackers, and a peer incident classification comparison chart. Use this dashboard to gain insights into the types of incidents that were detected in your environment,  analyze the effectiveness of your current incident response efforts, and learn about emerging threats. To learn more about this dashboard, see [Threat Summary Dashboard](dashboard/threat-summary.md).

### Vulnerability Summary dashboard

The Vulnerability Summary dashboard provides visibility into vulnerable software and cloud infrastructure in your environment, including lists of most seen vulnerabilities, most vulnerable hosts, top security remediations, and vulnerability counts, vulnerabilities by deployments, and a vulnerability trend. Use this dashboard to gain insights into the effectiveness of your current vulnerability management efforts, learn about new vulnerabilities and emerging threats, help prioritize your remediation plans, and focus on specific areas in your environment. To learn more about this dashboard, see [Vulnerability Summary Dashboard](dashboard/vulnerability-summary.md).

### Threat Risk Index (TRI) dashboard

The Threat Risk Index (TRI) Summary dashboard provides insights into the recent TRI scores of your environment, including the average TRI score and trends, vulnerabilities changes, last scanned asset changes, and TRI scores by assets. For more about how Alert Logic calculates TRI scores, see [Threat Risk Index Score Factors](TRI-score-factors.md). Use this dashboard to help you determine which of your deployments, VPCs, or networks are most exposed and susceptible to a security attack or breach. To learn more about this dashboard, see [Threat Risk Index Summary](dashboard/tri-summary.md).

### Coverage and Health dashboard

The Coverage and Health dashboard provides insight into your entitlement usage and statuses in your environment, including an unprotected node count, a summary of your entitlement,  node count and percentage usage, network and collection statuses, and open configuration exposures. Use this dashboard to improve network protection, fix configuration issues, and support optimization efforts in your environment. To learn more about this dashboard, see [Coverage and Health Dashboard](dashboard/coverage-health.md).

### Endpoint Protection dashboard

The Endpoint Protection dashboard provides a summary of your endpoint activity, including protection statuses, version updates, last check-ins, and platforms, count of malware attacks detected, list of most attacked users and endpoints, top attack types, and blocked attacks and responses to attacks. Use this dashboard to gain insights into your endpoint activity, learn about attack patterns, and analyze the effectiveness of your current threat and incident management process. To learn more about this dashboard, see [Endpoint Protection Dashboard](dashboard/endpoint-protection.md).

The Endpoint Protection dashboard feeds from data in your Extended Endpoint Protection product. You must have an endpoint agent installed to a workstation or server to get value from this dashboard. To learn more about configuring Extended Endpoint Protection, see [Get Started with Alert Logic Extended Endpoint Protection](../get-started/endpoint-protection.md).

### File Integrity Monitoring dashboard

The File Integrity Monitoring dashboard provides a summary of your file monitoring activity and issues found in your environment. Use this dashboard to gain insights into your file monitoring scope and status, focus your resources on specific systems or users that may need further investigation, and identify patterns or anomalies in your environment. To learn more about this dashboard, see [File Integrity Monitoring Dashboard ](dashboard/file-integrity-monitoring.md).

### Web Log Analytics dashboard

The Web Log Analytics (WLA) dashboard provides visibility into threats, incidents, and observations detected from your WLA instance in your environment. Use this dashboard to gain insights into the types of incidents detected in your environment,  analyze the effectiveness of your current incident response efforts, and learn about emerging threats. To learn more about this dashboard, see [Web Log Analytics Dashboard](dashboard/web-log-analytics.md).

### Firewall Log Traffic dashboard

The Firewall Log Traffic Analysis dashboard provides insights into the firewall traffic  connections found from analyzing firewall logs in  your environment. Use this dashboard to identify the types of connections that were detected,  trends that require  further investigations, and learn about emerging threats. To learn more about this dashboard, see [Firewall Log Traffic Analysis Dashboard](dashboard/firewall-log-traffic-analysis-dashboard.md).

### Firewall Log Volume dashboard

The Firewall Log Volume Analysis dashboard provides insights into the volume of firewall log messages, firewall security incidents and observations in your environment. Use this dashboard to quickly identify  patterns, trends and anomalies that require immediate response or further investigations. To learn more about this dashboard, see [Firewall Log Volume Analysis Dashboard](dashboard/firewall-log-volume-dashboard.md).

### Firewall Log Security Analysis dashboard 

The Firewall Log Security Analysis dashboard provides insights into the firewall security incidents generated from analyzing firewall logs in  your environment. Use this dashboard to quickly identify the types of firewall incidents that were detected,  analyze the effectiveness of your current firewall incident response efforts, and learn about emerging threats. To learn more about this dashboard, see [Firewall Log Security Analysis Dashboard](dashboard/firewall-log-security-dashboard.md).

### Authentication Management Summary dashboard

The Authentication Management Summary dashboard provides a summary of your authentication management application security incidents in your environment. Use this dashboard to gain insights into your management efforts of your authentication security incidents, and focus your resources on threats and anomalies in user login trends and activities in your environment. To learn more about this dashboard, see [Authentication Management Summary](dashboard/authentication-management-summary.md).

### Authentication Management Security dashboard

The Authentication Management Security dashboard provides a summary of your authentication security activity in your environment. Use this dashboard to gain insights into your user authentication attempts and login activity in your environment. To learn more about this dashboard, see [Authentication Management Security](dashboard/authentication-management-security.md).

## Customize your dashboards

You can change the background color of your Dashboard. By default, your Dashboard is in Light Mode. To change the background of your Dashboard, click the color icon (![](../Resources/Images/dashboard/color-icon.png)) on the top right, and then choose one of the following options:

* Light Mode
* Dark Mode
* Blue Mode
* Full Screen
