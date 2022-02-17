# Analyze Scan Results

You can use scan results to access valuable vulnerability information about your networks, including historical trends and current details. Reviewing the data helps to identify issues you can address to improve your security posture. You can review scan results and their outcomes in different pages in the Alert Logic console:

* [View legacy scan results](#viewlegacyscanresults)
* [View vulnerability reports](#Viewvulnerabilityreports)
* [View scan schedule breakdown reports](#Viewscanschedulebreakdownreports)
* [View and remediate exposures detected by vulnerability scans](#Viewandremediateexposuresdetectedbyvulnerabilityscans)

## View legacy scan results

If you were subscribed to the previous version of Alert Logic products, you can view your legacy scan results from the Settings menu. Click the Settings icon (![](../../Resources/Images/supportThreeDots.png)), and then click **Legacy Scan Results**. You can also access the legacy scan results from the Reports page.

**To access legacy scan results from the Reports page**:

1. Click **REPORTS**, and then click **Scheduled**.
2. Click **Saved Scheduled Reports**, and then click **Archived Reports**.

## View scan schedule breakdown reports

Scan schedule breakdown reports are a type of vulnerability report that provide summary, detailed, and variance vulnerability results for  specific scan schedules. For more information, see [Scan Schedule Breakdown](../reports/Vulnerabilities/reports.md#ScanScheduleBreakdown).

## View vulnerability reports

Alert Logic generates several reports based on vulnerabilities detected by scans. Vulnerability reports provide valuable summary, breakdown, variance, distribution, and trending data for vulnerabilities discovered  across applicable scans your environment. You can also view a report that lists when assets in your deployments were last scanned for vulnerabilities. For more information, see [Vulnerabilities Reports](../reports/Vulnerabilities/reports.md).

### View and remediate exposures detected by vulnerability scans

On the Exposures page in the Alert Logic console, you can organize the list by remediations to see the recommended actions you can take to address exposures based on vulnerabilities detected by scans. You can take these actions for the listed remediation:

* Dispose (suppress the vulnerability from view and from reports for a period of time)
* Conclude (complete the remediation action)

The recommended remediations also provide details that include the exposures, affected assets, and evidence of the vulnerability.  For more information, see [Exposures](../exposures.md).
