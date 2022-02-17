# Incidents

Alert Logic released an upgraded version of the Incidents page with enhanced features. You can switch between the updated Incidents page and the existing Incidents page by using the toggle icon (![](../Resources/Images/incidents/toggle.png)) on the upper-right side of the page. For more information, see [Incidents Upgrade ](../get-started/incidents-upgrade.md).

The Alert Logic console displays information about incidents, how to use that information to manage and close incidents, and how to secure your environments. An incident includes one or more suspicious events that require attention to maintain your security posture, achieve regulatory compliance, or both. Alert Logic generates incidents from multiple detection sources, and then organizes the incidents by threat level and classification type.

You can check the operational status of the Alert Logic intrusion detection services in the Service Status page in the Alert Logic console. Alert Logic recommends that you subscribe to the Service Status page and all your Alert Logic components, including Network IDS. For more information about the Service Status page and how to subscribe, see [Service Status](service-status.md).

In early 2020, the Incident Summary page was deprecated. The information is still available on the [Threat Summary Dashboard](dashboard/threat-summary.md).

## View incidents

The Incidents page, under ![](../Resources/Images/dashboard/respond-icon.png)**Respond** in the Alert Logic console, provides you with the information you need to analyze and address incidents in your environment.

The list on the Incidents page displays all the open, snoozed, or closed incidents in your account environment, as well as the account, deployment, date and time, the IP address of the attacker, and the target appliance name.

### Incident filters

You can apply filters to narrow the list to a specific set of incidents. Use the list on the left to choose the filters.

You can only view one status at a time. Choose which incident status you want to view:

* Open incidents
* Snoozed incidents
* Closed incidents

You can also apply the following secondary filters on those incidents:

* Threat Level
* Classification
* Detection Source
* Deployment
* Correlation Name

If you select the Deployment filter, and then select a deployment, the following filters are also available:

* Regions
* VPCs
* Subnets
* Tags
* Service
* Role

### Advanced incident search

The advanced search feature allows you to create complex queries that can combine with selected filters to further refine your incident search results. To access the advanced search feature, click **advanced search** under the search bar.

In the advanced search field, type a query statement using available fields and operators. If needed, you can use subsequent search fields to add <kbd>OR</kbd> statements and create a search that tests for multiple conditions. As you type a search statement, a warning icon (![](../Resources/Images/Icons/warning_icon_sql.png)) appears to the left of the search field until the query contains valid syntax. You cannot submit a search with invalid syntax.

A common query you can perform with the advanced incident search is:

The query below searches for brute force incidents. 

<kbd>Classification="brute-force"</kbd>

For a complete list of fields and additional sample search statements, see [Perform Advanced Searches](advanced-search.md).

#### Search by date and time range

The date range drop-down menu allows you to display incidents that occurred during a selected date range and within a time range for the selected dates. Select from the following to display incidents that occurred within the specified date and time range:

* This Month— Displays a calendar of the current month with all days highlighted.
* Today— Displays a calendar with the current day highlighted.
* This Week— Displays a calendar with the current week highlighted.
* All— Displays a calendar, on which you can click to select days, or a date range, for which you want to see incidents.

Each selection allows you to specify a time range to further narrow the search results.

## About threat levels

Incident threat levels convey the severity of each incident raised for protected assets, which allows you to assess and prioritize the actions to take toward threat remediation. Alert Logic categorizes incidents with the following icons and colors:

* ![](../Resources/Images/Icons/threat_critical_icon.png) Critical
* ![](../Resources/Images/Icons/threat_high_icon.png) High
* ![](../Resources/Images/Icons/threat_medium_icon.png) Medium
* ![](../Resources/Images/Icons/threat_low_icon.png) Low
* ![](../Resources/Images/Icons/threat_info_icon.png) Info

## About incident classification types

Alert Logic classifies incidents based on evidence received from monitored assets. The following table lists and defines the possible classification types.

| Classification label in Alert Logic console | Classification | Description  |
|---|---|---|
| application-attack | Application attack | An application attack incident identifies attacks that target application-specific vulnerabilities. Alert Logic creates an application attack incident when an attacker attempts to compromise an application with a buffer overflow, race condition, directory traversal, SQL injection, cross-site scripting, or <kbd>/usr/bin/perl</kbd> or other UNIX command attempts. |
| admin:activity | Admin activity | An admin security incident identified from security applications is related specifically to administrative actions. Alert Logic generates an authentication security incident when a user  grants another user administrator privileges and a user attempts to access an admin application. For more information on admin incident activity, see [Authentication Application Security Incidents](security-incidents.md) |
| authentication:activity | Authentication activity | An authentication security incident identified from security applications  relates specifically to user logins and user behavior. Alert Logic generates an authentication security incident when brute force activity is detected from an IP address, disabled MFA of a user from the sign-in logs, login failure from a risky IP address and sign-in attempts from a malicious IP address, logins detected from multiple countries in one day,successful login from a risky IP, and credential stuffing activity.  For more information on authentication in incident activity, see [Authentication Application Security Incidents](security-incidents.md) |
| brute-force | Brute force | A brute force incident identifies repeated authentication attempts and related activities. Alert Logic triggers a brute force incident when sufficient events indicate attempts to systematically compromise a system by brute force guessing valid user name and password combinations. |
| defensive-action | Defensive action |  |
| denial-of-service | Denial-of-service | A denial-of-service incident, which includes denial-of-service (DoS) attacks and distributed denial-of-service (DDoS) attacks, identifies an attempt to make computer resources or services unavailable either temporarily or indefinitely. Attackers typically use DoS and DDoS either to prevent e-commerce retailers from conducting business, or to send a social message. Alert Logic creates a denial-of-service incident when events indicate this type of attack. |
|  | Info leak | An information leak incident is a generally successful recon attempt. Alert Logic creates an information leak incident when events indicate attempts at reconnaissance activities. For example, port scans used to identify open and closed ports or obtaining information from a secure system can trigger an incident. For more information about reconnaissance activities, see [Recon](#Recon). |
|  | Log policy | A log policy incident is triggered when Alert Logic creates a log policy incident automatically, based on selected correlated log messages and specific conditions you define.                        

For example, you can specify that Alert Logic identify log messages containing five failed login events within a 60-second time period, and then create a log policy incident. |
| endpoint:activity | Endpoint Activity | An endpoint security incident is triggered when ransomware is detected on a single or multiple hosts,audit and remediation (potential new malware or suspicious event detected), outbreak of non-mitigated suspicious threats, non-mitigated malicious threats across multiple hosts, outbreak of malicious threats mitigated across multiple hosts, an agent that failed to remediate, and an agent with a high severity alert  (malicious and non-mitigated). For more information on endpoint activity incidents, see [Endpoint Security Incidents](endpoint-incidents.md) |
| log-review | Log Review | Log Review incidents come from the Alert Logic Log Review service. Some incidents are escalated by an Alert Logic analyst, and the rest appear as info level incidents. |
|  | Misconfiguration | Alert Logic triggers a misconfiguration incident when events indicate that a system is incorrectly configured. Attackers can use the misconfiguration to compromise the system. |
| policy-violation | Policy violation | A policy violation incident identifies activities that violate the acceptable use policies of most companies. These activities include viewing inappropriate material, peer-to-peer activity, and firewall policy changes. |
| recon | Recon | A recon incident identifies events that indicate reconnaissance activities against a network or set of hosts to evaluate them as a target. The activities that trigger this incident include gathering information about a server operating system, software versions, or the presence of debugging or demonstration scripts. |
| suspicious-activity | Suspicious activity | A suspicious activity incident identifies activity not included in another category that requires further research. Alert Logic creates a suspicious activity incident when anomalous activities, which could indicate a compromise, occur.

For example, the addition of a new domain administrator without the intent and knowledge of existing administrators could indicate an attacker added the administrator role to gain control over the environment or to provide a backdoor entry into the systems. |
| base | ?? |  |
| trojan-activity | Trojan activity | A Trojan activity incident identifies activity that indicates a host is infected by a Trojan horse or other type of backdoor malware, which masquerades as a legitimate program but actually steals information or harms the system. |
| worm-activity | Worm activity | A worm activity incident identifies hosts that display signs of worm infection.  A computer worm is self-replicating malware that uses a network to propagate and copy itself to other nodes, with or without your intervention. A worm typically uses a known vulnerability, and can cause damage by altering the infected system and consuming valuable network bandwidth. |

## About detection sources

Alert Logic detection sources convey the source of the incident. The following table lists and defines the possible detection sources.

| Detection Source | Description |
|---|---|
| Correlation Rules | You can define correlation rules to perform your own analysis of log messages and configure the correlation to generate an incident. For more information, see [Correlations and Notifications](../configure/notifications/log-correlation.md). |
| Network IDS | The Network Intrusion Detection System (Network IDS) monitors your deployments and generates incidents when it detects security threats such as brute force attacks, privilege escalation, and ransomware. |
| Manual | The Manual detection source is for incidents created  manually from the Log Search page in the Alert Logic console. For more information, see [Work with Log Messages](log-search/analyze-log-messages.md). |
| Firewall | Alert Logic can detect and generate firewall security incidents from log data collected from third-party firewall application resources. For more information, see [Firewall Incidents and Log Configuration](firewall-incidents.md). |
| Web Log Analytics (WLA) | Alert Logic generates incidents from log data collected from the WLA configuration that detects  common application vulnerabilities. For more information, see [About Alert Logic Web Log Analytics (WLA)](../get-started/about-wla.md). |
| Log Mgmt | Alert Logic generates incidents when the Log Management service detects suspicious activity such as unauthorized privilege escalations, brute force attempts, and access activities. |
| GuardDuty | Amazon GuardDuty is a continuous security monitoring service that you can integrate with Alert Logic. GuardDuty uses security logic and AWS usage statistics techniques to identify unexpected and potentially unauthorized and malicious activity, like escalations of privileges, uses of exposed credentials, or communication with malicious IPs, URLs, or domains.  For more information, see [Integrate Amazon GuardDuty Findings into Alert Logic Incidents](../configure/integrate-guard-duty-findings.md). |

## Incident actions

The incident list provides you with information that helps you determine what action to take for each incident. Each incident on the list allows you to [preview the incident](#incidentPreview), or open the incident to view the [Investigation Report](#investigationReport), [Recommendations](#recommendations), or [Evidence](#evidence). All views allow you to take certain actions to address the incident.

### Update an incident

**Update** (![](../Resources/Images/pencil icon.png)) allows you to choose from a list of options to update an incident with your assessment of the threat, and add an optional note to provide additional details about your update.

The following Threat Assessment options inform others in your organization whether the threat is valid, and what action (if any) the organization should take to remediate the threat.

Threat presents a valid risk:

* Taking action to mitigate the threat.
* Risk is acceptable. No action required.

Threat does not present a valid risk:

* Compensating control in place. No action required.
* The threat is not valid.
* Other assessment.

You can also mark the incident as **Not concluded yet.**

If you provide an update for an incident, you inform others in your organization about the status of the incident, and they can read detailed notes about any actions taken.

If you update an incident, the incident remains open.

### Snooze an incident

**Snooze** (![](../Resources/Images/snooze_blk_29x29.png)) allows you to temporarily remove an incident from the list until you remediate and close the incident. Snooze appears on the Investigation Report, Recommendations, and Evidence pages. To snooze an incident:

1. Select from the snooze options (tomorrow, in a couple days, next week, or in two weeks) when to return the incident to the Incident List.
2. Add an optional note about the incident.
3. Click **Snooze**.

You can click the **Snoozed** icon (![](../Resources/Images/snooze_grn_29x29.png)) to edit your snooze options, or to cancel the snooze and return the incident to the list.

### Close an incident

The option to close an incident appears on the Investigation Report, Recommendations, and Evidence pages. When you close an incident, you remove it from the list.

Click **Close** (![](../Resources/Images/close icon_30x29.png)) to close an incident.

Fill out the following information to justify closing the incident:

* Your assessment of the threat. 

The following Threat Assessment options inform others in your organization whether the threat is valid, and what action (if any) the organization should take to remediate the threat.
Threat presents a valid risk:
Threat does not present a valid risk:
   * Compensating control in place. No action required.
   * The threat is not valid.
   * Other assessment.
   * Taking action to mitigate the threat.
   * Risk is acceptable. No action required.
* Notes about the incident, including your reasons for closing the incident, and any steps taken to address the threat.

### Reopen an incident

If you determine a closed incident merits further investigation or discussion, you can reopen the incident.

To reopen a closed incident:

1. Filter the list by **Closed** incidents.
2. Click the incident you want to reopen.
3. Click **Closed**.
4. Add an optional note to explain why you reopened the incident.
5. Click **REOPEN**.

## Incident preview

Click **Preview** for more information about the incident, including:

* Incident ID
* Attacker IP address
* Target
* Account
* Deployment name
* Incident classification
* Detection source
* Appliance name

The preview allows you to update an incident, close an incident, or snooze an incident. For more information, see [Incident actions](#incidentActions).

Click **Open** to view the details of any incident on the list. Incident details appear on the [Investigation Report](#investigationReport), [Recommendations](#recommendations), and [Evidence](#evidence) pages. The information contained in these pages helps you decide whether to update, close, snooze, or reopen an incident.

### Investigation Report

When you open an incident, Alert Logic displays the Investigation Report, which includes an attack summary. This page describes the attack type and the attack methods, which help you understand the incident and its impact on your assets. If Alert Logic receives metadata from your assets, the Investigation Report also displays a topology diagram, which allows you to click an asset to view its details. For more information,  see [Topology](topology.md). In addition, the [Audit Log](#auditLog) lists the activity for the selected incident.

Click **SEE RECOMMENDATIONS** to learn how to remediate the incident and protect the threatened asset.

### Recommendations

Recommendations provides one or more courses of action you should take to secure the asset under attack and remediate the incident. In addition, the [Audit Log](#auditLog) lists the activity for the selected incident.

After you perform the recommended courses of action, click **Close** to mark the incident as closed and clear it from the list. For more information about closing incidents, see [Close an incident](#closeIncident).

### Evidence

The Evidence page displays information about the incident, including events, correspondence, and activity. You can use the information on this page to determine how to address incidents in your environment.

The Evidence page uses the following icons to display the following information about the selected incident

* ![](../Resources/Images/Icons/incident_activity.png) **Incident activity**—The Incident Activity icon lists activity and logs associated with the selected incident. The numeral on the icon represents the number of activities associated with the attack. Click the icon to expand the section and reveal details about the attack and the assets involved, as well as all activity and logs for the incident.
* ![](../Resources/Images/Icons/incident_flag.png) **Flagged evidence**—Alert Logic analysts can flag items of interest as supporting evidence for the attack and provide notes specific to each flagged item.
* ![](../Resources/Images/Icons/threat_critical_icon.png) **System-generated event**—This indicates the creation of the incident, or that the threat rating of the incident changed. The color and shading of the icon corresponds with the threat rating, as seen in [About threat levels](#aboutThreatLevels).
* ![](../Resources/Images/Icons/incident_al_note to_cust.png) **Incident notes from **Alert Logic—An Alert Logic analyst can provide notes about the incident, which appear in the Audit Log and Evidence List.
* ![](../Resources/Images/Icons/incident_escalated.png) **Incident escalated to customer**—The incident escalation icon indicates that Alert Logic notified you by email that the incident escalated. The color of the icon corresponds with the incident threat rating, as seen in [About threat levels](#aboutThreatLevels).
* ![](../Resources/Images/Icons/user_initial_icon.png) **Customer notes**—Any notes you create about the incident appear in this section.

Click the incident activity icon (![](../Resources/Images/Icons/incident_activity.png)) to view the events most relevant to the selected incident. If the incident is an IDS incident, and if you want to analyze all incident events, you can download (![](../Resources/Images/Icons/download.png)) all the incident event information to a PCAP file, which you can view in a third-party PCAP analyzer, such as [Wireshark](https://www.wireshark.org/).

### Audit Log

The Audit Log, which appears on the Investigation Report and Recommendations pages, uses the following icons to display milestone actions and information about the selected incident:

* ![](../Resources/Images/Icons/incident_flag.png) **Flagged evidence**—Alert Logic analysts can flag items of interest as supporting evidence for the attack and provide notes specific to each flagged item.
* ![](../Resources/Images/Icons/threat_critical_icon.png) **System-generated event**—This indicates the creation of the incident, or that the threat rating of the incident changed. The color and shading of the icon corresponds with the threat rating, as seen in [About threat levels](#aboutThreatLevels).
* ![](../Resources/Images/Icons/incident_al_note to_cust.png) **Incident notes from **Alert Logic—An Alert Logic analyst can provide notes about the incident, which appear in the Audit Log and Evidence List.
* ![](../Resources/Images/Icons/incident_evolved-red.png) **Evolved incident**—This icon represents an incident that evolved, and the color of the icon indicates the current, evolved threat level of the incident.
* ![](../Resources/Images/Icons/incident_escalated.png) **Incident escalated to customer**—The incident escalation icon indicates that Alert Logic notified you by email that the incident escalated. The color of the icon corresponds with the incident threat rating, as seen in [About threat levels](#aboutThreatLevels).
* ![](../Resources/Images/Icons/user_initial_icon.png) **Customer notes**—Any notes you create about the incident appear in this section.

The Audit Log information is similar to that of the Evidence page, but does not include the incident activity. Click **Evidence** for more information about incident activity.

### Bulk actions and exports

The Incident List supports bulk actions if you want to update, snooze, close or export one or multiple incidents. From the list, you can click the selection box (![](../Resources/Images/incident_selector.png)) above the incidents to select all incidents. If you hover over and click the threat level icon for one or more incidents, you can select those incidents for a single action.

When you select one or more incidents, you can also choose to export the incident details to a CSV file to view later, or to share with others in your organization.

## Multi-account management

The account selector allows you to monitor all the managed (child) accounts in your organization. If you use this feature to change your account selection to that of a managing (parent) account, you can monitor, assess, and compare the security posture across the entire organization.

Click the account name located in the upper right of your screen to view the full list of accounts in your organization. From the drop-down, select a parent account. You can use the search feature to narrow the list.

If your organization manages assets for other customer accounts, you could see data from child accounts on the Incidents page and the Reports page.

For all other features, the Alert Logic console displays results only for the chosen customer account. If, on any feature page, you want to view results for only a specific managed account, use the account selector to change the customer account.

## Incident notifications

The Notifications feature in the Alert Logic console can alert you, other subscribed users, or a configured connector (such as a webhook) when incidents that meet specific criteria  occur.
Notifications allow you to know about, and respond quickly to, threats or changes in your environment. In addition, email notifications for escalated incidents include that notes the Alert Logic analyst provided in the Incidents page.

To set up incident notifications, click ![](../Resources/Images/dashboard/notifications-icon.png)  **NOTIFICATIONS** at the top right, and then click **Add Notification**. For more information, see [Incident Notifications](../configure/notifications/incident.md).

## Incident Summary

The Incident Summary provides a high-level, interactive view of all open incidents, arranged by classification type and threat level.

The Summary displays the total number of open incidents and affected hosts. The interactive infographic allows you to hover over an incident circle to determine the number of incidents of that classification type at that severity level. Click the incident circle to open the [View incidents](#incidentList), filtered by the specified classification and threat level. Click a classification type on the infographic to open the Incident List, filtered by incidents of that classification type.

About incident evolution

Incident evolution (Cloud Defender only) occurs when Alert Logic receives additional events associated with the incident and then creates an incident of a higher threat rating. If an incident evolves, the Alert Logic Security Operations Center (SOC) sends a new incident notification.
