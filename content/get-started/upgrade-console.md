# Upgrade to Managed Detection and Response

The Alert Logic console provides a universal navigation experience for all Alert Logic customers, regardless of your product subscriptions.

The Alert Logic console shows only the tabs and pages appropriate to your product subscription. This topic describes all possible tabs and pages, but specifies the subscriptions that generate the tabs and pages.  For more information about subscriptions Alert Logic offers, see [Get Started with Alert Logic   Subscriptions and Add-ons](subscriptions-addons.md).

## Upgrade process and window

Prior to your upgrade, Alert Logic performs a migration precheck  to uncover issues in your environment that can prevent a successful upgrade. An implementation engineer shares results and schedules a meeting with your engineering team to review  any required and recommended actions. For details about the precheck, see [Migration Prechecks](../reference/migration-prechecks.md).

After your team resolves any blocking issues, Alert Logic works with you to schedule the migration. Plan to allow 48 hours for the Alert Logic team to complete your upgrade. The two-day window allows time for troubleshooting, if necessary. The upgrade occurs during business hours Monday to Friday, with the actual migration taking approximately one hour.

## Prerequisites

Prior to your upgrade, you must perform the following cloud deployment updates:

* If you have Amazon Web Services (AWS) deployments to upgrade, you must ensure they use IAM roles created with the most current policy documents. To ensure your AWS deployments are configured properly, see:
   * [Update AWS IAM Roles to Prepare for Upgrade](update-aws-roles-for-upgrade.md#update-roles)
   * [AWS deployments with no credentials](../reference/migration-prechecks.md#AWSdeploymentswithnocredentials)
* If you have Azure deployments to upgrade, you must ensure that the configuration of the resources allows Alert Logic to discover and monitor your assets. To ensure your Azure deployments are configured properly, see [Update Azure Deployment Configuration to Prepare for Upgrade](update-azure-deployments-for-upgrade.md).

For a complete list of issues that can block your upgrade or affect its success, see [Migration Prechecks](../reference/migration-prechecks.md).

## How to find features in the new console

The new functionality that corresponds to legacy offerings is available for all MDR subscriptions.

| Legacy Functionality Name | New Functionality  |
|---|---|
| Log Manager Saved View | [Create Saved and Scheduled Log Searches](../analyze/log-search/save-schedule.md) |
| Log Review Cases | [Monthly Log Review Report](../analyze/reports/threats/log-review-analysis/monthly-log-review.md) and [Incidents](../analyze/incidents.md) |
| Log Search and Log Search BETA | [Newer Search experience with Simple and Expert modes](search-a.md) and [Search: Log Messages](../analyze/log-message-search.md) |
| Webhooks | [Webhook Connectors](../configure/connectors.md), including connectors for ticketing and messaging systems and a universal webhook connector |
| Scheduled Reports | [Scheduled Reports and Notifications](../configure/notifications/report.md) |
| Collection Alerts | [Daily Health Summary](../analyze/reports/service/health/daily-health-summary.md) and [Scheduled Reports and Notifications](../configure/notifications/report.md) |
| Scan Schedules | [Default and custom scan schedules](../analyze/manage-scans-and-results/schedules.md#Createascanschedule) |
| Summary and Dashboards | Available as [Reports Guide](../analyze/reports/reports.md), and [Risk Reports](../analyze/reports/risk/reports.md), and [Dashboards](../analyze/dashboards.md). |
| Reports | [Reports Guide](../analyze/reports/reports.md) |
| Host Groups and Zones | [Topology](../analyze/topology.md) |
| Log Correlation and Alerts | [Correlations and Notifications](../configure/notifications/log-correlation.md) |
| Assignment Policies | Automatic agent assignment within a network, which can be overriden by setting up [Cross-Network Protection](../deploy/cross-network-protection.md) |
| Blocking policies | Automated Response |
| Out-of-Band WAF | Web Attack Detection |
| Alert Logic Tags | Full tag support for all assets |

## Deprecated or unsupported functionality

Alert Logic has removed or does not support the following functionality. Both lists apply to Cloud Defender, which includes both Threat Manager and Log Manager.

* For Threat Manager customers
   * Browse Devices
   * Event alerts
   * Defense alerts
   * Case alerts
   * Monitoring policies
* For Log Manager customers
   * Log Collection Schedule policies
   * Case alerts

## Upgrade details

Your upgrade offers feature parity and enhancements that affect the following functionality,  which is available with all MDR subscriptions:

* [Machine Learning Log Review Upgrade](../analyze/log-review-upgrade.md) (March 2021)
* [Incidents Upgrade ](incidents-upgrade.md) (March 2021)
* [Log Search Upgrade](log-search-upgrade.md) (February 2021)
* [Cloud Defender Omnibox Search Upgrade](omnibox-search-upgrade.md) (February 2021?)
* [Notifications Upgrade](notifications-upgrade.md) (February 2021)
* [Scan Functionality Upgrade](scans-upgrade.md) (January 2021)
* [Managed Detection and Response Reports Upgrade](upgrade-reports.md) (February 2019)

## Additional features

Your upgrade to MDR offers features that were not available on the legacy platform. The additional features improve your experience and your ability to detect and respond to threats in your environment.

All MDR subscriptions offer these features:

* [CIS Microsoft Azure Foundation Benchmark reporting](../analyze/reports/compliance/azure-foundation-benchmark.md) (~March 2020)
* [Dashboards](../analyze/dashboards.md) (February 2020)
* [Threat Risk Index](../analyze/TRI-score-factors.md) (February 2020)
* [Exposures](../analyze/exposures.md) (February 2020)
* [Extended Endpoint Protection](about-extended-endpoint-protection.md) (September 2019
* [Health](../analyze/health.md) (April 2019)
* [Cross-Network Protection](../deploy/cross-network-protection.md) (Data Center deployments) (April 2019)

These features are available with Alert Logic MDR Professional and Alert Logic MDR Enterprise subscriptions:

* [File Integrity Monitoring ](../configure/file-integrity-monitoring.md) (September 2020)
* [Web Log Analytics (WLA)](about-wla.md) (September 2020)
* [Application Registry](../configure/application-registry.md) (April 2020)
* Policy-based configuration of system and [application](../configure/application-logs.md) (flat file) logs
* Improved support for [Azure deployments](../deploy/azure-pro-ent.md) and [AWS deployments](../deploy/aws-auto-pro-ent.md)

## Learn more

For more resources to help you learn about key features in MDR, see [Recommended Training for New and Upgrading Customers](recommended-training.md). Linked materials include training videos, product documentation, and knowledge base articles organized by feature.
