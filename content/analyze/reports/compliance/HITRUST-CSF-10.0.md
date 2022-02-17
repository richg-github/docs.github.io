# HITRUST CSF 10.0 Information Systems Acquisition, Development, and Maintenance

The HITRUST Common Security Framework (CSF) reports provide available documentation and compliance artifacts that help you demonstrate compliance with HITRUST CSF control categories, as outlined in the HITRUST Risk Management Framework.

The HITRUST CSF 10.0 Information Systems Acquisition, Development, and Maintenance report  describes how to access web application protection and vulnerability management features in the Alert Logic console that help demonstrate compliance with Control Category 10.0.

**To access the HITRUST CSF 10.0 report:**

1. In the Alert Logic console, click the menu icon (![](../../../Resources/Images/dashboard/menu-icon.png)), and then click ![](../../../Resources/Images/dashboard/validate-icon.png)**Validate**.
2. Click **Reports**, and then click  **Compliance**.
3. Under **HITRUST CSF**, click **VIEW**.
4. Click **HITRUST CSF 10.0 Information Systems Acquisition, Development, and Maintenance**.

## Filter the report

To refine your findings, you can filter your report by  date range and customer account.

### Filter the report using drop-down menus

By default, Alert Logic includes **(All)** filter values in the report.

**To add or remove filter values: **

1. Click the drop-down menu in the filter, and then select or clear values.
2. Click **Apply**.

The report summary page displays two columns. **Control References** lists each procedure that is required  to meet the selected control objective. **Available Documentation and Artifacts** describes, and contains links to, the documentation and compliance artifacts that can demonstrate compliance with each control objective.

This report is composed of four pages, the **Summary** page, the **WAF** Deployment page, the **WAF**Traffic page, and the **WAF** Policy Violation page. Each page includes filters  to specify the scope of the information you need to collect.

## Available Documentation and Artifacts

This report provides access to features in the Alert Logic console that help you demonstrate  compliance with these control objectives in Control Category 10.0:

* 10.02 Correct Processing in Applications
* 10.06 Technical Vulnerability Management

## Control Objective 10.02 Correct Processing in Applications

This section of the report includes documentation and artifacts that help you demonstrate that you have  implemented procedures to ensure compliance with Control Objective 10.02 Correct Processing in Applications. This objective requires you to design controls into applications to ensure correct processing to prevent errors, loss, unauthorized modification, or misuse of information in applications.

### Control Reference 10.b (Level 1 Implementation Requirements)

Compliance with Control Reference 10.b Input Data Validation requires you to develop applications based on secure coding guidelines to prevent common coding vulnerabilities in software development processes as outlined in the HITRUST Risk Management Framework.

For web applications and application interfaces (internal or external), development must be based on secure coding guidelines to prevent vulnerabilities as outlined in the HITRUST Risk Management Framework.

Web-based applications must also be checked for the most current Open Web Application Security Project (OWASP) top 10 vulnerabilities related to input validation.

This report provides documentation and artifacts that help you demonstrate that the WAF is situated in front of your public-facing web applications to detect and prevent web-based attacks, is actively running and up to date, generates audit logs, and is configured to either block web-based attacks, or generate an alert that is immediately investigated.

### WAF Deployment page

The WAF Deployment page provides the list of protected websites. You can use the information on this page to demonstrate the WAF is configured to detect and protect your public-facing web applications.

To generate this report, from the Summary page, click WAF** Deployment page**. To refine your findings, you can filter this page by  customer account and appliance name.

#### Website Operating Mode section

This section displays the website operating mode in a color-coded pie chart in the selected filters. The graph presents the following operating modes:

* Pass: Requests are not blocked, and logging is not performed. This mode is primarily used during the onboarding phase and for troubleshooting.
* Detect: Default operating mode during the tuning phase. Violations to configured policy rules are only logged.
* Protect: Violations to configured policy rules will be blocked and logged.

![](../../../Resources/Images/Reports/PCI-6.6/website-operating-mode.jpg)

#### Proxy Certificates section

This section provides the proxy certificate statuses in a color-coded pie chart for the selected period. The graph presents the following proxy certificate statuses:

* Valid
* Expires in less than six months
* Expires soon
* Expired

![](../../../Resources/Images/Reports/PCI-6.6/proxy-certifcate.jpg)

#### Website List section

The list displays the websites protected by the WAF appliances in your environment for the selected period. The list is organized by customer name, proxy vhost, appliance name, proxy mode, and proxy certificate status.

![](../../../Resources/Images/Reports/PCI-6.6/website-list.jpg)

### WAF Traffic page

The WAF Traffic page of this report provides the daily web traffic statistics. You can use the information on this page to demonstrate the WAF is actively processing requests and traffic in front of your web applications.

To generate this report, from the Summary page, click WAF** Traffic page**. To refine your findings, you can filter this page by date range, customer account, appliance name, and measuring unit.

#### WAF Traffic by Day section

The bar graph displays the daily WAF traffic volume in the selected filters. You can view the data measured  by request or data size (in MB). Click the **Measure by** drop-down, and then select how you want the data measured.

![](../../../Resources/Images/Reports/WAF Traffic/WafTrafficbyDay2.png "")

#### Appliance List section

The list displays the daily traffic volume by request and megabytes processed by the WAF appliances in your environment for the selected period. The list is organized by date, customer name, appliance name, traffic requests, and traffic (in MB).

![](../../../Resources/Images/Reports/WAF Traffic/ApplianceList.png)

### WAF Policy Violations page

The WAF Policy Violations page of this report provides the daily distribution of WAF policy violations. You can use the information on this page to demonstrate the WAF is configured to detect and block web-based attacks.

To generate this report, from the Summary page, click **WAF Policy Violations page**. To refine your findings, you can filter this page by  date range and customer account.

#### Violations by Day section

The bar graph presents the daily WAF policy violation count for all the protected websites in the selected filters.

![](../../../Resources/Images/Reports/WAF Violation Explorer/violationsbyday.png)

#### Violations by Operating Mode section

This section displays WAF policy violations by operating mode in a color-coded pie chart in the selected filters. The graph presents the following operating modes:

* Pass: Requests are not blocked, and logging is not performed. This mode is primarily used during the onboarding phase and troubleshooting.
* Detect: Default operating mode during the tuning phase. Violations to configured policy rules are only logged.
* Block:	Violations to configured policy rules will be blocked and logged.

![](../../../Resources/Images/Reports/WAF Violation Explorer/ViolationbyOperatingMode.png)

####  Violations by Risk Level section

This section displays the WAF policy violations by risk level presented in a color-coded pie chart in the selected filters. The risk levels are the following:

* Critical: Could represent a successful attack or breach
* High: Requires immediate attention
* Medium: Recommended observation and monitoring
* Low: Common violations and events
* None:           No risk detected

![](../../../Resources/Images/Reports/WAF Violation Explorer/ViolationsbyRiskLevel.png)

#### Violations by Attack Class section

The list displays the WAF policy violations by attack class during the selected period. The list is organized by attack class, the total number of violations in each attack class, and the percentage of violations in each attack class, along with a color-coded bar that represents the size of violations in each attack class. Hover over the color-coded bar for more information about that attack class.

![](../../../Resources/Images/Reports/WAF Violation Explorer/violationsbyattackclass.png)

#### Violations by Violation Type section

The list displays the WAF policy violations by violation type during the selected period. The list is organized by violation type, the total number of that violation type, and the percentage of each violation type, along with a color-coded bar that represents the size of that violation type. Hover over the color-coded bar for more information about that violation type.

![](../../../Resources/Images/Reports/WAF Violation Explorer/ViolationsbyViolationType.png)

## Control Objective 10.06 Technical Vulnerability Management

This section of the report includes documentation and artifacts that help you demonstrate that you have  implemented procedures to ensure compliance with Control Objective 10.06 Technical Vulnerability Management. To reduce the risks resulting from exploitation of published technical vulnerabilities, Control Objective 10.06 requires implementation of technical vulnerability management in an effective, systematic, and repeatable way with measurements taken.

### Control Reference 10.m  (Level 1 Implementation Requirements)

Compliance with Control Reference 10.m Control of Technical Vulnerabilities  requires you to gather specific information needed to support technical vulnerability management, including the software vendor, version numbers, current state of deployment (for example, what software is installed on what systems), and the person(s) within the organization responsible for the software.

Appropriate, timely action must be taken in response to the identification of potential technical vulnerabilities. Once a potential technical vulnerability is identified, the organization must identify the associated risks and the actions to be taken. These actions involve patching of vulnerable systems and/or applying other controls.

This report section provides you with the following links for quick access to appropriate pages in the Alert Logic console that illustrate compliance with procedures in Control Reference 10.m:

* Protection configuration settings in the [Deployments page](../../../get-started/deployments.md) to review the vulnerability scan schedule for the deployment in your environment.
* Vulnerability assessment findings in the [Vulnerabilities group of the Reports page](../reports.md#Vulnerability-reports) to review quarterly interval vulnerability scan results across your environment.
* PCI Scanning feature in the [PCI Scanning page](../../../get-started/pci-scans.md) to review the latest 25 external vulnerability scan reports for the most recent 12-month period.
