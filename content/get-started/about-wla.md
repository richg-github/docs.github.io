# About Alert Logic Web Log Analytics (WLA)

Alert Logic Web Log Analytics (WLA) is a log-based application attack detection solution that protects your web applications from common application vulnerabilities. WLA analyzes web server access logs for threats and attacks with a combination of pattern-matching signatures, and anomaly detection and machine-learning engine. WLA also reduces the need for tuning, minimizes false-positives, and provides visibility by inspecting HTTPS requests for threats post-decryption. You can gain security visibility across all web applications in your organization.

WLA can serve as a supplemental resource to existing Alert Logic Managed Web Application Firewall (WAF) which can assist you in making informed decisions on when to upgrade the protection of an application.

WLA serves as a detection source for Alert Logic to generate   incidents in the  [Incidents](../analyze/incidents.md) page. You can also search for WLA logs in the [Search: Log Messages](../analyze/log-message-search.md) page in the Alert Logic console. You can access the [Web Log Analytics Dashboard](../analyze/dashboard/web-log-analytics.md), which provides visibility into incidents and observations detected from WLA logs in your environment.

WLA is offered to customers with a Managed Detection and Response, Professional, or Enterprise subscription. WLA currently supports deployment for IIS, Apache2, and Nginx web servers.

## WLA analytics

The WLA is composed of an attack and threat detection engine and ActiveRules and correlations.

The WLA engine can detect the following:

* Signature-based detections of general web attack methods like SQL Injection, Code Injection, OS Commanding, XSS, and more
* Virtual patch-based detection and attribution of exploits targeting known vulnerabilities and known web shells
* Anomaly based detection of brute-forced login attempts, known web shells, and suspicious POST requests

WLA ActiveRules and correlations consist of:

* Non-hostile behavior (false positives, authorized assessments)
* Activity and server response code-based incidents
* Correlation-based severity and compromise confidence

## WLA incidents

WLA incidents are listed in the [Incidents](../analyze/incidents.md) page and are automatically escalated as low or medium threats. A WLA incident is generated when one or more suspicious events are detected from WLA logs and require attention to maintain your security posture.

The [Incidents](../analyze/incidents.md) page provides you with information that helps you determine the action to take for each incident. Each incident on the list allows you to [preview the incident](https://docs.alertlogic.com/analyze/incidents.htm#incidentPreview), or open the incident to view the [Investigation Report](../analyze/incidents.md#investigationReport), [Recommendations](../analyze/incidents.md#recommendations), or [Evidence](../analyze/incidents.md#evidence). All views allow you to take certain actions to address the incident.

## Web Log Analytics (WLA) dashboard

The Web Log Analytics (WLA) dashboard provides visibility into threats, incidents, and observations detected from your WLA instance in your environment. You can use the dashboard to gain insights into the types of incidents detected in your environment,  analyze the effectiveness of your current incident response efforts, and learn about emerging threats.

This dashboard includes visuals of the following data:

* Count of open WLA incidents
* List of most seen attackers
* List of most attacked hosts
* Countries where WLA incidents originate
* Web attack trends
* Top observations

For more information, see the [Web Log Analytics Dashboard](../analyze/dashboard/web-log-analytics.md).

### WLA observations

Alert Logic also performs observations of relevant attack information that is derived from WLA logs. Observations do not always meet the criteria for Alert Logic to generate an incident, but can demonstrate security value. Observations can identify attack patterns and allow you to conduct threat hunting.

You can view and export data related to observations in the [Top Observations by SRC_IP and Attack](../analyze/dashboard/web-log-analytics.md#Top) visual of the WLA dashboard.

## WLA configuration

WLA currently supports IIS, Apache2, and Nginx web servers. You must have an Alert Logic agent or a local remote collector already installed to deploy WLA. For instructions on how to deploy WLA, see [Web Log Analytics (WLA) Configuration](../configure/wla-configuration.md).

Although steps to deploy WLA are different for each web server, you must configure flat file collection after you have deployed WLA. For more information on how to configure a flat file collection, see [Application Logs for Flat File Configuration](../configure/application-logs.md).

For large environments, Alert Logic recommends that you use a WAF. For more information, see [Alert Logic Managed Web Application Firewall (WAF) Basics](../configure/inline-waf/basics.md).
