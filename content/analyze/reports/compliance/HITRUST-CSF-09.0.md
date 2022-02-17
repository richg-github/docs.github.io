# HITRUST CSF 09.0 Communications and Operations Management

The HITRUST Common Security Framework (CSF) reports provide available documentation and compliance artifacts that help you demonstrate compliance with HITRUST CSF control categories, as outlined in the HITRUST Risk Management Framework.

The HITRUST CSF 09.0 Communication &amp; Operations Management report provides guidance on how to access configuration features in the Alert Logic console to that help you demonstrate compliance with Control Category 09.0.

**To access the HITRUST CSF 09.0 report:**

1. In the Alert Logic console, click the menu icon (![](../../../Resources/Images/dashboard/menu-icon.png)), and then click ![](../../../Resources/Images/dashboard/validate-icon.png)**Validate**.
2. Click **Reports**, and then click  **Compliance**.
3. Under **HITRUST CSF**, click **VIEW**.
4. Click **HITRUST CSF 09.0 Communication and Operations Management**.

## Filter the report

To refine your findings, you can filter your report by  date range and customer account.

### Filter the report using drop-down menus

By default, Alert Logic includes **(All)** filter values in the report.

**To add or remove filter values: **

1. Click the drop-down menu in the filter, and then select or clear values.
2. Click **Apply**.

The report summary page displays two columns. **Control References** lists each procedure that is required  to meet the selected  control objective. **Available Documentation and Artifacts** describes, and contains links to, the documentation and compliance artifacts that this report can demonstrate compliance with each control objective.

## Available Documentation and Artifacts

This report provides access to features in the Alert Logic console that help you demonstrate  compliance with the following control objectives in Control Category 09.0:

* 09.04 Protection Against Malicious and Mobile Code
* 09.06 Network Security Management
* 09.10 Monitoring

This report is composed of four pages, this Summary page, the Log Review Summary page, and the Log Review Incidents page. Each page includes filters to specify the scope of the information you need to collect.  The Log Review Summary page and the Log Review Incidents page has information that can help you demonstrate compliance with the Control Reference 09.ab Monitoring System Use section in Control Objective 09.10 Monitoring.

##  Control Objectives 09.04 Protection Against Malicious and Mobile Code

This section consists of specifications to meet the requirements for Control Objective 09.04 Protection Against Malicious and Mobile Code.  This control objective requires you to ensure that integrity of information and software is protected from malicious or unauthorized code.

### Control Reference 09.j (Level 1 Implementation Requirements)

Compliance with Control Reference 09.j Controls Against Malicious Code requires you to demonstrate protection against malicious code is based on malicious code detection and repair software, security awareness, and appropriate system access and change management controls.

This section  provides you with a link to the Alert Logic Extended Endpoint Protection page where you can review the protection status, software version status, and last check-in time for Windows and MacOS endpoints in your environment.  You can use this information  to  confirm you have protection against malicious code.

This section  provides you with a link to the Alert Logic Extended Endpoint Protection page where you can review malware attacks detected in your environment and the action taken in response to quarantine and override malicious files or isolated vulnerable endpoints.  You can use this information  to  confirm you have protection against malicious code.

##  Control Objectives 09.06 Network Security Management

This section consists of specifications to meet the requirements for Control Objective 09.06  Network Security Management.  This control objective requires you to ensure the protection of information in networks and protection of the supporting network infrastructure.

### Control Reference 09.m (Level 1 Implementation Requirements)

Compliance with Control Reference 09.m Network Controls requires that network managers implement controls to ensure the security of information in networks, and the protection of connected services from unauthorized access. Controls are implemented to ensure the availability of network services and information services using the network. Responsibilities and procedures are established for the management of equipment on the network, including equipment in user areas.

This section provides you with the following links for quick access to appropriate pages in the Alert Logic console:

* Networks monitored in your environment by the Network IDS in the [Health](../../health.md) page.
* The [Deployments](../../../get-started/deployments.md) page where you can view the Network IDS coverage in the scope of protection topology diagram for a specific deployment.        
The list of networks and topology provided by Alert Logic may not cover the entire cardholder data environment. You must provide network diagrams with all components of the cardholder data environment.
* The [PCI scanning page](../../../configure/pci-scans.md)  to review the latest 25 internal vulnerability scan reports for the most recent 12- month period.

##  Control Objectives 09.10 Monitoring 

This section consists of specifications to meet the requirements for Control Objective 09.10  Monitoring.  This control objective requires you to ensure information security events are monitored and recorded to detect unauthorized information processing activities in compliance with all relevant legal requirements.

This section of the report includes documentation and artifacts that help you demonstrate that you have  implemented procedures to ensure compliance with these Control References:

* 09.aa Audit Logging
* 09.ab Monitoring System Use
* 09.ac Protection of Log Information
* 09.ad Administrator and Operator Logs
* 09.ae Fault Logging

### Control Reference 09.aa (Level 1 Implementation Requirement)

Compliance with Control Reference 09.aa Audit Logging requires information systems processing covered information create a secure audit record each time a user accesses, creates, updates, or archives covered information via the system.

This section provides you with a link for quick access to the [Log Search](../../log-message-search.md) page in the Alert Logic console, where you can use the date range drop-down menu to view log messages received on or before the date one year ago.

This section also provides a link for quick access to the [Log Management Flat File Policy](../../../configure/log-management-flat-file-policy.md) configuration in the Log Management page.

### Control Reference 09.ab (Level 1 Implementation Requirements)

Compliance with Control Reference 09.ab Monitoring System Use requires your organization to comply complies with all relevant legal requirements applicable to its monitoring activities. Items that are monitored include:

* authorized access
* unauthorized access attempts

This section provides links to the Log Review Summary page and the Log Review Incidents page.

#### Log Review Summary 

The Log Review Summary page provides the daily distribution of log incidents reviewed by Alert Logic analysts. You can use the information on this page to demonstrate that the daily log review process includes manual review of audit logs and access changes.

You can also click the link for quick access to the Log Review incidents in the Alert Logic console where you can search for and view the details of the incidents.

To generate this report, from the Summary page, click **Log Review Summary page**. To refine your findings, you can filter this page by date range, and customer account.

##### Status section

This section provides the status counts and percentages of total login incidents that the Alert Logic Security Operations Center (SOC) analysts closed and escalated for the selected period.

![](../../../Resources/Images/Reports/Monthly-log-review/status.png)

##### Log Review Incidents by Day and Status section

This section provides a stacked histogram chart that displays the daily status counts  of total login incidents that the SOC analysts closed and escalated for the selected period.

![](../../../Resources/Images/Reports/Monthly-log-review/incidents-by-day-and-status.png)

##### Log Review Incident Summary Totals section

This section displays the total, escalated, and closed login incident counts for each type of log review summary category for the selected period.

For more information about the incidents during the selected period, click the **Monthly Log Review Report** to be redirected to the Monthly Log Review report. To learn more about the Monthly Log Review report, see [Monthly Log Review Report](../threats/log-review-analysis/monthly-log-review.md).

![](../../../Resources/Images/Reports/pci-requirement-10.6-incidents/log-review-incidents-summary-totals.png)

#### Log Review Incidents page

The Log Review Incidents page provides the daily distribution of log in incidents reviewed by Alert Logic analysts. You can use the information on this page to demonstrate that the daily audit log review process includes manual review of security events.

You can also click the link for quick access to the Log Review incidents in the Alert Logic console where you can search for and view the details of the incidents.

To generate this report, from the Summary page, click **Log Review Incidents page**. To refine your findings, you can filter this page by date range, and customer account.

##### Incident Count by Day section

#### Incident Count by Day section

This section provides the daily incident count and the total count for  the selected period.

![](../../../Resources/Images/Reports/PCI-requirement-11.4/incident-count-by-day.png)

##### List of Incidents section

#### List of Incidents section

The list displays Log Review incidents for the selected filters. The list is organized by customer account, date created, detection source, incident ID, and summary.

Click **Search Incidents** to be redirected to the Incidents Lists page, which contains more information about the incidents in the selected period.

![](../../../Resources/Images/Reports/pci-requirement-10.6-incidents/list-of-incidents-log-review.png)

### Control Reference 09.ac (Level 1 Implementation Requirements)

Compliance with Control Reference 09.ac Protection of Log Information requires you to demonstrate that access to system audit tools and audit trails is safeguarded from unauthorized access and use to prevent misuse or compromise of logs.

This section  provides you with a link to the Alert Logic [Log Search](../../log-message-search.md) page where you can search logs for message types related to invalid access attempts. You can use this information  to  demonstrate that log data is protected against tampering and unauthorized access.

The report page includes a link to an Alert Logic Knowledge Base article that contains the recommended log search statements you can use on the Alert Logic Log Search page. You can use the log search statements to gather the supporting documentation that illustrates compliance with Control Reference 09.ac Protection of Log Information.

### Control Reference 09.ad (Level 1 Implementation Requirements)

Compliance with Control Reference 09.ad Administrator and Operator Logs requires you to demonstrate that your organization ensures that proper logging is enabled in order to audit administrator activities. System administrator and operator logs are reviewed on a regular basis.

This section  provides you with a link to the Alert Logic [Log Search](../../log-message-search.md) page where you can search logs for message types related to changing user accounts with root or administrative privileges. You can use this information  to  demonstrate that activity is logged and regularly reviewed.

The report page includes a link to an Alert Logic Knowledge Base article that contains the recommended log search statements you can use on the Alert Logic Log Search page. You can use the log search statements to gather the supporting documentation that illustrates compliance with Control Reference 09.ad Administrator and Operator Logs.

### Control Reference 09.ae (Level 1 Implementation Requirements)

Compliance with Control Reference 09.ae Fault Logging requires you yo to demonstrate that faults are reported by users or by system programs related relatd to problems with information processing or communications systems are logged. There are clear Clear rules for handling reported faults are outlined in the HITRUST Risk Management Framework.

This section provides you with a link for quick access to a list of users in the Alert Logic console that are subscribed to receive health status alerts including network coverage, collection issues, and host with no agent.
