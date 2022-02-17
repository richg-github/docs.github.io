# Get Started with the Alert Logic Console

The Alert Logic console provides a universal navigation experience for all Alert Logic customers, regardless of subscription level. The Alert Logic console displays only the tabs and pages appropriate to your subscription level. This topic describes all possible tabs and pages, but specifies the subscriptions that generate the tabs and pages.

You can check  the operational status of the Alert Logic console in the Service Status page. Alert Logic recommends that you subscribe to the Service Status page and all your  components, including Alert Logic console. For more information about the Service Status page and how to subscribe, see [Service Status](../analyze/service-status.md).

## Navigation menu

The navigation menu is located on the left side of the page under a menu icon (![](../Resources/Images/dashboard/menu-icon.png)), and the options are nested.

**To navigate between pages**:

1. Click the menu icon (![](../Resources/Images/dashboard/menu-icon.png)) to see the navigation menu.
2. Click on a navigation group (for example, **Respond**) to expand the options under that group.
3. Click on a navigation item (for example, **Incidents**) that you want to explore further.
4. Click the menu icon  (![](../Resources/Images/dashboard/menu-icon.png)) again to collapse the menu and view the page.

### ![](../Resources/Images/dashboard/respond-icon.png) Respond 

#### Incidents

The [Incidents](../analyze/incidents.md) page displays information about:

* Incidents generated from multiple sources, like Network IDS, Log Management, and Amazon GuardDuty
* How to use that information to manage and close incidents
* How to secure your environments

This page requires an Alert Logic MDR Professional  or an Alert Logic MDR Enterprise Enterprise subscription. For more information about subscriptions and add-ons, see [Get Started with Alert Logic   Subscriptions and Add-ons](subscriptions-addons.md).

#### Exposures

The [Exposures](../analyze/exposures.md) page provides you with the information you need to analyze and address exposures in your environment. Alert Logic lists exposures found in your deployments; provides detail about the exposure, evidence, and affected assets; and lists remediations to resolve an exposure or a group of exposures.

#### Health

Ensure that your deployments are correctly configured from the [Health](../analyze/health.md) page, which provides this information:

* Summary of your environment
* Detailed health information regarding your networks, appliances, and agents with suggested configuration remediations
* Option to subscribe to health summary alerts

### ![](../Resources/Images/dashboard/investigate-icon.png) Investigate

#### Search

The Search tab allows you to search for:

* [Log Messages](../analyze/log-message-search.md)—requires a Professional or an Enterprise subscription
* Events—requires a Professional or an Enterprise subscription

#### Topology

The  Topology page displays an interactive diagram that uses color-coded icons to display the distribution of exposures and threats across your network assets. For more information, see [Topology](../analyze/topology.md).

#### Vulnerability Library

Alert Logic lists all of the scan content that Alert Logic scanners can check for in the Vulnerability Library. You can easily search for and view information on a specified vulnerability that Alert Logic scanned for, and see whether it impacts assets in your environment.

### ![](../Resources/Images/dashboard/validate-icon.png) Validate

#### Reports

The [Reports](../analyze/reports/reports.md) tab provides access to data related to exposures and incidents Alert Logic found within your deployments. Report data is cached and refreshed every 30 minutes. As a result, reports can take up to 30 minutes to reflect the latest data seen in the console.

Depending on your Alert Logic subscriptions, you will see some or all of the following report types:

* [Risk Reports](../analyze/reports/risk/reports.md#Risk)—Provide convenient access to analysis, statistics, assessments, and trending data related to your security and health posture, threat risk index, and enterprise risks. Each report provides interactive filtering options, visual representations of the data, and informative tooltips. All subscriptions see this content.
* [Threats Reports](../analyze/reports/threats/reports.md#Threats)—Provide convenient access to analysis, statistics, assessments, and trending data related to threats and incidents detected from your subscribed products and services. Each report provides interactive filtering options, visual representations of the data, and informative tooltips. This content requires a Professional or Enterprise subscription.
* [Vulnerabilities Reports](../analyze/reports/Vulnerabilities/reports.md#Vulnerabilities)—Provide convenient access to analysis, statistics, assessments, and trending data related to vulnerabilities discovered in your environment based on scanning outcomes. Each report provides interactive filtering options, visual representations of the data, and informative tooltips.  All subscriptions see this content.
* [Remediations Reports](../analyze/reports/remediations/reports.md#Remediations)—Provide convenient access to analysis, statistics, assessments, and trending data related to configuration issues and security exposures from your subscribed products and services. Each report provides interactive filtering options, visual representations of the data, and informative tooltips.  All subscriptions see this content.
* [Compliance Reports](../analyze/reports/compliance/reports.md#Compliance)—Provide convenient access to analysis, statistics, and trending data related to compliance assessment status and audit preparedness from your subscribed products and services. Each report provides interactive filtering options, visual representations of the data, and informative tooltips. All subscriptions see this content.
* [Service Reports](../analyze/reports/service/reports.md#Service)—Provide convenient access to data related to entitlements, capability usage, users and security content for your subscribed products and services. Each report provides interactive filtering options, visual representations of the data, and informative tooltips. This content requires a Professional or Enterprise subscription.
* [WAF Reports](../analyze/reports/WAF/reports.md) —Provide convenient access to activity and policy information for the Alert Logic Managed Web Application Firewall (WAF) service. This content requires WAF purchased as an add-on.

#### PCI Scan Disputes

File a dispute in the [PCI Scan Disputes](../configure/pci-scan-dispute.md) page if a PCI scan reported findings that you want to dispute, such as if a scan identifies a false positive vulnerability.

### ![](../Resources/Images/dashboard/configure-icon.png)Configure

#### Deployments

Configure [Deployments](about-deployment-types.md) for AWS, Azure, Google Cloud Platform, and Data Center protected environments. All subscriptions see this content.

#### Log Management

The Log Management page has configuration settings for Log Management policies and [Log Management Policies](../configure/log-management-policies.md)and [log collection schedules](../configure/schedule-log-collection.md). This content requires a Professional or an Enterprise subscription.

#### Certificate and Keys

Set up [Certificates and Keys](../configure/certificates-keys.md) for your assets. This content requires a Professionalor an Enterprise subscription.

#### WAF

Set up Alert Logic Managed Web Application Firewall (WAF). This content requires an Enterprise subscription or a Professional subscription with WAF purchased as an add-on.

#### Application Registry

The [Application Registry](../configure/application-registry.md) provides an intuitive and efficient way to integrate multiple third-party applications that can generate logs. Application Registry is a repository of platform integrations in your Configuration group in the Alert Logic console. Integration with third-party applications adds administrative and security value to your organization.  Application Registry is only available for Professional and EnterpriseManaged Detection and Response customers.

#### Endpoints

The [Endpoint Protection](about-extended-endpoint-protection.md) page provides access to Extended Endpoint Protection functionality, which helps you control threats and manage incidents from employee workstations, points of sale, servers, and more.

#### PCI Scanning

Use the [Payment card industry (PCI) scanning](../configure/pci-scans.md) page to schedule  PCI compliance scans, view the results of those scans, and then work to resolve vulnerabilities and prove compliance to auditors.

#### Connectors

[Connectors](../configure/connectors.md) is a convenient feature that  allows Alert Logic to send real-time data directly to a third-party application. You can configure connectors in the Alert Logic console to send alert notifications to any public-facing HTTP endpoint.

### ![](../Resources/Images/dashboard/manage-icon.png) Manage

#### Integrations

#### Users

The [User settings](../prepare/manage-user-account.md)  page allows you to manage user account settings, such as your name, contact information, and password. User accounts with the administrator role can manage the details for other users in their organization.

#### Notifications

Configure [Notifications](../configure/notifications.md) to get an email about  threats, changes, and scheduled events in your environment so you can respond quickly.

#### Service Status

The [Service Status](../analyze/service-status.md) page allows  customers to monitor the status of their subscribed region and product capabilities. Alert Logic provides updates for incidents in progress, including the overall status of Alert Logic regions and products, statuses for individual product capabilities, and details about past incidents.
