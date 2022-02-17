# Scan Functionality Upgrade

Alert Logic upgraded scan functionality to provide fully automated scanning for all your assets. You no longer have to create individual scans for every asset.

When you create a new deployment, Alert Logic automatically creates default scan schedules to perform external and internal vulnerability scans on all non-excluded assets and ports that vary according to deployment type. Alert Logic also creates a default discovery scan schedule  to find new assets in Data Center deployments. You can schedule when to perform specific scans for all or selected assets and ports. To learn more about deployments and deployment types, see [About  Deployment Types](about-deployment-types.md).

Several features in the Alert Logic console allow you to control how and when to scan, exclude assets and ports,  and expedite an asset to be scanned ahead of its scheduled time. You can view data results, including vulnerabilities, statistics, reports, and recommended actions against threats discovered during scans.

PCI scans are not affected by this upgrade. For information, see [Manage PCI Scans](../configure/pci-scans.md#Manage2).

## Upgraded scans features

[From perspective of Cloud Defender customer we want to upgrade] The upgrade provides feature parity for scan frequency and scan scheduling. Upgrades affect:

* Scanning capability
* Scan scheduling
* Adjusting scan performance

To learn more about upgrade details of scanning capabilities and scheduling, see [Scan Functionality Upgrade](#).

Alert Logic offers enhanced features for creating and managing scans, adjusting scan performance, expediting scans, and analyzing results.

### Create and manage scans

Alert Logic scans all assets in your deployments automatically according to default scan schedules. You no longer have to create individual scans. Alert Logic offers several ways for you to manage scan schedules in your deployments.

The following features are available for managing your scans from the Scan Schedules page for each deployment:

* Default scan schedules with preselected frequencies, scan windows, assets, and ports
* Create additional schedules for all or selected assets and ports
* Edit default and custom schedules
* Stop a scan in progress
* Activate or deactivate a scan schedule
* Exclude assets and ports from scans

For information about these features and more, see [Manage Scan Schedules](../analyze/manage-scans-and-results/schedules.md). To get started with scans, see [Get Started with Alert Logic Scans](get-started-scans.md).

Exclusions, scan frequency, and scheduling options apply only to assets that are scanned using Alert Logic appliances. Cloud configuration checks performed using cloud APIs, such as checks that are part of the CIS Foundations benchmark, are not affected.

### Expedite scans

If you need to run a  scan on a host immediately, you can use the Scan Now feature on the Topology page. This feature scans the selected host right away or as soon as possible, outside the normal schedule. For more information, see [Scan Now](../analyze/manage-scans-and-results/adjust-settings.md#ScanNow).

You can  also create a scan schedule and choose the **Scan once** option to scan selected assets once, starting at a specific time. For example, to verify a patch or remediation action, you can use this option to schedule a scan of several assets to start within the next five minutes instead of waiting for the next regularly scheduled scan. For more information, see [Create a scan schedule](../analyze/manage-scans-and-results/schedules.md#Createascanschedule).

### Adjust scan settings

Features for adjusting scan settings are available from the Topology page:

* Manage credentials for internal vulnerability scans
* Adjust scan performance by choosing more or fewer concurrent scans

For more information, see [Adjust Scan Settings](../analyze/manage-scans-and-results/adjust-settings.md).

### Statistics

The Alert Logic console contains several pages where you can access data pulled from scan results:

* [Vulnerabilities Reports](../analyze/reports/Vulnerabilities/reports.md)        —Provide valuable summary, breakdown, variance, distribution, and trending data for vulnerabilities discovered across your environments by all scans.
* [Scan Schedule Breakdown](../analyze/reports/Vulnerabilities/reports.md#ScanScheduleBreakdown)        —Provide summary, detailed, and variance vulnerability results for  specific scan schedules.
* [Exposures](../analyze/exposures.md)        —Lists exposures found in your deployments resulting from vulnerability scans  and remediations to resolve an exposure or a group of exposures.

You are also notified when assets have not been scanned in the [Coverage and Health Dashboard](../analyze/dashboard/coverage-health.md) and [Health](../analyze/health.md) page.

### Scan results

You can review scan results and their outcomes in several different pages in the Alert Logic console:

* [Legacy scan results](../analyze/manage-scans-and-results/analyze-results.md#viewlegacyscanresults)        —For customers who have upgraded from a previous version of the console
* [Vulnerabilities Reports](../analyze/reports/Vulnerabilities/reports.md)        —For full reports of all scan results
* [Scan Schedule Breakdown](../analyze/reports/Vulnerabilities/reports.md#ScanScheduleBreakdown)        —For full reports of specific scan schedule results
* [Exposures](../analyze/exposures.md)        —For viewing and addressing individual issues

### Search vulnerabilities

You can find specific vulnerabilities in your environment from the list of open exposures on the Exposures page. You can switch to the Exposures view, optionally select filters on the left  to narrow results, and use the search feature at the top of the list to find specific vulnerabilities. For more information about the Exposures page, see [Exposures](../analyze/exposures.md).

You can also use the Vulnerability Library to research vulnerabilities that Alert Logic scans for and see whether a specific vulnerability impacts your environment. For more information, see [Vulnerability Library](../analyze/vulnerability-library.md).

### Host groups and zones

Deployments in Managed Detection and Response replace host groups and zones. On the Topology page, you can filter by deployment, regions, networks, subnets, hosts, tags, and other assets to see which assets are being scanned. You can also manage scan settings such as your credentials to set up credentialed scanning for assets and adjust scan performance settings. For more information, see [Topology](../analyze/topology.md) and [Adjust Scan Settings](../analyze/manage-scans-and-results/adjust-settings.md).

The Last Scanned Breakdown report, available from the Vulnerabilities Reports page, lists when assets in your deployments were last scanned for vulnerabilities. For more information, see [Last Scanned Breakdown](../analyze/reports/Vulnerabilities/last-scanned-breakdown.md).
