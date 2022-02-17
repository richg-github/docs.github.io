# Adjust Scan Settings

You can  adjust scan settings  for specific assets from  the Topology page in the Alert Logic console. The Topology page organizes your assets in an interactive diagram that you can filter and customize. For more information, see [Topology](../topology.md).

Adjustments you can make to scans from the Topology page include:

* [Manage your credentials](#Manageyourcredentials)
* [Adjust scan performance](#Adjustscanperformance)
* [Scan Now](#ScanNow)

### Manage your credentials

You can add credentials to your assets to use with internal vulnerability scans on the Topology page. If you provide credentials, Alert Logic performs comprehensive authenticated vulnerability checks using package information and other local sources of data. If you do not provide credentials,  scans on your assets occur using only methods available to unauthenticated users.

To access the Topology page, click ![](../../Resources/Images/dashboard/investigate-icon.png)**Investigate**, and then click **Topology**.

**To manage your credentials**:

1. On the Topology page, specify a deployment or region in the respective drop-down menus.
2. Click on the asset for which you want to manage credentials, and then in the slideout panel, click **Scan Settings**.
3. Click **ADD CREDENTIAL**, and then enter the required fields.
4. Click **ADD CREDENTIAL** to save your credentials.

### Adjust scan performance

For discovery scans, Alert Logic scans a maximum of ten 256-IPv4 CIDR blocks concurrently by default. For internal and external vulnerability scans, the maximum number of IPs scanned concurrently is ten by default.

You can choose fewer concurrent scans to reduce scan traffic. Choosing a lower number results in slower scans and a longer scan duration. For faster scans and a shorter scan duration, you can choose a higher number of concurrent scans (up to 20).  The number you choose is a maximum limit—the actual number of concurrent scans   does not exceed the selected amount and depends on factors such as appliance resource availability and network bandwidth during the scan window.

**To adjust scan performance:**

1. On the Topology page, specify a deployment or region in the respective drop-down menus.
2. Click on the asset for which you want to adjust scan performance, and then in the slideout panel, click **Scan Settings**.
3. In the Discovery area, enter a number from 1 (slower scans) through 20 (faster scans). The default is 10 maximum concurrent CIDR blocks scanned.
4. In the Vulnerability area, enter a number from 1 (slower scans) through 20 (faster scans). The default is 10 maximum concurrent IPs scanned.
5. Click **SAVE** to save your selections.

### Scan Now

If you need to run a scan immediately, you can use the Scan Now feature on the Topology page. This feature scans the selected host right away or as soon as possible, outside the normal schedule.

    For hosts with [Agent-Based Scanning](agent-based-scan.md), Scan Now triggers an agent-based scan at the same time as the network scan. The results of both scan devices are merged once the l network scan completes.    
To see which scans are in progress, click the scan icon (![](../../Resources/Images/Icons/icon-scan-map.PNG)) to see the scan statuses of your assets. For more information about scan status, see [Customize the diagram display](../topology.md#customize-display).

**To use the Scan Now feature:**

1. On the Topology page, specify a deployment or region in the respective drop-down menus.
2. Click the host you want to scan immediately, if a scan is not in progress.
3. In the slideout panel, click **Actions**, and then click **SCAN NOW**.
If the host is excluded from scanning in the deployment scope of protection, a message prompts you to confirm whether to continue with the scan. If ports are excluded, a message prompts you to choose whether to honor or override the exclusions. If you choose to honor exclusions, the scanner does not scan the excluded ports.
4. Click **OK** to run the scan.

Scan Now may delay the scan for 5-25 minutes, depending on technological factors such as the current load on the scanner and the availability of a scan appliance. Alert Logic will always scan the host as soon as possible.
