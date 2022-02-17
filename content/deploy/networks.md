# Configure and Manage Networks in Data Center Deployments

A  network is a range of IP addresses, expressed in CIDR notation, that you want an appliance to monitor. You can configure a network with a CIDR range up to /8. However, Alert Logic recommends that you configure networks with the smallest subnet blocks that match your environment. Doing so improves visibility into network traffic levels and improves the ability to monitor the health of your environment.

For an appliance to monitor a network, you must assign the network to the same monitoring policy used by the appliance. You may apply multiple networks to a monitoring policy. For more information about monitoring policies, see .

Appliances do not monitor network traffic that does not originate from networks listed in the  monitoring policy used by the appliance. The exception to this rule is traffic from protected hosts, which appliances always monitor.

To see the list of networks in a deployment, click the deployment tile, and then click **Networks and Protected Hosts**.

## Networks list

Networks are listed in the table, sorted by network name. You can search for a specific network or tag, or use the filters to show only networks with specific characteristics.

Click a network in the table to view details about the network, the network status history, and data statistics for the network.

The **Status** column indicates if a network is working or in error. If a network is not attached to a monitoring policy, the status says unprotected.

### Create and protect networks

The Alert Logic console provides two options for network creation. You can create a network from the Monitoring Policies page, or you can create a network from Networks and Hosts.

#### Create a network from the Monitoring Policies page

If you create a network when you create a monitoring policy, you can use a single page in the Alert Logic console to both create the network and create or assign a monitoring policy to the network.

To create a network from the Monitoring Policies page:

1. Click **CONFIGURATION** > **Network IDS**.
2. On the left navigation pane, click **Policies**, and then click **Monitoring**.
3. Click the **Add** icon (![](../Resources/Images/Icons/cdAddPlus.png)).
4. In the **Name** field, type a name for the monitoring policy.
5. Under **Networks**, select **Create new Networks**.
6. In the **Name** box, type a name for the network.
7. In the **CIDR** box, type the network CIDR information.
8. To assign tags to your network, in the **Tags** box, type one or more tags.
If you want to assign more than one tag to the network, you must press **Enter** between each tag name.             12. Select the appliances you want to apply to the monitoring policy.
If you do not select an appliance, the health status of your network appears as "unprotected" on the Networks and Hosts page. 14. Selectwhether you want to use an existing whitelist policy or create a new whitelist policy.
15. Click **SAVE**.

#### Create a network from the Networks and Hosts page

To create and protect a network from Networks and Hosts:

1. Click the **Add** icon (![](../Resources/Images/Icons/cdAddPlus.png)).
2. Choose how you want to input network information. Choose:
   1. **Normal Mode** to enter details about one network at a time.					The **Tags** field is not comma delimited. If you want to assign more than one tag to the network, you must press **Enter** between each tag name.
      1. In the **Name** box, type a name for the network.
      2. In the **CIDR** box, type the network CIDR information.
      3. To assign tags to your network, in the **Tags** box, type one or more tags.
   3. **List Mode** to enter networks by CIDR.
      1. In the **CIDR** box, type the network CIDR information.
      							To enter multiple networks, separate the CIDR addresses with a comma.
4. To monitor the network immediately, use the drop-down to select the appliance that you want to monitor the network.
5. Click **Save**.

    If you do not select an appliance, the health status of your network appears as "unprotected" on the Networks and Hosts page.     ### Edit networks

The  edit feature allows you to perform edits on one or more networks.

**To edit networks**

1. Click the **Add** icon (![](../Resources/Images/Icons/cdAddPlus.png)).
2. In the table of networks, find the network that you want to edit and click the pencil icon (![](../Resources/Images/pencil icon_29x29.png)) in the **Actions** column.
3. Make necessary edits to the following fields:
   * **Name**
   * **CIDR**
   * **Collection Alerts**
   * **Tags**
5. Click **Update**.

### Additional options

You can mass edit networks, export a list of networks, or force a statistics update. To access these options, click the gear icon in the top right corner.

The mass edit and mass archive/delete features have a maximum number of entries that they can handle. If you have an issue using the feature on a large number of entries, use the Alert Logic API instead.

To mass edit networks:

1. From the **Networks** page, click the gear icon, and then click **Mass Edit**.
2. Make the following changes, if applicable:2. Under **Tags**, select a tag option, and then in the Tags field, enter the applicable tag(s).
3. Specify whether you want to delete the selected networks.
   1. Specify whether you want changes applied to the following:
      * **All Networks**
      * **Only Filtered Networks**
      * **Only Selected Networks**
   3. Select an appliance to protect the specified networks.
4. Click **Save**.

### Export networks

You can export your list of networks to a file.

To export networks:

1. From the **Networks** page, click the gear icon, and then select **Export Networks**.
2. Choose whether you want to export a list of all networks or only filtered networks.
3. Select a format for the exported file:
   * Comma separated values (.csv)
   * Tab delimited values (.txt)
   * Microsoft Excel 1997–2003 (.xls)
   * Microsoft Excel 2007 (.xlsx)
5. Click **Export**.

### Force statistics update

The Alert Logic console automatically updates network details and statistics every 30 minutes. You can manually force a statistics update to refresh the network screen display.

To force a statistics update:

From the **Networks** page, click the gear icon, and then click **Force Statistics Update**.
