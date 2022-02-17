# Get Started with Alert Logic Scans

A scan detects and identifies network and host vulnerabilities in your environment. Scans can perform external attack simulations as well as comprehensive vulnerability checks including registry evaluation. For more information, see the detailed [About Alert Logic Scans](../deploy/about-scans.md) documentation. Alert Logic scans can also help you meet Payment Card Industry (PCI) compliance requirements. For more information, see [Manage PCI Scans](../configure/pci-scans.md).

You can check the operational status of your automated and scheduled scans in the Service Status page in the Alert Logic console. Alert Logic recommends that you subscribe to the Service Status page and all your Alert Logic components, including scans. For more information about the Service Status page and how to subscribe, see [Service Status](../analyze/service-status.md).

## Scan types

There are four types of supported scans:

* Discovery scans
* Internal scans
* External scans
* PCI scans

### Discovery scans

A discovery scan is used to identify hosts on a network. The scanner makes a reasonable attempt to identify live systems, including systems that do not respond to common Internet Control Message Protocol (ICMP) echo requests.

### Internal scans

An *internal scan* runs from an Alert Logic appliance or agent in your environment.

**Internal scan with no credentials or agent-based scan:**

If you do not provide credentials or enable agent-based scanning, Alert Logic scans your network without logging on to each host and performs as many vulnerability as possible.

**Internal scan with credentials and no agent-based scan:**

When you define a scan, you can specify credentials to use with the internal scan. If you provide credentials, Alert Logic can log on to each host on your network and collect information about the host while it performs comprehensive vulnerability checks including registry setting evaluation. To learn how to provide credentials, see [Manage your credentials](../analyze/manage-scans-and-results/adjust-settings.md#Manageyourcredentials).

**Internal scan with agent-based scan:**

You can enable agent-based scanning by deployment. Agent-based scans and  credentialed network scans provide similar  internal vulnerability assessment.  When the network scan begins an internal assessment of a host, it checks with that host for the presence of agent-based scan configuration. The network scan will not run redundant vulnerability assessments for the host. For more information, see [Agent-Based Scanning](../analyze/manage-scans-and-results/agent-based-scan.md).

### External scans

An external scan runs from the Alert Logic network against your environment. This type of scan simulates attacks from outside your network and identifies potential issues from these attack types.

For more information about discovery, internal, and external scans, see [About Alert Logic Scans](../deploy/about-scans.md) and [Alert Logic Scanning Technical Description](../reference/scans-technical-description.md).

### PCI scans

A PCI scan is a type of external scan that is used specifically for Payment Card Industry (PCI) compliance requirements. For more information on PCI scans, see [Manage PCI Scans](../configure/pci-scans.md).

## Scanning best practices summary

When configuring your scans, use the following guidelines to create successful scans and scan results. For more in-depth best practices, see the detailed [Scanning best practices](../deploy/about-scans.md#scanning-best-practices).

* Scan often
* Scan everything in your network
* Scan at the right times
   * Scan your servers, firewalls, and routers during off-peak times
   * Scan your workstations during working hours
   * Scan your staging devices and remediate any issues findings before scanning production devices
* Do not scan during service windows

### Optimize your scans

When configuring your assets for scanning, consider and implement a strategy that is particular to your scanning targets and environment.

* **Use agent-based or credentialed scans on everything, and use un-credentialed scans as fallback.** Agent-based scanning or credentialed scans produce the most accurate results and should be used on all servers and workstations. Un-credentialed network scans should be used only for devices where agent-based or credentialed scanning is not available, for example, routers, switches, and printers.
* **Be mindful of what you are scanning.** In terms of length, not all types of scans are equal. Windows-credentialed scanning takes longer than all other credentialed or non-credentialed scans. Under test scenarios, Windows-credentialed scans have taken up to four times as long as other scans. The web application scanning component used in Alert Logic PCI scans can also run long due to the amount of web pages present and the number of fields on each page, multiplied by the number of sites being scanned. Consider these factors when defining your scans and determining scan windows.
* **Multitask.** Scan your networks separately in a staggered schedule to allow for remediation in stages.
* **Try not to scan over WAN links or VPN.** The traffic between the scanner and the scan target is high compared to the relatively low traffic between the scanner and Alert Logic. Place the scanner on the same side of the VPN or WAN link as the scan target for the best use of your bandwidth.

For printer devices that are not using web services, Alert Logic recommends stopping services that reside on ports 80 and 443, and disable “LPD/LPR” on the printer port 515/TCP to prevent the device from printing scan activity log messages.

## Manage your scans

Alert Logic performs scans on all assets in your deployments. When you create a new deployment, Alert Logic automatically creates default scan schedules to perform external and internal vulnerability scans on all non-excluded assets and ports that vary according to deployment type. Alert Logic also creates a default discovery scan schedule  to find new assets in Data Center deployments. You can schedule when to perform specific scans for all or selected assets and ports.

To learn  how to manage scans and scan results, see [Manage Scans and Scan Results](../analyze/manage-scans-and-scan-results.md).

* [Manage Scan Schedules](../analyze/manage-scans-and-results/schedules.md)        —Manage your scan schedules and scan frequency for each deployment.
* [Exclude assets and ports from scans](../analyze/manage-scans-and-results/schedules.md#Excludeassetsfromscans)        —You can exclude certain assets and ports from scans in each deployment.
* [Scan Now](../analyze/manage-scans-and-results/adjust-settings.md#ScanNow)        —Alert Logic allows you to expedite scanning for individual assets when necessary.

Exclusions, scan frequency, and scheduling options apply only to assets that are scanned using Alert Logic appliances. Cloud configuration checks performed using cloud APIs, such as checks that are part of the CIS Foundations benchmark, are not affected.
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

### Scanned assets, credentials, and performance adjustments

The Last Scanned Breakdown report, available from the Vulnerabilities Reports page, lists when assets in your deployments were last scanned for vulnerabilities. For more information, see [Last Scanned Breakdown](../analyze/reports/Vulnerabilities/last-scanned-breakdown.md).

On the Topology page, you can filter your assets by regions, networks, subnets, hosts, tags and other assets to see which assets are being scanned. You can also manage scan settings such as your credentials to set up credentialed scanning for assets and adjust scan performance settings. For more information, see [Topology](../analyze/topology.md) and [Adjust Scan Settings](../analyze/manage-scans-and-results/adjust-settings.md).
