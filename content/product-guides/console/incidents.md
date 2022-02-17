# Incidents

## Overview

Alert Logic Cloud Defender and Alert Logic Cloud Insight Essentials display information about incidents, how to use that information to manage and close incidents, and how to secure your environments.

An **incident** comprises correlated suspicious **events** that require attention to maintain your security posture, achieve regulatory compliance, or both. Alert Logic generates incidents based on various predefined scenarios.

In addition, Alert Logic uses evidence received from monitored assets to classify threats by the type of attack they represent and to assign a threat level to the incident.

The [Incident Summary](#incidentSummary) and the [Incident List](#incidentList) under the Incidents tab in the Alert Logic console provide you with the information you need to analyze and address incidents in your environment. The [Events](#monitorEvents) page, under the Search tab, provides detailed information about the events involved with specific incidents. Under [Blocks](#Blocks) on the Search tab, you can access, view details of, and search blocking actions instituted by your network. Finally, event and incident [Alert Rules](#AlertRules) can be created and viewed under the Configuration tab.

You can also manage IP addresses that have been blocked on your network.

### About threat levels

Incident threat levels convey the severity of each incident raised for protected assets, which allows you to assess and prioritize the actions to take toward threat remediation. Alert Logic categorizes incidents with the following icons and colors:

* ![](../../Resources/Images/Icons/threat_critical_icon.png) Critical
* ![](../../Resources/Images/Icons/threat_high_icon.png) High
* ![](../../Resources/Images/Icons/threat_medium_icon.png) Medium
* ![](../../Resources/Images/Icons/threat_low_icon.png) Low
* ![](../../Resources/Images/Icons/threat_info_icon.png) Information

### About incident classification types

Alert Logic classifies incidents based on evidence received from monitored assets. The following table lists and defines the possible classification types.

| Classification | Description  |
|---|---|
| Application attack | An application attack incident identifies attacks that target application-specific vulnerabilities. Alert Logic creates an application attack incident when an attacker attempts to compromise an application with a buffer overflow, race condition, directory traversal, SQL injection, cross-site scripting, or <kbd>/usr/bin/perl</kbd> or other UNIX command attempts. |
| Brute force | A brute force incident identifies repeated authentication attempts and related activities. Alert Logic triggers a brute force incident when sufficient events indicate attempts to systematically compromise a system by brute force guessing valid user name and password combinations. |
| Denial-of-service | A denial-of-service incident, which includes denial-of-service (DoS) attacks and distributed denial-of-service (DDoS) attacks, identifies an attempt to make computer resources or services unavailable either temporarily or indefinitely. Attackers typically use DoS and DDoS either to prevent e-commerce retailers from conducting business, or to send a social message. Alert Logic creates a denial-of-service incident when events indicate this type of attack. |
| Info leak | An information leak incident is a generally successful recon attempt. Alert Logic creates an information leak incident when events indicate attempts at reconnaissance activities. For example, port scans used to identify open and closed ports or obtaining information from a secure system can trigger an incident. For more information about reconnaissance activities, see [Recon](#Recon). |
| Log policy | A log policy incident is triggered when Log Manager creates a log policy incident automatically, based on selected correlated log messages and specific conditions you define.                        

For example, you can specify that Alert Logic identify log messages containing five failed login events within a 60-second time period, and then create a log policy incident. |
| Misconfiguration | Alert Logic triggers a misconfiguration incident when events indicate that a system is incorrectly configured. Attackers can use the misconfiguration to compromise the system. |
| Policy violation | A policy violation incident identifies activities that violate the acceptable use policies of most companies. These activities include: viewing inappropriate material, peer-to-peer activity, and firewall policy changes. |
| Recon | A recon incident identifies events that indicate reconnaissance activities against a network or set of hosts to evaluate them as a target. The activities that trigger this incident include gathering information about a server operating system, software versions, or the presence of debugging or demonstration scripts. |
| Suspicious activity | A suspicious activity incident identifies activity not included in another category that requires further research. Alert Logic creates a suspicious activity incident when anomalous activities, which could indicate a compromise, occur.

For example, the addition of a new domain administrator without the intent and knowledge of existing administrators could indicate an attacker added the administrator role to gain control over the environment or to provide a backdoor entry into the systems. |
| Test | Developers use the test incident class for testing purposes, such as testing proposed classifications. |
| Trojan activity | A Trojan activity incident identifies activity that indicates a host is infected by a Trojan horse or other type of backdoor malware, which masquerades as a legitimate program but actually steals information or harms the system. |
| Worm activity | A worm activity incident identifies hosts that display signs of worm infection.  A computer worm is self-replicating malware that uses a network to propagate and copy itself to other nodes, with or without your intervention. A worm typically uses a known vulnerability, and can cause damage by altering the infected system and consuming valuable network bandwidth. |

### About incident evolution

In Cloud Defender only, an incident can change in severity as more information is discovered. This process, called "incident evolution," occurs when Alert Logic receives additional events and then creates an incident of a higher threat rating. If an incident evolves, the Alert Logic Security Operations Center (SOC) sends a new incident notification.

## Incident Summary

The Incident Summary provides a high-level, interactive view of all open incidents, arranged by classification type and threat level.

The Summary displays the total number of open incidents and affected hosts. The interactive infographic allows you to hover over an incident circle to determine the number of incidents of that classification type at that severity level. Click the incident circle to open the [Incident List](#incidentList), pre-filtered by the specified classification and threat level. Click a classification type on the infographic to open the Incident List, filtered by incidents of that classification type.

## Incident List

The Incident List provides a list of all the incidents in your environment. If an incident on the list evolved (Cloud Defender only), you can click the evolution bar to view a history of the incident evolution.

You can click any incident on the list to learn more about it and take remediation steps. Incident detail pages include the [Investigation Report](#investigationReport), [Recommendations](#recommendations), and [Evidence](#evidence). On each of these pages you can view the [Audit Log](#auditLog), which lists the activity for the selected incident. You may also [Update an incident](#updateIncident), [Close an incident](#closeIncident), or even [Reopen an incident](#reopenIncident).

If the Incident List contains a large number of incidents, you can apply filters to narrow the list to a specific set of incidents. Use the options on the left to choose **Open**, **Snoozed**, or **Closed** incidents and filter those incidents by **Threat Level** or **Classification Type**. If you have Amazon GuardDuty, you may also filter by **Deployments**, **Regions**, **VPCs**, and **Subnets**.

### Investigation Report

When you select an incident from the Incident List, Cloud Defender provides details about the attack from which the incident originated, including the location of the attacker and the targeted asset.

The incident details are listed across the top, followed by the buttons to [Update an incident](#updateIncident), [Snooze an incident](#snoozeIncident), and [Close an incident](#closeIncident). Below that is the Investigation Report and the [Audit Log](#auditLog).

**Investigation Report**

The Investigation Report section includes information describing the attack type and the attack methods to help you understand the incident and its impact on your assets.

Click **SEE RECOMMENDATIONS** at the bottom to learn how to remediate the incident and protect the threatened asset. You can also click on **Recommendations** in the left navigation bar.

### Recommendations

Recommendations provides one or more actions you should take to secure the asset under attack and remediate the incident. It also shows the [Audit Log](#auditLog) for the incident.

After you perform the recommended course of action, click **Close** to mark the incident as closed and clear it from the Incident List. For more information about closing incidents, see [Close an incident](#closeIncident).

### Evidence

The Evidence page uses the following icons to display all information about the selected incident.

* ![](../../Resources/Images/Icons/incident_activity.png) **Incident activity**—The Incident Activity icon lists activity and logs associated with the selected incident. The numeral on the icon represents the number of activities associated with the attack. Click the icon to expand the section and reveal details about the attack and the assets involved, as well as all activity and logs for the incident.
* ![](../../Resources/Images/Icons/incident_flag.png) **Flagged evidence**—Alert Logic analysts can flag items of interest as supporting evidence for the attack and provide notes specific to each flagged item.
* ![](../../Resources/Images/Icons/threat_critical_icon.png) **System-generated event**—This indicates the creation of the incident, or that the threat rating of the incident changed. The color and shading of the icon corresponds with the threat rating, as seen in [About threat levels](../../analyze/incidents.md#aboutThreatLevels).
* ![](../../Resources/Images/Icons/incident_al_note to_cust.png) **Incident notes from **Alert Logic—An Alert Logic analyst can provide notes about the incident, which appear in the Audit Log and Evidence List.
* ![](../../Resources/Images/Icons/incident_evolved-red.png) **Evolved incident**—This icon represents an incident that evolved, and the color of the icon indicates the current, evolved threat level of the incident.
* ![](../../Resources/Images/Icons/incident_escalated.png) **Incident escalated to customer**—The incident escalation icon indicates that Alert Logic notified you by email that the incident escalated. The color of the icon corresponds with the incident threat rating, as seen in [About threat levels](../../analyze/incidents.md#aboutThreatLevels).
* ![](../../Resources/Images/Icons/user_initial_icon.png) **Customer notes**—Any notes you create about the incident appear in this section.

The information in Evidence can be filtered by source and provides access to relevant events or logs related to this incident.

### Audit Log

The Audit Log, which appears on the [Investigation Report](#investigationReport), [Recommendations](#recommendations), and the [Evidence](#evidence) pages, uses the following icons to display milestone actions and information about the selected incident:

* ![](../../Resources/Images/Icons/incident_activity.png) **Incident activity**—The Incident Activity icon lists activity and logs associated with the selected incident. The numeral on the icon represents the number of activities associated with the attack. Click the icon to expand the section and reveal details about the attack and the assets involved, as well as all activity and logs for the incident.
* ![](../../Resources/Images/Icons/incident_flag.png) **Flagged evidence**—Alert Logic analysts can flag items of interest as supporting evidence for the attack and provide notes specific to each flagged item.
* ![](../../Resources/Images/Icons/threat_critical_icon.png) **System-generated event**—This indicates the creation of the incident, or that the threat rating of the incident changed. The color and shading of the icon corresponds with the threat rating, as seen in [About threat levels](../../analyze/incidents.md#aboutThreatLevels).
* ![](../../Resources/Images/Icons/incident_al_note to_cust.png) **Incident notes from **Alert Logic—An Alert Logic analyst can provide notes about the incident, which appear in the Audit Log and Evidence List.
* ![](../../Resources/Images/Icons/incident_evolved-red.png) **Evolved incident**—This icon represents an incident that evolved, and the color of the icon indicates the current, evolved threat level of the incident.
* ![](../../Resources/Images/Icons/incident_escalated.png) **Incident escalated to customer**—The incident escalation icon indicates that Alert Logic notified you by email that the incident escalated. The color of the icon corresponds with the incident threat rating, as seen in [About threat levels](../../analyze/incidents.md#aboutThreatLevels).
* ![](../../Resources/Images/Icons/user_initial_icon.png) **Customer notes**—Any notes you create about the incident appear in this section.

### Update an incident

**Update**, which appears on the [Investigation Report](#investigationReport), [Recommendations](#recommendations), and [Evidence](#evidence) pages, allows you to choose from a list of options to update an incident with your assessment of the threat, and add an optional note to provide details about your update.

The following Threat Assessment options inform others in your organization whether the threat is valid, and what action (if any) the organization should take to remediate the threat.

Threat presents a valid risk:

* Taking action to mitigate the threat.
* Risk is acceptable. No action required.

Threat does not present a valid risk:

* Compensating control in place. No action required.
* The threat is not valid.
* Other assessment.

Adding an update allows others to know the status of the incident and read detailed notes about any actions taken.

If you update an incident, the incident remains open. [Close an incident](#closeIncident) is the only action that allows you to close the incident and remove it from the [Incident List](#incidentList).

### Snooze an incident

**Snooze** allows you to temporarily remove an incident from the [Incident List](#incidentList) until you remediate and close the incident. Snooze appears on the [Investigation Report](#investigationReport), [Recommendations](#recommendations), and [Evidence](#evidence) pages. To snooze an incident:

1. Select from the snooze options (tomorrow, in a couple days, next week, or in two weeks) when to return the incident to the Incident List.
2. Add an optional note about the incident.
3. Click **Snooze**.

When you snooze an incident the icon becomes a green "Snoozed" icon.

You can click the Snoozed icon to edit your snooze options, or to cancel the snooze and return the incident to the Incident List.

### Close an incident

The option to close an incident appears on the [Investigation Report](#investigationReport), [Recommendations](#recommendations), and [Evidence](#evidence) pages. When you close an incident, you remove it from the [Incident List](#incidentList).

Click **Close** to close an incident.

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
* (Optional) Notes about the incident, including your reasons for closing the incident, and any steps taken to address the threat.

### Reopen an incident

If you determine a closed incident merits further investigation or discussion, you can reopen the incident.

To reopen a closed incident:

1. Filter the [Incident List](#incidentList) by **Closed** incidents.
2. Click the incident you want to reopen.
3. Click **Closed**.
4. Add an optional note explaining why you are reopening the incident.
5. In the panel that appears, click **REOPEN**.

## Events

Events, log messages, and web violations can generate incidents. The ability to view the details of an event is a key part of threat and vulnerability management. The Events link opens a new tab on your browser on which you can search for and view, a list of events and event details, such as target host, response events, event correlation, threat scenario logs, and more.

    To return to Incidents, close the Event List tab in your browser.     ### View events

To view your events, click **Search**.

Available event list options include :

* Range—To display events based on when they occurred, select a value in the  **Range** drop-down list, which appears above the event list.

    You can select **Enable range greater than 1 day**, but use of a range greater than one day can decrease performance.    * Acknowledge events—To acknowledge events, select the box next to each event to update, or click **Select all** at the bottom of the list,  and then click **Mark as acknowledged**.
* Status or type—To display events by status or type, at the bottom of the list of events, next to **Show Events**, select one or more of the following options and click **Apply**:
   * **Acknowledged**—Shows events that have been acknowledged
   * **Correlative**—Shows events that are correlated
   * **Informative**—Shows events that are informative
   * **Non-Processed Only**—Shows events that have not yet been processed
* View event details—To view the details of an event, including header and payload information, the target host, response events, event correlation and payload reconstruction. For more information, see [View event details](#View3).

### Search events

You can use any combination of the available search features—the event number search, search filters, and right-click options—to either search for a specific event, or narrow a long list of events. Each method provides a different type of search capability.

#### Event number search

The Search box provides a simple way to search for events by event ID number. In the **Event #** box, which is located above the list of events, type the event ID number for the event you want to find, and then click **Search**.

#### Search filters

The most detailed way to search events is to use search filters. You can use search filters to combine different search parameters, such as event  classification, threat rating, and signature. In addition, you can use the Saved Filters drop-down menu to select a filters you created.

To search events using search filters:

1. (Optional) In the **Saved Filters** drop-down list, select a previously saved filter if applicable, and click **Load** or **Load in New Window**.
2. In the drop-down list of columns, select a column to filter by.
3. In the drop-down list of operations, select an operation for the search term for the selected column (for example, **does not contain**).
4. For the search term, enter a search value. The type of entry field that is used depends on the selected column; for example, a text box is used for Signature, a list of defined values is used for Classification, and date and time fields are used for Date.
5. (Optional) Click **Add another filter** to add an additional search parameter, and repeat steps 5 - 7. If you have created several filters and want to delete one, click **Remove** for the filter to discard.
6. Click **Apply Filters** to run your search query. 
Only those events that satisfy the search criteria are displayed.
7. (Optional) To save your defined filters, specify a name in the **Save filters as:** box, and click **Save**.
8. (Optional) To discard defined filters and applied results, click **Clear**.
9. (Optional) To hide the Search Filters configuration area, click **Search Filters**.

#### Right-click options

Right-click options allow you to filter and sort listed events by column values and defined values.

Available right-click options vary, depending on the content of the row in which you right-clicked.

To filter and sort events using right-click options:

1. On the Event list, click **Search** or **Apply Filters** to bring up your events.
2. In the list of events, right-click a value for an event and select one of the following options:
You can also click on the column heading to sort the list by the column.
   * **Only show rows with this value**
   * **Hide rows with this value**
   * **Clear show/hide/sort settings for this column**—This option returns the column to its default view.
   * **Sort list by this column**
   * **Roll up by this column**

To discard applied filters and results, click **Clear**.

### View event details

Within each event are details about the event, such as target host, response events, event correlation, threat scenario logs, and more. When viewing event details, you can scan involved IP addresses and look up WHOIS and NetBIOS information.

To view the details of an event:

1. On the Event list, click **Search** or **Apply Filters** to bring up your events.
2. In the displayed list of events, click the event to view.
3. Use the tabs at the bottom of the page to view the following event details:
   * **Header and Payload**—Provides a dump of header and payload data.
   * **Target Host**—Provides details of the target host, if available.
   * **Response Events**—Provides a list of response events.
   * **Event Correlation**—Lets you correlate events based on field values. To use, select a value from the **Search field** drop-down list and click the plus sign icon ( ![](../../Resources/Images/Icons/al_plussign.jpg) ). For the corresponding field that appears, select an appropriate value. Repeat this task to include additional fields, and then click **Go**.
   * **Threat Scenario Logs**—Lists any threat scenario logs, if available.
   * **Payload Reconstruction**—Provides data dumps of payloads for the main event and any response events.

### Update an event

When you investigate an event, you can update the event by acknowledging the event, creating an incident from the event, and adding the event to a case for tracking. You can also block the host at fault.

To update an event:

1. On the Event list, click **Search** or **Apply Filters** to bring up your events.
2. In the displayed list of events, click the **name** of the event to update. 
Event details appear.
3. Use the following options to update the event, as needed:
   * **Action**—To perform an action on an event, select one of the following values, and click **Update**:
      * **Block Host**—Block the host
      * **Create Incident**—Create an incident record for this event
      * **Acknowledge Event**—Mark the event as acknowledged
   * **Add to Case**—To add the event to the Case Creation cart, in the left navigation area, click **Add to Case**. For more information on cases, see Cases.

### View real-time NetBIOS, WHOIS, and IP Address Scan information

When evaluating blocks, you may find it useful to view real-time information about NetBIOS, WHOIS, and the IP address for the source and destination of the event.

You can view NetBIOS  for IPv4, and WHOIS for IPv4 and IPv6.

To view real-time NetBIOS, WHOIS, and IP Address Scan information:

1. On the Event list, click **Search** or **Apply Filters** to bring up your events.
2. In the list of displayed events, click the **Name** of the event to view.
3. On the **Event Details** page, right-click the source, destination, or proxy IP addresses.
4. From the displayed list, select  **Lookup Whois Information**, **Lookup NetBIOS Information**, or **Scan This IP Address Now**.

### Create an incident from an event

This feature is supported in Threat Manager only.

Incidents let you track a potential issue until it is resolved. When Threat Manager identifies a threat, it creates an incident with the related information.  In addition to these automatically-created incidents, you can create an incident based on an event that has occurred.

To create an incident from an event:

1. On the Event list, click **Search** or **Apply Filters** to bring up your events.
2. In the list of displayed events, click the **name** of the event for which to create an incident.
3. In the **Action:** list, select **Create Incident**, and then click **Go**.
4. Specify property values.
5. Click **Save**.

When specifying property values, you can specify correlation criteria to identify related events and log messages to include in the incident. At the bottom of the window, in the **Event Correlation** tab, from the **Search field** drop-down menu, select the value you want to add to the correlation criteria, and then click the plus sign icon (![](../../Resources/Images/Icons/al_plussign.jpg)). 

You can add multiple correlation criteria. **Transpose** lets you specify criteria for ports or IP addresses and whether the ports or IP addresses are the source or destination for the event.

If you add both the **Source Address** and **Transpose** criteria, Threat Manager finds events for which that IP address is either the source or destination address. For each correlation criteria, select whether you want to include or exclude the current event value by selecting the **is…** or **is not…** option for each criteria.

### Add an event to a case

To add an event to a case, you must first add the event to the Case Creation cart and then process the cart. Use the respective procedure below to select one or multiple events at a time.  For more information on cases, see Cases.

To select an event to add to a case:

1. On the Event list, click **Search** or **Apply Filters** to bring up your events.
2. In the displayed list of events, click the **name** of the event to add to a case.
The event details appear.
3. In the left navigation area, click **Add to case**. 
The event is added to the Case Creation cart.
4. Use one of the following procedures to add the event to a case (process the cart):
   * 
   * 

To select multiple events to add to a case:

1. On the Event list, click **Search** or **Apply Filters** to bring up your events.
2. Select the box for each event to add to a case.
3. Right-click an area in the list of events and select **Add to Case**.
The selected events are added to the Case Creation cart.
4. Use one of the following procedures to add the event to a case (process the cart):
   * 
   * 

## Blocks

The Events page also allows you to access, view details of, and search blocking actions instituted on your network. You can also roll back or reissue blocks. From the left navigation, above **Events**, click **Blocks**.

### View blocks

To view a list of blocks that have been instituted on your network, click **Search**.

Available options for block monitoring include:

* Display blocks based on when they were instituted. Select a value in the **Range** drop-down list. To increase the range to greater than a day, select **Enable range greater than 1 day**.

    Selection of "Enable range greater than 1 day," can increase search times, which results in a longer page load time.    * Perform a roll-back or a re-issue of a block. Select the box next to each block to act on or click **Select all** to select all listed blocks. Use the **With selected** drop-down list at the bottom of the page to select one of the following options, and then click **Go**:
You can also roll back or reissue a block when viewing block details.
   * **Roll-back**—Reverse the block
   * **Re-issue**—Reinstate the block
* View the details of a block. For more information, see .

### Search blocks

You can search instituted blocks  from the Defenses List using any combination of the number search, search filters, and right-click options. Each method provides a different type of search capability.

#### Block number search 

The block number search provides a simple way to search for block records by block ID number. In the **Block #** box, which is located above the list of blocks, type the block ID number for the block you want to find, and then click **Search**.

#### Search filters

The most detailed way to search blocks is to use search filters. You can use search filters to combine different search parameters, such as customer, status, action type, or firewall.

To search blocks using search filters:

1. On the Event list, click **Search** or **Apply Filters** to bring up your blocks.
2. (Optional) In the **Saved Filters** drop-down list, select a previously saved filter if applicable, and click **Load** or **Load in New Window**.
3. In the drop-down list of columns, select a column to filter by.
4. In the drop-down list of operations, select an operation for the search term for the selected column (for example, **is not**).
5. For the search term, enter a search value. The type of entry field that is used depends on the selected column.
6. (Optional) Click **Add another filter** to add an additional search parameter, and repeat steps 5 - 7. To delete a filter, click **Remove**.
7. Click **Apply Filters** to run your search query. 
Only those block records that satisfy the search criteria are displayed.
8. (Optional) To save your defined filters, specify a name in the **Save filters as:** box, and click **Save**.
9. (Optional) To discard defined filters and applied results, click **Clear**.
10. (Optional) To hide the Search Filters configuration area, click **Search Filters**.

#### Right-click options

Right-click options let you filter and sort displayed blocks using columns and defined values.

    Available right-click options vary, depending on the content of the row in which you right-clicked.    
To filter and sort blocks using right-click options:

1. On the Block list, click **Search** or **Apply Filters** to bring up your blocks.
2. In the list of blocks, right-click a value for a block and select one of the following options:
You can also click on the column heading to sort the list by the column.
The list of displayed blocks is updated.
   * **Only show rows with this value**
   * **Hide rows with this value**
   * **Clear show/hide/sort settings for this column**—This option returns the column to its default view.
   * **Sort list by this column**
   * **Roll up by this column**
4. (Optional) To discard applied filters and results, click **Clear**.

### View block details

Within each block record are details about the block, including any NetBIOS scan and WHOIS request information. When viewing block details, you can also roll back or reissue the block, or add the block to a case for tracking.

To view the details of a block:

1. On the Block list, click **Search** or **Apply Filters** to bring up your blocks.
2. Click the **ID** of the block to view.
Block details appear.
3. Use the tabs at the bottom of the page to view the respective details. The following tabs are available:
   * **Whois Requests**—Lists any WHOIS request information.
   * **History**—Lists activities related to the block, such as when and how the block was requested and if the block is active.
   * **NetBIOS Scans**—Lists any related NetBIOS scan information.
6. (Optional) To modify or perform an action on a block, see .

### Update a block

When working on a block, you can rollback or reissue a block if needed. You can also add tags to the block record and add the block record to a case for tracking.

This section describes blocking instances that have occurred on your network. For information about when to institute a block and blocking policies, see [Customer Accounts, User Accounts, and User Roles](../../prepare/users-roles.md#advancedTMConfiguration).

To update a block record:

1. On the Block list, click **Search** or **Apply Filters** to bring up your blocks.
2. Click the **ID** value for the block to update. 
Block details appear.
3. Use the following options to modify a block or the block record:
   * **Add tag**—To add keywords to a block record, click **Add tags**. Type tags to add to the block record, and click **Save Tags**.
   * **Action**—To perform an action on a block, select one of the following values, and click **Update**:
      * **Rollback**—Reverse the block
      * **Reissue Block**—Reinstate the block
      * *Waiting for block*—(For display only)
   * **Add to Case**—To add the block to the Case Creation cart, in the left navigation area, click **Add to Case**. For more information on cases, see Cases.

### Add a block to a case

To add a block to a case, you must first add the block to the Case Creation cart and then process the cart. Use the respective procedure below to select one or multiple blocks.  For more information on cases, see Cases.

To select a block to add to a case:

1. On the Block list, click **Search** or **Apply Filters** to bring up your blocks.
2. In the displayed list of blocks, click the **ID** of the block to add to a case.
The block details appear.
3. In the left navigation area, click **Add to case**. 
The block is added to the Case Creation cart.
4. Use one of the following procedures to add the block to a case (process the cart):
   * 
   * 

To select multiple blocks to add to a case:

1. On the Block list, click **Search** or **Apply Filters** to bring up your blocks.
2. In the displayed list of blocks, select the box for each block to add to a case.
3. Right-click an area other than the **ID** column and select **Add to Case**.
The selected blocks are added to the Case Creation cart.
4. Use one of the following procedures to add the block to a case (process the cart):
   * 
   * 

## Alert Rules

From the event monitoring feature, you can view and create rules for event and incident alerts.

### Define event alert rules

Event alerts notify you of event activities based on signatures. In addition to the details about the signature triggers, you can specify the minimum event severity threshold and how often to receive alert notifications.

To define an event alert rule:

1. At the top of the Alert Logic console,  in the drop-down menu, click **Incidents**.
2. In the left navigation area, under **Alert Rules**, click **Event**.
3. In **Rule Name**, type a descriptive name for the rule.
4. In **Minimum Time Between Alerts**, type the number of minutes between alert notifications. Type "0" to receive alerts when they occur.
5. If you manage child customer accounts, in the **Choose Child Customers to Apply Rule to** drop-down list, select one or more customers on whose events to alert you.
6. In **Minimum Event Severity to Trigger Rule**, type the severity value that must be met to trigger the rule.
7. Select one of the following options regarding when to trigger the rule:
   * **any signature is triggered on an appliance for the first time**—Trigger the rule the first time any signature occurs on an appliance.
   * **the event signature is in selected signatures**—Use the drop-down list to select a signature category, and then select specific signatures to trigger the rule.
   * **the event signature is not in the selected signatures**—Use the drop-down list to select a signature category, and then select specific signatures to trigger the rule when excluded.
9. Click **Save**.
The alert rule is activated and added to the list of existing alert rules.
10. (Optional) To view an existing rule, at the bottom of the page, click on the **Name** value for the rule to view.

### Define incident alert rules

Incident alerts notify you of incident activity. You can set your preferences to receive alert notifications based on incident creation or closure, or other changes in status. You can also specify the minimum severity threshold for incidents to be alerted on and how often to receive alert notifications.

To define an incident alert rule:

1. At the top of the Alert Logic console,  in the drop-down menu, click **Incidents**.
2. In the left navigation area, under **Alert Rules**, click **Incident**.
3. In **Rule Name**, type a descriptive name for the rule.
4. In **Minimum Severity to Trigger Rule**, select the severity value from the drop-down list that must be met to trigger the rule.
5. In **Choose Event Status to Trigger Rule**, select the incident status event to trigger the rule.
6. In **Time Between Alert Occurrences**, type the number of minutes between alert notifications. Type "0" to receive alerts when they occur.
7. If you manage child customer accounts, in the **Choose Child Customers to Apply Rule to** drop-down list, select one or more customers on whose events to alert you.
8. Click **Save**.
The alert rule is activated and added to the list of existing alert rules.
9. (Optional) To view an existing rule, at the bottom of the page, click on the **Name** value for the rule to view.
