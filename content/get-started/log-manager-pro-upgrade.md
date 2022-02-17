# Log Manager Pro Upgrade

Alert Logic Log Manager collects, aggregates, and normalizes log data whether it originates in your own data center, a hosted environment, or the cloud. Flexible data collection options, including physical appliances, remote collectors with agents or without agents, and cloud native APIs, provide low-impact deployment options for all of your infrastructure. Alert Logic will upgrade Log Management customers to Log Management Pro, which includes a number of changes to your experience.

The Alert Logic console shows only the tabs and pages appropriate to your product subscription. This topic describes all possible tabs and pages, but specifies the subscriptions that generate the tabs and pages.  For more information about subscriptions Alert Logic offers, see [Get Started with Alert Logic   Subscriptions and Add-ons](subscriptions-addons.md).

## Prerequisites

Prior to your upgrade, you must perform the following deployment and agent updates:

* If you have Amazon Web Services (AWS) deployments, you must ensure your deployments use IAM roles created with the most current policy documents. To update IAM roles, see [Update your IAM roles](../prepare/aws-cross-account-role-setup.md#update-roles).
* If you have Azure deployments, you must ensure your Microsoft Azure resources are configured to allow Alert Logic to discover and monitor your assets. To ensure your Azure deployments are properly configured, see [Configure App Registration and RBAC for Microsoft Azure Resources](../prepare/azure-rbac-role-setup.md).
* Upgrade your agents and appliances to the most recent version. Download and install the appropriate agents or appliances. For more information, see the following documents:
   * [Install the Alert Logic Agent for Linux](../prepare/alert-logic-agent-linux.md)
   * [Install the Alert Logic Agent for Windows](../prepare/alert-logic-agent-windows.md)
   * [Install and Configure the  Virtual Appliance](../prepare/virtual-appliance.md)

## How to find features in the new console

| Legacy Functionality Name | New Functionality  |
|---|---|
| Collection Alerts | [Health](../analyze/health.md#Notifica) |
| Log Review Cases | [Monthly Log Review Report](../analyze/reports/threats/log-review-analysis/monthly-log-review.md), and [Incidents](../analyze/incidents.md) |
| Host Groups and Zones | [Topology](../analyze/topology.md) |
| Log Manager Saved View | [Create Saved and Scheduled Log Searches](../analyze/log-search/save-schedule.md) |
| Summary and Dashboards | Available as [Threat Risk Index Summary](../analyze/dashboard/tri-summary.md), [LM Professional Entitlement Summary](../analyze/reports/service/entitlement/lm-pro-entitlement-summary.md), and [Dashboards](../analyze/dashboards.md) |
| Webhooks | [Support for Webhooks](../prepare/webhooks.md) |
| Remediations | [Exposures](../analyze/exposures.md) |

## Deprecated or unsupported functionality

Alert Logic has removed functionality or removed support for functionality of the following:

* For Log Manager customers
   * Legacy Log Search
   * Alert rules

    For Log Manager customers, this upgrade involves only collection and scan configuration migration, and does not include scan schedule migration.
