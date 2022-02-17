# Get Started with Threat Manager Professional

Alert Logic Threat Manager Pro combines a cloud-based network intrusion detection system and a vulnerability assessment solution into a service that works in any environment, from on-premises to the cloud. For more information about Alert Logic subscriptions, see [Alert Logic Subscription Levels](subscription-levels.md). To learn more about your entitlements, see [TM Professional Entitlement Summary](../analyze/reports/service/entitlement/tm-pro-entitlement-summary.md).

## Review system and platform requirements

Before you get started, make sure all necessary parts of your environment are ready to be used with Alert LogicManaged Detection and Response. Review the [Operating System and Browser Requirements ](../requirements/operating-system-browsers.md).

You also must check your cloud platforms to make sure they meet instance size and throughput requirements:

* [Requirements for Managed Detection and Response for Amazon Web Services (AWS)](../requirements/amazon-web-services.md)
* [Requirements for Managed Detection and Response for Microsoft Azure](../requirements/microsoft-azure.md)
* [Requirements for Managed Detection and Response for Google Cloud Platform](../requirements/google-cloud.md)

## Alert Logic console navigation menu

The new navigation menu makes it easy to navigate through the Alert Logic console from the Dashboards page. For more detailed information, see [Managed Detection and Response Navigation Menu Updates](../analyze/dashboard/navigation.md#Navigation).

**To start navigating to pages in the Alert Logic console**:

1. Click the menu icon (![](../Resources/Images/dashboard/menu-icon.png)) to see the navigation menu.
2. Click a navigation group (for example, **Respond**) to expand the options under that group.
3. Click a navigation item (for example, **Incidents**) that you want to explore further.

## Deployment Creation Overview

The  general workflow for all deployment types is below. For more detailed information and deployment creation instructions for customers with Professional subscriptions, see the table below:

| Platform | Professional |
|---|---|
| AWS | [Amazon Web Services (AWS) Deployment Configuration—Automatic Mode (Professional Subscription)](../deploy/aws-auto-pro-ent.md) |
| [Amazon Web Services (AWS) Deployment Configuration—Manual Mode  (Professional Subscription)](../deploy/aws-manual-pro-ent.md) |
| Azure | [Microsoft Azure Deployment Configuration (Professional Subscription)](../deploy/azure-pro-ent.md) |
| Google Cloud Platform | [Data Center Deployment for Google Cloud Platform (Professional Subscription)](../deploy/google-cloud-pro-ent.md) |
| Oracle Cloud Platform | [Alert Logic Data Center Deployment for Oracle Cloud ](../deploy/oracle-cloud.md) |
| Data center/on-premesis | [Data Center Deployment Configuration (Professional Subscription)](../deploy/data-center-pro-ent.md) |

    To determine whether you should use an Automatic Mode or Manual Mode deployment creation procedure for an AWS Deployment, see [About  Deployment Types](about-deployment-types.md).    
When you create a deployment, the Alert Logic console prompts you through the following steps:

1. Configure   third-party access to cloud-based assets (AWS and Azure deployments only)
2. Assets
   * Discover assets (AWS and Azure deployments)
   * Add assets (Data Center deployments)
4. Define the scope of your protection
5. Schedule scans
6. Install appliances and agents
7. Update firewall rules and configure ports for scanning

### Provide Alert Logic third-party access

When you create an AWS or Azure deployment, you must grant Alert Logic access to your cloud environments for asset discovery and scanning. The access granted Alert Logic provides only the amount of access required to monitor the assets in your cloud environments.

### Asset discovery

After you grant Alert Logic access  to your cloud account or subscription, Alert Logic automatically discovers its assets. Alert Logic displays the assets discovered in your account in a visual topology diagram. To learn more about topology, see [Topology](../../../../analyze/topology.md).

If you have external-facing assets, you can add them by domain name or IP address.

### Add assets for Data Center deployments

For Data Center deployments, you must manually add the following assets

* Internal assets: Network and subnet
* External assets: Domain name or IP address

### Define your scope of protection

You can define the scope of your protection per network basis. Click a region or individual network to set the scan level or leave it unprotected. You also have the option to exclude assets or tags from external scanning, internal scanning, and Network IDS.

### Schedule scans

Alert Logic automatically performs discovery and vulnerability scans once a day. You can schedule when and how often you want Alert Logic to scan for new assets or perform vulnerability scans. For more information, see [Manage your scans](#manage-scans).

### Configuration topology overview

This topology diagram provides an overview of your scope of protection. You can see which assets are unprotected, or are protected at the Essentials (if applicable) or Professional levels.

      You will only see protection levels that your subscription level allows.       ### Install appliances and agents

Appliances

A Professional subscription requires that you install appliances for scanning and network IDS.

**Agents**

Alert Logic provides a single agent that collects data used for analysis, such as log messages and network traffic, metadata, and host identification information. For more information about installing agents, see [Install the Alert Logic Agent for Linux](../../prepare/alert-logic-agent-linux.md) or [Install the Alert Logic Agent for Windows](../../prepare/alert-logic-agent-windows.md).

### Update the Alert Logic agent firewall rules

Ensure the proper outbound firewall rules are in place for the node where you installed the agent. For information, see [Requirements for the Alert Logic Agent](../requirements/agent.md).

### Update the Alert Logic appliance firewall rules

If you used an automation template provided by Alert Logic for your appliance installation, you do not need to perform this step.

Ensure the proper inbound and outbound firewall rules are in place for the appliance. For information, see [Alert Logic Requirements for Virtual and Physical Appliances](../requirements/appliance-requirements.md).

### Configure ports for scanning

For internal scanning, Alert Logic recommends that the appliance IP be able to communicate with target assets for scanning over ports 1-65535 to validate any open service running on any port on the assets. This configuration also allows Alert Logic to test for vulnerabilities that may exist for those services.

## Dashboards

Dashboards present pertinent information that feeds from live data in your environment. You can click most items in visuals  to view the source of the data, which redirects to the corresponding page in the Alert Logic console. This allows you to drill down further into issues and streamline your response actions. For more details about Dashboards, see [Dashboards](../analyze/dashboards.md).

## Manage your scans

Alert Logic performs automatic internal and external scans on all of the assets in your deployments  once a day, unless you change the schedule. However, you can manage automatic scans in your deployments in several ways. To learn  how to manage scans and scan results, see [Manage Scans and Scan Results](../analyze/manage-scans-and-scan-results.md).

* [Manage Scans and Scan Results](../analyze/manage-scans-and-scan-results.md#Manage2)—Manage your scan schedules and scan frequency for each deployment. Default scan frequency is once a day.
* [Manage Scans and Scan Results](../analyze/manage-scans-and-scan-results.md#Manage)—You can exclude certain assets from scans in each deployment.
* [Manage Scans and Scan Results](../analyze/manage-scans-and-scan-results.md#ScanNow)—Alert Logic allows you to expedite scanning for individual assets when necessary.

Exclusions, scan frequency, and scheduling options apply only to scans of host assets by Alert Logic appliances. Cloud configuration checks performed with cloud APIs, such as checks that are part of the CIS Foundations benchmark, are not affected.
### Statistics

The Alert Logic console contains several pages where you can access data from scan results:

* [Threat Risk Index Summary](../analyze/dashboard/tri-summary.md)
* [Vulnerability Analysis](../analyze/reports/reports.md#vulnerabilityAnalysis)
* [Risk ](../analyze/reports/reports.md#Risk-reports)
* [Health Summary](../analyze/health.md#Summary)

You are also notified when assets have not been scanned in the Remediations page. See [Configuration Remediations ](../analyze/remediations.md#Configur) for more information.

### Scan results

You can review scan results and their outcomes in several different pages in the Alert Logic console:

* [Vulnerability Analysis](../analyze/reports/reports.md#vulnerabilityAnalysis)—For full reports of scan results
* [Remediations](../analyze/remediations.md)—For viewing and addressing individual issues

### Search vulnerabilities

You have access to view vulnerabilities. The [Vulnerability Analysis](../analyze/reports/reports.md#vulnerabilityAnalysis) reports allow you to view and filter vulnerabilities in the your environment. The [List of Vulnerabilities](../analyze/reports/Vulnerabilities/vulnerability-analysis/vulnerability-lists.md) in the [Monthly Vulnerability Summary](../analyze/reports/Vulnerabilities/vulnerability-analysis/vulnerability-summary.md) displays all vulnerabilities in the filters you choose.

### Scanned assets and credentials

You can filter your assets by regions, networks, subnets, hosts, tags and other assets to see what is being scanned from the Topology page. You can also manage your credentials to set up credentialed scanning for assets on this page. See [Topology](../analyze/topology.md) for more information.

## Health

The Health page provides a summary of you deployments to ensure that your deployments are correctly configured by providing the following:

* Summary of your environment
* Detailed health information regarding your networks, appliances, and agents
* Suggested configuration remediations
* Option to subscribe to health summary alerts

For more information about the Health page, see [Health](../analyze/health.md).

## Exposures

The Exposures page displays the number and types of security and configuration exposures in your protected deployment, and it provides you with information about the exposure, including color-coded threat level, evidence, and recommendations to address the exposure. For more details about the Exposures page, see [Exposures](../analyze/exposures.md).

## Reports

The Reports page provides access to data related to exposures, risks, and compliance status that Alert Logic assessed within your environment. Each report provides interactive filtering options, visual representations of the data, and informative tooltips. As a result, reports can take up to 30 minutes to reflect the latest data seen in the console. To learn more about the Reports page, see [Reports Guide](../analyze/reports/reports.md).

The Threat Manager Professional subscription include the following report types:

* [Risk Reports](../analyze/reports/reports.md#Risk-reports)—Provide convenient access to analysis, statistics, assessments, and trending data related to your security and health posture, threat risk index, and enterprise risks.
* [Threats Reports](../analyze/reports/reports.md#Threats)—Provide convenient access to analysis, statistics, assessments, and trending data related to threats and incidents detected from your subscribed products and services.
* [Vulnerabilities Reports](../analyze/reports/reports.md#Vulnerability-reports)—Provide convenient access to analysis, statistics, assessments, and trending data related to vulnerabilities discovered in your environment based on scanning outcomes.
* [Remediations Reports](../analyze/reports/reports.md#Remediations-reports)—Provide convenient access to analysis, statistics, assessments, and trending data related to configuration issues and security exposures from your subscribed products and services.
* [Compliance Reports](../analyze/reports/reports.md#Compliance-reports)—Provide convenient access to analysis, statistics, and trending data related to compliance assessment status and audit preparedness from your subscribed products and services.
* [Service Reports](../analyze/reports/reports.md#Service-reports)—Provide convenient access to data related to entitlements, capability usage, users and security content for your subscribed products and services. This includes the [TM Professional Entitlement Summary](../analyze/reports/service/entitlement/tm-pro-entitlement-summary.md), specific to Threat Manager Professional customers.

## Management settings

You can manage user account settings, such as your name, contact information, and password. To learn more about how to manage user settings, see [User settings](../prepare/manage-user-account.md).

You can also configure and manage notifications to keep you informed about the health of your account and the accounts you manage. If your user account has the Administrator role, you can manage the notifications for users in your customer account and accounts you manage. To learn more about notifications, see [Notifications](../configure/notifications.md).

Alert Logic integrations allow you to extend Alert Logic into AWS Inspector andAWS Config Rules, configure Custom Checks as inputs to Alert Logic, and even integrate with the Atlassian JIRA ticketing system.

## Service Status

The Service Status page provides updates for incidents in progress, including the overall status of Alert Logic regions and products, statuses for individual product capabilities, and details about past incidents. You can also subscribe to notifications when Alert Logic creates, updates, or resolves a service incident. To learn more about the Service Status page, see [Service Status](../analyze/service-status.md).
