# SOC 2 Common Criteria 7.2 Security Event and Anomaly Detection

The SOC 2 Audit Reports provide documentation to help demonstrate compliance with the Trust Services Criteria established  by the American Institute of Certified Public Accountants (AICPA). The SOC 2 CC7.2 Security Event and Anomaly Detection report describes how to access security event and threat response reporting features in the Alert Logic console that help demonstrate compliance with Common Criteria (CC) 7.2.

**To access the SOC 2 CC7.2 Security Event and Anomaly Detection report:**

1. In the Alert Logic console, click the menu icon (![](../../../Resources/Images/dashboard/menu-icon.png)), and then click ![](../../../Resources/Images/dashboard/validate-icon.png)**Validate**.
2. Click **Reports**, and then click **Compliance**.
3. Under **SOC 2 Audit**, click **VIEW**.
4. Click **SOC 2 CC7.2 Security Event and Anomaly Detection**.

## Filter the report

To refine your findings, you can filter your report by  date range and customer account.

### Filter the report using drop-down menus

By default, Alert Logic includes **(All)** filter values in the report.

**To add or remove filter values: **

1. Click the drop-down menu in the filter, and then select or clear values.
2. Click **Apply**.

The report summary page displays two columns. **Points of Focus** lists points of focus, specifically related to all engagements using the trust services criteria, that highlight important characteristics relating to CC7.2. **Available Documentation and Artifacts** describes, and contains links to, the documentation and compliance artifacts that can demonstrate compliance with each point of focus.

## Available Documentation and Artifacts

This report provides access to features  in the Alert Logic console that help you demonstrate  compliance with CC7.2. You have direct access to reports related to security anomalies and data for security events that were detected across your environment. This report also provides access to monitored network traffic for security events, and monitored logs and network traffic for security events in the Health page.

This criteria requires that the entity monitors system components and the operation of those components for anomalies that are indicative of malicious acts, natural disasters, and errors affecting the entity's ability to meet its objectives; anomalies are analyzed to determine whether they represent security events.

## Implements Detection Policies, Procedures, and Tools 

Implements Detection Policies, Procedures, and Tools point of focus requires you to demonstrate that detection policies and procedures are defined and implemented and detection tools are implemented on infrastructure and software to identify anomalies in the operation or unusual activity on systems. Procedures may include (1) a defined governance process for security event detection and management that includes provision of resources; (2) use of intelligence sources to identify newly discovered threats and vulnerabilities; and (3) logging of unusual system activities.

Alert Logic does not provide data for this point of focus. You must provide the policy and procedure documents for this audit.

## Designs Detection Measures 

The Designs Detection Measures point of focus requires you to demonstrate that detection measures are designed to identify anomalies that could result from actual or attempted (1) compromise of physical barriers; (2) unauthorized actions of authorized personnel; (3) use of compromised identification and authentication credentials; (4) unauthorized access from outside the system boundaries; (5) compromise of authorized external parties; and (6) implementation or connection of unauthorized hardware and software.

Alert Logic does not provide data for this point of focus. You must provide the policy and procedure documents for this audit.

## Implements Filters to Analyze Anomalies

The Implements Filters to Analyze Anomalies point of focus requires you to demonstrate that management has implemented procedures to filter, summarize, and analyze anomalies to identify security events.

This section provides you with a link for quick access to the Log Anomaly Analysis reports  in the Alert Logic console where you can review security anomalies detected from monitored logs across your environment.

This section also provides  you with a link for quick access to the [Event Analysis](../threats/reports.md#Event) in the Alert Logic console where you can review summary, distribution and trending data for security events detected from monitored logs across your environment.

## Monitors Detection Tools for Effective Operation

The Monitors Detection Tools for Effective Operation point of focus requires you to demonstrate that management has implemented processes to monitor the effectiveness of detection tools.

This section provides you with a link for quick access to the Unhealthy Appliance section of the [Health](../../health.md) page in the Alert Logic console where you can view the appliances used to monitor network traffic for security events.

This section also provides  you with a link for quick access to the Unhealthy Agents section page of the [Health](../../health.md) page  in the Alert Logic console where you can view agents used to monitor logs and network traffic for security events.
