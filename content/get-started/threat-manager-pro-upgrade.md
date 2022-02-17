# Threat Manager Professional Upgrade

Alert Logic Threat Manager Professional combines a cloud-based network intrusion detection system and a vulnerability assessment solution into a service that works in any environment, from on-premises to the cloud. Threat Manager customers who choose to upgrade to Threat Manager Professional  receive a number of changes that simplify and improve your experience.

The Alert Logic console shows only the tabs and pages appropriate to your product subscription. This topic describes all possible tabs and pages, but specifies the subscriptions that generate the tabs and pages.  For more information about subscriptions Alert Logic offers, see [Get Started with Alert Logic   Subscriptions and Add-ons](subscriptions-addons.md).

## Requirements

Your existing appliances, agents, and deployments from Threat Manager are migrated to Threat Manager Professional, and your historical data is available. You are not required to perform any updates, although Alert Logic recommends you use the latest deployment and agent updates:

* If you have Amazon Web Services (AWS) deployments, you must ensure your deployments use IAM roles created with the most current policy documents. To update IAM roles, see [Update your IAM roles](../prepare/aws-cross-account-role-setup.md#update-roles).
* If you have Azure deployments, you must ensure your Microsoft Azure resources are configured to allow Alert Logic to discover and monitor your assets. To ensure your Azure deployments are properly configured, see [Configure App Registration and RBAC for Microsoft Azure Resources](../prepare/azure-rbac-role-setup.md).
* Upgrade your agents and appliances to the most recent version. Download and install the appropriate agents or appliances. For more information, see the following documents:
   * [Install the Alert Logic Agent for Linux](../prepare/alert-logic-agent-linux.md)
   * [Install the Alert Logic Agent for Windows](../prepare/alert-logic-agent-windows.md)
   * [Install and Configure the  Virtual Appliance](../prepare/virtual-appliance.md)

## How to find features in the new console

Alert Logic has improved, replaced, and moved several features in the Alert Logic console. See the table below for major changes:

| Legacy Functionality Name | Upgraded Functionality  |
|---|---|
| Alert Logic console | (Optional) [Managed Detection and Response Navigation Menu Updates](../analyze/dashboard/navigation.md#navigat) |
| Summary and Dashboards | Available as [Threat Risk Index Summary](../analyze/dashboard/tri-summary.md), [TM Professional Entitlement Summary](../analyze/reports/service/entitlement/tm-pro-entitlement-summary.md#Enterpri), and the new [Dashboards](../analyze/dashboards.md). |
| Scans | [Manage Scans and Scan Results](../analyze/manage-scans-and-scan-results.md#Manage2) |
| Hosts, Networks, Protected Hosts, and Network IDS | [Topology](../analyze/topology.md), [Get Started with Alert Logic Deployments](deployments.md), [Health](../analyze/health.md) |
| Alert Rules | [Notifications](../configure/notifications.md#manage-health-notifications) |
| Remediations | [Exposures](../analyze/exposures.md) |

## Automated functionality

The new Alert Logic console offers automation of traditional features that you previously had to manually configure when your deployments are upgraded to the Threat Manager Professional. Automation of features also applies if you need to create a new deployment. Alert Logic has automated the following functionality:

* Browse Devices
* Legacy Threat Manager appliances
* Assignment policies
* Monitoring policies
* Blocking configuration

### Upgraded scanning features

The  upgrade provides feature parity for scan frequency and simple scan scheduling. Upgrades affect:

* Collection capability
* Scanning capability
* Scan scheduling
* PCI scanning

To learn more about upgrade details of scanning capabilities and scheduling, see [Scan Functionality Upgrade](scans-upgrade.md).

## About Threat Manager Professional capabilities

In the Alert Logic console, your  subscription provides visibility to assets and vulnerabilities across your environments through the following capabilities:

* [Threat Risk Index Summary](../analyze/dashboard/tri-summary.md): This dashboard provides insights into the recent TRI scores of your environment, including the average TRI score and trends, vulnerabilities changes, last scanned asset changes, and TRI scores by assets.
* (Optional) [Dashboards](#Dashboards): This is a new feature that presents interactive visuals that present data regarding the state of your environment and  track existing issues if you chose to use the new Dashboards.
* [Deployments](#Deployments): A defined set of assets that you want to monitor and protect in your cloud-based or physical data centers.
* [Scan frequency and scheduling](#scheduling): A schedule for how often and when you want Alert Logic to perform scans for each deployment.
* [Topology](#Topology): An interactive diagram that  displays your deployments and the distribution of exposures and threats across your assets.
* [Health](#Health): A summary of the state of your deployments, including detailed information on your configuration assets.
* [Exposures](#Exposures): Security and configuration exposures found in your environment, and remediation support for those exposures.
* [Reports](#reports): Data related to exposures, risks, and compliance status, which you can share and download.
* [PCI Scanning](#PCI-Scanning): Payment Card Industry (PCI) scanning, and Approved Scanning Vendor (ASV) support and disputing.
* [Vulnerability Library](#Library): List of scan content that Alert Logic checks, where you can search and view information for specific vulnerabilities.
* [Management settings](#settings): Your user account, notifications, and integrations settings.
* [Service Status](#Status): Page for monitoring the status of your subscribed region and product capabilities.

### Dashboards

Dashboards presents pertinent information that feeds from live data in your environment. You can click most items in visuals  to view the source of the data, which redirects to the corresponding page in the Alert Logic console. This allows you to drill down further into issues and streamline your response actions. For more details about Dashboards, see [Dashboards](../analyze/dashboards.md).

#### Alert Logic console navigation menu from Dashboards

If you chose to use the new Dashboards, you can easily navigate through the Alert Logic console from the Dashboards page. For more detailed information, see [Managed Detection and Response Navigation Menu Updates](../analyze/dashboard/navigation.md#Navigation).

**To start navigating to pages in the Alert Logic console**:

1. Click the menu icon (![](../Resources/Images/dashboard/menu-icon.png)) to see the navigation menu.
2. Click a navigation group (for example, **Respond**) to expand the options under that group.
3. Click a navigation item (for example, **Incidents**) that you want to explore further.

### Deployments

Deployments allows you to monitor and protect a defined set of assets, including your appliances, agents, hosts, and collectors in your environments. You can create deployments for assets found in your Amazon Web Services (AWS), Microsoft Azure, and other cloud-based or physical data centers. You can also configure Alert Logic product use. For more information about deployments, see [Get Started with Alert Logic Deployments](deployments.md).

#### Scan frequency and scheduling

From your deployments, and depending on your deployment type, you can configure your scan scheduling and frequency for discovery scans and vulnerability scans, and you can exclude assets from for scanning. For more information about scans, see [Manage Scans and Scan Results](../analyze/manage-scans-and-scan-results.md#Manage2).

### Topology

You can view your deployment networks, and all its assets, in an interactive diagram from the Topology page. You can customize and filter the what assets you want to see, and you can view asset details, take action on remediations, manage your credentials, and expedite scans for specific assets. For more information, see [Topology](../analyze/topology.md).

### Health

The Health page provides a summary of you deployments to ensure that your deployments are correctly configured by providing the following:

* Summary of your environment
* Detailed health information regarding your networks, appliances, and agents
* Suggested configuration remediations
* Option to subscribe to health summary alerts

For more information about the Health page, see [Health](../analyze/health.md).

### Exposures

The Exposures page displays the number and types of security and configuration exposures in your protected deployment, and it provides you with information about the exposure, including color-coded threat level, evidence, and recommendations to address the exposure. For more details about the Exposures page, see [Exposures](../analyze/exposures.md).

### Reports

The Reports page provides access to data related to exposures, risks, and compliance status that Alert Logic assessed within your environment. Each report provides interactive filtering options, visual representations of the data, and informative tooltips. As a result, reports can take up to 30 minutes to reflect the latest data seen in the console.

The Threat Manager Professional subscription include the following report types:

* Risk— Includes [Reports Guide](../analyze/reports/reports.md#EnterpriseRisk) reports which provides valuable insights and analysis of your incidents, events, and vulnerabilities. You can evaluate threats and incidents and your response efforts, validate events and focus your efforts, and gain insights into the effectiveness of your vulnerability management.
* Threats— Includes [Incident Analysis](../analyze/reports/reports.md#incidentAnalysis) and [Reports Guide](../analyze/reports/reports.md#EventAnalysis) reports which provide convenient access to analysis, statistics, assessments, and trending data related to threats and incidents detected from your subscribed products and services.
* Vulnerabilities—Includes [Vulnerability Analysis](../analyze/reports/reports.md#vulnerabilityAnalysis), [                Vulnerability Analysis - Full Reports](../analyze/reports/reports.md#vulnerabilityanalysisfullreport), and [Reports Guide](../analyze/reports/reports.md#CurrentVulnerabilityFinder) reports which provide convenient access to analysis, statistics, assessments, and trending data related to vulnerabilities discovered in your environment based on scanning outcomes.
* Remediations— Includes [Reports Guide](../analyze/reports/reports.md#ConfigurationRemediations) and [Reports Guide](../analyze/reports/reports.md#SecurityRemediations) reports which provide convenient access to analysis, statistics, assessments, and trending data related to configuration issues and security exposures from your subscribed products and services.
* Compliance—Includes [Reports Guide](../analyze/reports/reports.md#PCIDSSAudit) and [Reports Guide](../analyze/reports/reports.md#HIPAAHITECHSecurityAudit) reports which provide convenient access to analysis, statistics, and trending data related to compliance assessment status and audit preparedness from your subscribed products and services.
* Service— Includes [TM Professional Entitlement Summary](../analyze/reports/service/entitlement/tm-pro-entitlement-summary.md), [Reports Guide](../analyze/reports/reports.md#CapabilityUsage), [Health](#Health), and [Users](../analyze/reports/reports.md#Users) reports which provide convenient access to data related to entitlements, capability usage, users and security content for your subscribed products and services.

### PCI Scanning

You can schedule  external scans that are required for PCI compliance. You can quickly and easily view the results of those scans. If you need to dispute scan results, and resolve vulnerabilities to prove compliance to auditor, you can use the PCI Scans Disputes page. To learn how to schedule and manage PCI scans, see  [Manage PCI Scans](../configure/pci-scans.md). To learn how to dispute PCI scan report findings, see [PCI Scan Disputes](../configure/pci-scan-dispute.md).

### Vulnerability Library

Alert Logic lists all of the scan content that Alert Logic scanners can check in the Vulnerability Library. You can easily search for and view information on a specified vulnerability Alert Logic scanned for and see whether it impacts assets in your environment. To learn more about the Alert Logic Vulnerability Library, see [Vulnerability Library](../analyze/vulnerability-library.md).

### Management settings

You can manage user account settings, such as your name, contact information, and password. To learn more about how to manage user settings, see [User settings](../prepare/manage-user-account.md).

You can also configure and manage notifications to keep you informed about the health of your account and the accounts you manage. If your user account has the Administrator role, you can manage the notifications for users in your customer account and accounts you manage. To learn more about notifications, see [Notifications](../configure/notifications.md).

Alert Logic integrations allow you to extend Alert Logic into AWS Inspector and AWS Config Rules, configure Custom Checks as inputs to Alert Logic, and even integrate with the Atlassian JIRA ticketing system.

### Service Status

The Service Status page provides updates for incidents in progress, including the overall status of Alert Logic regions and products, statuses for individual product capabilities, and details about past incidents. You can also subscribe to notifications when Alert Logic creates, updates, or resolves a service incident. To learn more about the Service Status page, see [Service Status](../analyze/service-status.md).
