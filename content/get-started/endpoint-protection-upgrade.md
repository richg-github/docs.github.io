# Alert Logic Extended Endpoint Protection Upgrade

Alert Logic is upgrading Barkly customers to the full, robust Alert Logic Essentials subscription. This includes a number of changes to your experience. The Essentials subscription, in addition to the Extended Endpoint Protection, offers other capabilities and functionality you can use in the Alert Logic console. For more information about Alert Logic subscriptions, see [Get Started with Alert Logic   Subscriptions and Add-ons](subscriptions-addons.md).

## Extended Endpoint Protection changes

Your new experience includes all of the same capabilities as the current Extended Endpoint Protection, including new and improved features. If you want a reminder of the Extended Endpoint Protection features, see [About Alert Logic Extended Endpoint Protection](about-extended-endpoint-protection.md).

Some of the current tabs have minor name changes:

| Tab name | New tab name |
| Status | Summary |
| Scans | Overrides |
| Incidents | Events |
| Settings | Options |

### Added features

Extended Endpoint Protection now includes a few added and improved features with your Alert Logic Essentials upgrade:

* Option to mark an endpoint as a virtual desktop infrastructure (VDI) master image. For more information, see [Virtual Desktop Infrastructure Environments](../deploy/vdi.md).
* Automatic detection of proxy configuration, instead of manual configuration of your proxy
* Improved detection capabilities, which reduce false positives with an automated, real-time file reputation lookup
* Support for MacOS

## Network change requirements

Although no system requirement changes are necessary to upgrade to Alert Logic Essentials subscription, you must make network changes for your endpoints to communicate with Alert Logic. You must update your TCP connections to specific domains via defined ports. To see the endpoint TCP connection requirements, see [Communication with Alert Logic](../requirements/endpoint-requirements.md#communication).

## About Essentials capabilities

In the Alert Logic console, the Essentials subscription provides visibility to assets and vulnerabilities across your environments through the following capabilities:

* [Dashboards](#Dashboards): Interactive visuals that present data regarding the state of your environment and  track existing issues.
* [Deployments](#Deployments): A defined set of assets that you want to monitor and protect in your cloud-based or physical data centers.
* [Scan frequency and scheduling](#scheduling): A schedule for how often and when you want Alert Logic to perform scans for each deployment.
* [Topology](#Topology): An interactive diagram that  displays your deployments and the distribution of exposures and threats across your assets.
* [Health](#Health): Connection and configuration status for assets in your environment, and remediation support for health exposures.
* [Exposures](#Exposures): Security exposures found in your environment, and remediation support for those exposures.
* [Reports](#reports): Data related to exposures, risks, and compliance status, which you can share and download.
* [PCI Scanning](#PCI-Scanning): Payment Card Industry (PCI) scanning, and Approved Scanning Vendor (ASV) support and disputing.
* [Vulnerability Library](#Library): List of scan content that Alert Logic checks, where you can search and view information for specific vulnerabilities.
* [Management settings](#settings): Your user account, notifications, and integrations settings.
* [Service Status](#Status): Page for monitoring the status of your subscribed region and product capabilities.

### Dashboards

Dashboards present pertinent information that feeds from live data in your environment. You can click most items in visuals  to view the source of the data, which redirects to the corresponding page in the Alert Logic console. This allows you to drill down further into issues and streamline your response actions. For more details about Dashboards, see [Dashboards](../analyze/dashboards.md).

### Deployments

Deployments allows you to monitor and protect a defined set of assets, including your appliances, agents, hosts, and collectors in your environments. You can create deployments for assets found in your Amazon Web Services (AWS), Microsoft Azure, and other cloud-based or physical data centers. You can also configure Alert Logic product use. For more information about deployments, see [Get Started with Alert Logic Deployments](deployments.md).

#### Scan frequency and scheduling

From your deployments, and depending on your deployment type, you can configure your scan scheduling and frequency for discovery scans and vulnerability scans, and you can exclude assets for scanning. For more information about scans, see [Manage Scan Schedules](../analyze/manage-scans-and-results/schedules.md).

### Topology

You can view your deployment networks, and all its assets, in an interactive diagram from the Topology page. You can customize and filter what assets you want to see, and you can view asset details, take action on remediations, manage your credentials, and expedite scans for specific assets. For more information, see [Topology](../analyze/topology.md).

### Health

The Health page  provides detailed information about your environment to ensure that your deployments are configured correctly. Health exposures result from configuration or connection problems that disrupt access to  Alert Logic product capabilities.

The Health page displays the number and types of connection or configuration exposures in your protected deployment, and it provides you with information about the exposure, including severity, evidence, and recommendations to address the exposure. For more information about the Health page, see [Health](../analyze/health.md).

### Exposures

The Exposures page displays the number and types of security exposures in your protected deployment, and it provides you with information about the exposure, including color-coded threat level, evidence, and recommendations to address the exposure. For more details about the Exposures page, see [Exposures](../analyze/exposures.md).

### Reports

The Reports page provides access to data related to exposures, risks, and compliance status that Alert Logic assessed within your environment. Each report provides interactive filtering options, visual representations of the data, and informative tooltips. As a result, reports can take up to 30 minutes to reflect the latest data seen in the console. To learn more about the Reports page, see [Reports Guide](../analyze/reports/reports.md).

The Essentials subscription include the following report types:

* [Risk Reports](../analyze/reports/reports.md#Risk-reports)—Provide convenient access to analysis, statistics, assessments, and trending data related to your security and health posture, threat risk index, and enterprise risks.
* [Vulnerabilities Reports](../analyze/reports/reports.md#Vulnerability-reports)—Provide convenient access to analysis, statistics, assessments, and trending data related to vulnerabilities discovered in your environment based on scanning outcomes.
* [Remediations Reports](../analyze/reports/reports.md#Remediations-reports)—Provide convenient access to analysis, statistics, assessments, and trending data related to configuration issues and security exposures from your subscribed products and services.
* [Compliance Reports](../analyze/reports/reports.md#Compliance-reports)—Provide convenient access to analysis, statistics, and trending data related to compliance assessment status and audit preparedness from your subscribed products and services.

### PCI Scanning

You can schedule  external scans that are required for PCI compliance. You can quickly and easily view the results of those scans. If you need to dispute scan results, and resolve vulnerabilities to prove compliance to auditor, you can use the PCI Scans Disputes page. To learn how to schedule and manage PCI scans, see  [Manage PCI Scans](../configure/pci-scans.md). To learn how to dispute PCI scan report findings, see [PCI Scan Disputes](../configure/pci-scan-dispute.md).

### Vulnerability Library

Alert Logic lists all of the scan content that Alert Logic scanners can check in the Vulnerability Library. You can easily search for and view information on a specified vulnerability Alert Logic scanned for and see whether it impacts assets in your environment. To learn more about the Alert Logic Vulnerability Library, see [Vulnerability Library](../analyze/vulnerability-library.md)

### Management settings

You can manage user account settings, such as your name, contact information, and password. To learn more about how to manage user settings, see [User settings](../prepare/manage-user-account.md).

You can also configure and manage notifications to keep you informed about the health of your account and the accounts you manage. If your user account has the Administrator role, you can manage the notifications for users in your customer account and accounts you manage. To learn more about notifications, see [Notifications](../configure/notifications.md).

Alert Logic integrations allow you to extend Alert Logic into AWS Inspector andAWS Config Rules, configure Custom Checks as inputs to Alert Logic, and even integrate with the Atlassian Jira ticketing system.

### Service Status

The Service Status page provides updates for incidents in progress, including the overall status of Alert Logic regions and products, statuses for individual product capabilities, and details about past incidents. You can also subscribe to notifications when Alert Logic creates, updates, or resolves a service incident. To learn more about the Service Status page, see [Service Status](../analyze/service-status.md).

## Alert Logic console navigation menu

**To start navigating to pages in the Alert Logic console**:

1. Click the menu icon (![](../Resources/Images/dashboard/menu-icon.png)) to see the navigation menu.
2. Click a navigation group (for example, ![](../Resources/Images/dashboard/respond-icon.png)**Respond**) to expand the options under that group.
3. Click a navigation item (for example, **Incidents**) that you want to explore further.

See the table below for the tab, pages, and functionality available to you in the Alert Logic console:

| **![](../Resources/Images/dashboard/dashboard-icon.png) Dashboards** | [Dashboards](../analyze/dashboards.md) |
| ![](../Resources/Images/dashboard/respond-icon.png) Respond |  |
| Exposures | [Exposures](../analyze/exposures.md) |
| Health | [Health](../analyze/health.md) |
| ![](../Resources/Images/dashboard/investigate-icon.png) Investigate |  |
| Topology | [Topology](../analyze/topology.md) |
| Vulnerability Library | [Vulnerability Library](../analyze/vulnerability-library.md) |
| ![](../Resources/Images/dashboard/validate-icon.png) Validate |  |
| Reports | [Reports](../analyze/reports/reports.md) |
| PCI Scan Disputes | [PCI Scan Disputes](../configure/pci-scan-dispute.md) |
| ![](../Resources/Images/dashboard/configure-icon.png)**Configure** |  |
| Deployments | [Deployments](deployments.md) |
| Endpoints | [Extended Endpoint Protection](endpoint-protection.md) |
| PCI Scanning | [PCI Scanning](pci-scans.md) |
| ![](../Resources/Images/dashboard/manage-icon.png)              Manage |  |
| Integrations | Integrations |
| Users | [Users](../prepare/users-roles.md) |
| Notifications | [Notifications](../configure/notifications.md) |
| Service Status | [Service Status](../analyze/service-status.md) |
| ![](../Resources/Images/dashboard/support-icon.png)**Support** | Support information |
