# Get Started with Alert Logic Scans

A scan detects and identifies network and host vulnerabilities in your environment. Scans can perform external attack simulations as well as comprehensive vulnerability checks including registry evaluation. Alert Logic scans can also help you meet PCI compliance requirements. For more information, see the detailed [About Alert Logic Scans](../deploy/about-scans.md) documentation.

## Scan types

There are three types of supported scans:

#### Internal scans

An internal scan runs from an Alert Logic appliance in your environment. When you define a scan, you can specify [credentials](../prepare/authenticated-scanning.md) to use with the internal scan. If you provide credentials, Alert Logic can log on to each host on your network and collect information about the host while it performs comprehensive vulnerability checks including registry setting evaluation. If you do not provide credentials, Alert Logic scans your network without logging on to each host and performs as many checks as possible.

#### External scans

An external scan runs from the Alert Logic data centers against your environment. This type of scan simulates attacks from outside your network and identifies potential issues from these attack types.

#### PCI scans

A PCI scan is a type of external scan that is used specifically for Payment Card Industry (PCI) compliance requirements. For more information on PCI scans, refer to the PCI scan documentation.

## Scanning best practices

When you configure your scans, use the following guidelines to create successful scans and scan results. For more in-depth best practices, see the detailed [About Alert Logic Scans](../deploy/about-scans.md) documentation.

* Scan often.
* Scan everything in your network.
* Scan at the right times:
   * Scan your servers, firewalls, and routers during off-peak times.
   * Scan your workstations during working hours.
* Do not scan during service windows.
* Make sure each scan is manageable.
   * Run open-ended scans so they are not truncated by scan windows.
   * Split up long scans into reasonable pieces to make sure everything is scanned.

## Suggested scan frequency

The following table shows the recommended frequency for internal and external scans on different sets of ports.

| Scan frequency | Common TCP and UDP ports | Typically Vulnerable TCP and UDP ports | All TCP and UDP ports |
|---|---|---|---|
| Internal scan | External scan | Internal scan | External scan | Internal scan | External scan |
|---|---|---|---|---|---|
| Daily |  | x |  |  |  |  |
| Weekly | x |  |  | x |  |  |
| Monthly |  |  | x |  |  | x |
| Quarterly |  |  |  |  | x |  |
| After configuration change |  |  |  |  | x | x |
| Suspicion of break or infection |  |  |  |  | x | x |

## Originating IP addresses

The following table contains the range of IP addresses owned by Alert Logic. Alert Logic scans originate from a subset of the following IP addresses. Make sure that your firewalls allow scanning traffic from all of the following IP addresses.

| IP/CIDR | # of addresses | Included addresses |
|---|---|---|
| 204.110.218.0/23 | 512 | 204.110.218.0 — 204.110.219.255 |
| 208.71.208.0/22 | 1024 | 208.71.208.0 — 208.71.211.255 |
| 185.54.124.0/22 | 1024 | 185.54.124.0 — 185.54.127.255 |

## Explore Alert Logic scans

You can access most scan-related features from the Scans page in the Alert Logic console. From the Scans page, you can create and schedule scans, manage scan results, and complete steps for PCI compliance. For scans that have completed, you can view results, download a CSV file of the results, and get help with scans or individual vulnerabilities. For more information on these tasks, see the detailed [About Alert Logic Scans](../deploy/about-scans.md) documentation.

### Access Alert Logic scans

To access scans and scan results: [View and export scan results](../analyze/manage-scans-and-results/schedules.md#Viewandexportscanresults)

1. In the Alert Logic console, click **OVERVIEW**, and then click **Scans**.
2. On the Scans page, use the tabs to access scan features, as follows:
   * **Statistics**—Access summarized vulnerability information for your environment from overall scan results. See [View vulnerability statistics](../deploy/manage-scans-results.md#viewHighLevelVulnerability).
   * **Scans**—Create and update scan definitions, and access scan results. See [How to work with scans and scan results](../deploy/manage-scans-results.md).
   * **PCI Compliance**—Create PCI scans and access PCI scan results. See [Manage PCI Scans](../configure/pci-scans.md).
   * **Search**—Search scan results for criteria such as vulnerability name and risk levels. See [Search scan results](../deploy/manage-scans-results.md#searchScansHistory).

### Download scan reports

To download a report after a scan has finished:

1. In the Alert Logic console, click **OVERVIEW**, and then click **Scans**.
2. Navigate to the Scans tab on the Scans page.
3. Click **Results** next to the scan title. The table that appears shows all completed reports for the selected scan.
4. Click the icons in the **Export** column to download reports in various formats.* Click the green CSV icon (![](../Resources/Images/Icons/green_csv.png)) to download a .csv file with vulnerability and exposure details.
* Click the blue CSV icon (![](../Resources/Images/Icons/blue_csv.png)) to download a .csv file with host details.

The industry-standard CSV downloads include detailed host and vulnerability information. The format allows you to analyze, sort, and filter the information externally in the software of your choice. Alert Logic recommends you use CSV downloads for all scan analysis.

### Scan help

If you need help with scan results, you can create a support case either at the scan level or at the individual vulnerability level.

To get help at the scan level:

1. In the Alert Logic console, click **OVERVIEW**, and then click **Scans**.
2. Select your desired scan from the list and then click **Results**.
3. In the Log ID column of the table, click the support icon (![](../Resources/Images/Cloud Defender/Scanning/al-support.png)) for the specific scan run date.
4. An email form appears in your default email application. The email is pre-filled with the following information:
   * Product
   * Account Name
   * Account ID
   * Policy Name
   * Policy ID
6. Add a description of your issue to the email, and then send it. An Alert Logic engineer will address your case.

To get help at the vulnerability level:

1. In the Alert Logic console, click **OVERVIEW**, and then click **Scans**.
2. Select your desired scan from the list, and then click **Results**.
3. Locate the specific scan run date, and then click the number of hosts listed in the **Results** column.
4. Click the support icon (![](../Resources/Images/Cloud Defender/Scanning/al-support.png)) next to the individual vulnerability.
5. An email form appears in your default email application. The email is pre-filled with the following information:
   * Product
   * Account Name
   * Account ID
   * Policy Name
   * Policy ID
   * Vulnerability Name
   * Vulnerability ID
   * Exposure ID
   * Host IP
   * Host ID
7. Add a description of your issue to the email, and then send it. An Alert Logic engineer will address your case.
