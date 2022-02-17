# Get Started with Alert Logic PCI Scans

A PCI scan is a type of external scan used specifically for Payment Card Industry Data Security Standard (PCI DSS) compliance requirements. PCI scans offer a better assessment of web servers than the regular Alert Logic external scan, and produce a document that you can use as proof of compliance. For more information about scans, see [Manage PCI Scans](../configure/pci-scans.md).

## PCI scanning best practices

When configuring your scans, use the following guidelines to create successful scans and scan results. For more in-depth best practices, see [Scanning best practices](../deploy/about-scans.md#scanning-best-practices).

* Scan at least monthly by a fully qualified domain name (FQDN) when available. PCI compliance requires a minimum of quarterly reports, but Alert Logic recommends scheduling scans for PCI compliance  monthly or more often.
* Scan your entire PCI scope.
* Reduce your PCI scope as much as possible.
* Schedule your scans for your servers, firewalls, and routers during off-peak times.
* Do not scan during service windows, and allow PCI scans to run to completion.
* Split up long scans into distinct PCI scopes.

PCI scanning produces a legal document that can affect your compliance standing. It is the responsibility of the customer to make sure the scope is correct.

## Originating IP addresses

The following table contains the range of IP addresses owned by Alert Logic. Alert Logic scans originate from a subset of these IP addresses, so make sure that your firewalls allow scanning traffic.

| IP/CIDR | Number of addresses | Included addresses |
|---|---|---|
| 204.110.218.0/23 | 512 | 204.110.218.0 — 204.110.219.255 |
| 208.71.208.0/22 | 1024 | 208.71.208.0 — 208.71.211.255 |
| 185.54.124.0/22 | 1024 | 185.54.124.0 — 185.54.127.255 |

## Explore Alert Logic PCI scans

You can access most scan-related features from the Scans page in the Alert Logic console. All PCI scan information is on the PCI Compliance tab.

To access PCI scan information:

1. In the Alert Logic console, click the menu icon (![](../Resources/Images/dashboard/menu-icon.png)) to see the navigation menu, and then click the ![](../Resources/Images/dashboard/configure-icon.png)**Configure** menu item.
2. Click **PCI Scanning** to access the PCI Scanning page.
3. Click the **PCI Compliance** tab.
4. You can explore PCI scan features, as follows:
   * **Current Status**—View your scan status.
   * **Latest 25 Reports**—Manage completed scan results.
   * **PCI Scan**—Create and schedule new scans.
   * **PCI Disputes**—See your dispute status.

For more information on these tasks, see [View PCI compliance status and history](../configure/pci-scans.md#viewStatusHistory)

### Schedule a PCI scan

To schedule a PCI scan:

1. Navigate to the **PCI Compliance** tab on the Scans page.
2. Under **PCI Scan**, click  **Schedule New Scan**.
3. On the New PCI Scan page, enter the requested information.              PCI DSS requires customers to supply FQDNs in addition to external-facing IP addresses and other unique entryways into applications for the entire in-scope infrastructure. This includes, but is not limited to:
   * Discrete IP addresses
   * IP address ranges
   * Domains for all web servers
   * Domains for mail servers
   * Domains used in name-based virtual hosting
   * Web-server URLs to directories that cannot be reached by crawling the website from the home page
   * Any other public-facing domains or domain aliases
5. Click **Submit PCI scan job**.

For more information on scheduling PCI scans, see [Schedule a PCI scan](../configure/pci-scans.md#scheduleScan).

### Download scan reports

To view results and download a report after a scan is complete:

1. Navigate to the **PCI Compliance** tab on the Scans page.
2. Under **Latest 25 Reports**, click a scan title.
3. In the **PCI Scan Result page**,  under the **Report Downloads**, is a list of available reports:
   * **Executive Summary**—Vulnerabilities by component showing compliance status for each host scanned.
   * **Vulnerability Details**—Report listing the details of each vulnerability. The report is available as a CSV file or a PDF. The CSV file includes less detail than the PDF, but the information is easy to view and analyze in a spreadsheet.
   * **Attestation of scan compliance**—Overall summary that shows whether the scan customer’s infrastructure received a passing status.
   * **PCI ASV Feedback form**—Use this form if you want to send feedback to PCI Security Standards Council (SSC) regarding your scanning experience, your experience with Alert Logic, or any other aspects of PCI scans.
   * Alert Logic** Disclosures regarding ASV PCI Scans**—This is a disclosure form of which solutions Alert Logic owns rights.
5. Click the report you want to download. Some reports open a new page while the console processes them.

### Dispute PCI scan results

To dispute a vulnerability, you must provide an explanation and supporting evidence for the disputed findings, and then submit the information for review by an Alert Logic Approved Scanning Vendor (ASV) Security Engineer. After you submit your dispute request, the engineer reviews the submitted evidence and makes a ruling. If the engineer has questions or needs more information, he or she will communicate with you through the PCI dispute system. For more information on how to submit your dispute by using the Alert Logic PCI Dispute system, see the instructions in [PCI Scan Disputes](../configure/pci-scan-dispute.md).

Alert Logic does not carry disputes forward from one quarterly scan to the next. This is one of the requirements defined in the [ASV Program Guide](https://www.pcisecuritystandards.org/documents/ASV_Program_Guide_v3.0.pdf).

### PCI scan help

If you need help with your PCI results, contact Alert Logic Technical Support at (877) 484-8383 in the US, or +44 (0) 203 011 5533 in the UK.

## PCI Audit reports

Alert Logic provides PCI audit reports in the Reports page which provide documentation to help you demonstrate compliance to specific requirements of the  PCI DSS.

**To access the PCI Requirements report:**

1. In the Alert Logic console, click **Reports**, and then click **Compliance**.
2. Under **PCI DSS Audit**, click **VIEW**.
