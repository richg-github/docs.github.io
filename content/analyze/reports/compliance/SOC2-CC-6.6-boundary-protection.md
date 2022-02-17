# SOC 2 Common Criteria 6.6 Boundary Protection

The SOC 2 Audit Reports provide documentation to help demonstrate compliance with the Trust Services Criteria established  by the American Institute of Certified Public Accountants (AICPA). The SOC 2 CC6.6 Boundary Protection report describes how to  use and access threat detection, scanning, and web application protection features in the Alert Logic console that help demonstrate compliance with Common Criteria (CC) 6.6.

**To access the SOC 2 CC6.6 Boundary Protection report:**

1. In the Alert Logic console, click the menu icon (![](../../../Resources/Images/dashboard/menu-icon.png)), and then click ![](../../../Resources/Images/dashboard/validate-icon.png)**Validate**.
2. Click **Reports**, and then click **Compliance**.
3. Under **SOC 2 Audit**, click **VIEW**.
4. Click ** SOC 2 CC6.6 Boundary Protection**.

## Filter the report

To refine your findings, you can filter your report by  date range and customer account.

### Filter the report using drop-down menus

By default, Alert Logic includes **(All)** filter values in the report.

**To add or remove filter values: **

1. Click the drop-down menu in the filter, and then select or clear values.
2. Click **Apply**.

The report summary page displays two columns. **Points of Focus** lists points of focus, specifically related to all engagements using the trust services criteria, that highlight important characteristics relating to CC6.6. **Available Documentation and Artifacts** describes, and contains links to, the documentation and compliance artifacts that can demonstrate compliance with each point of focus.

## Available Documentation and Artifacts

This report provides access to your monitored networks, Network IDS coverage for each deployment, vulnerability scan schedule, PCI scanning reports, and the WAF deployment page that help you demonstrate  compliance with CC6.6. This criteria requires the entity to demonstrate that logical access security measures are implemented to protect against threats from sources outside its system boundaries.

## Restricts Access 

The Restricts Access point of focus requires you to demonstrate that the types of activities that can occur through a communication channel (for example, FTP site, router port) are restricted.

Alert Logic does not provide data for this point of focus. You must provide the policy and procedure documents for this audit.

## Protects Identification and Authentication Credentials 

The Protects Identification and Authentication Credentials point of focus requires you to demonstrate that identification and authentication credentials are protected during transmission outside its system boundaries.

Alert Logic does not provide data for this point of focus. You must provide the policy and procedure documents for this audit.

## Requires Additional Authentication or Credentials

The Requires Additional Authentication or Credentials point of focus requires you to demonstrate that additional authentication information or credentials are required when accessing the system from outside its boundaries.

Alert Logic does not provide data for this point of focus. You must provide the policy and procedure documents for this audit.

## Implements Boundary Protection Systems 

The Implements Boundary Protection Systems point of focus requires you to demonstrate that boundary protection systems (for example, firewalls, demilitarized zones, and intrusion detection systems) are implemented to protect external access points from attempts and unauthorized access and are monitored to detect such attempts.

This section provides you with the following links for quick access to appropriate pages in the Alert Logic console:

* Networks monitored in your environment by the Network IDS in the [Health](../../health.md) page.
* Network IDS coverage for each deployment in the Scope of Protection topology diagram in the [Get Started with Alert Logic Deployments](../../../get-started/deployments.md) page.
* Vulnerability scan schedules for each deployment in your environment in the [Get Started with Alert Logic Deployments](../../../get-started/deployments.md) page. For more information about scan scheduling, see [Manage Scans and Scan Results](../../manage-scans-and-scan-results.md).
* [PCI scanning page](../../../configure/pci-scans.md)  to review the latest 25 internal vulnerability scan reports for the most recent 12-month period.
* Websites protected by Alert Logic Managed Web Application Firewall (WAF) in the [WAF websites](../../../configure/inline-waf/basics.md#searchAndWorkWebsites) page.
