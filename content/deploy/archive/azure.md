# Microsoft Azure Deployment Configuration

Alert Logic allows you to add Microsoft Azure deployments to the Alert Logic console. The Deployments page appears under the Configuration tab in the Alert Logic console. To add a deployment, click the add icon (![](../../Resources/Images/Icons/cdAddPlus.png)), and then enter the requested information to provide Alert Logic with third-party access to the specified cloud environment. For more information about adding deployments for other cloud environments, see [Amazon Web Services (AWS) (AWS) Deployment Configuration](aws.md) and [Data Center Deployment Configuration (Essentials Subscription)](../data-center-essentials.md).

## Name your deployment

In the Deployment Name field, type a descriptive name for the deployment you want to create, and then click **SAVE AND CONTINUE**.

## Allow access to Azure subscription

To protect your Azure deployment, you must set up an Azure RBAC role to allow Alert Logic to access your account. Fill out the required fields, and then click **SAVE**. If you need help, see [Configure App Registration and RBAC for Microsoft Azure Resources](../../prepare/azure-rbac-role-setup.md).

## Asset Discovery

Allow Alert Logic a moment to discover your assets. When discovery is complete, click **CONTINUE**. Alert Logic displays the assets discovered in your account in topology diagrams. To learn more about topology, click [Topology](../../analyze/topology.md).

### Add external assets

You can add external assets by domain name or IP address. Alert Logic will scan these external assets that you define.

    External assets are also used for non-PCI external scans.     
**To add external assets:**

1. Click the Add icon (![](../../Resources/Images/Icons/cdAddPlus.png)) and choose the DNS name or IP address.
   * If you chose the DNS name, enter your fully-qualified domain name in the field.
   * If you chose IP address, name your external IP address, and then enter the IP address in the field.
3. Click **SAVE**.

## Scope of protection

Alert Logic discovers and organizes deployments into a visual topology where you can select the desired levels of protection for your assets.

You can define the scope of your protection per region or network  or subnet. Each network and subnet appears within its protected region. Click a region or individual network or subnet to set the service level  or leave it unprotected, and then click **SAVE**. You can also use tags  in the internal scanning tab of **EXCLUSIONS** to exclude assets from scanning, including subnets. You must choose one of the following levels of coverage:

* Unprotected
* Alert Logic Essentials coverage
* Alert Logic Professional coverage
* Alert Logic Enterprise coverage

The choices available for scope of protection correspond directly with your entitlement. Although a Professional subscription includes all the features of Essentials, a Professional customer cannot set the protection scope to Essentials unless the account has a separate Essentials subscription. Likewise, an Enterprise customer cannot set the protection scope to Essentials or Professional unless the account has separate subscriptions for those.

You can [change the protection level](../change-protection.md) later as needed.

### Exclusions

You also have the option to exclude assets or Azure tags from external scanning, internal scanning, and Network IDS.

#### External scanning

1. Click **EXCLUSIONS**.
2. Click the **External Scanning** tab.
3. To exclude assets, click **ASSETS** to search for available assets to exclude, and then click **EXCLUDE** for the asset you want to exclude.               You can remove an asset from the exclusion list at any time to include the asset in scanning. To remove an asset from the exclusion list, click **CANCEL**.
4. To exclude ports, click **PORTS**, and then do the following:
   1. Search for the host, subnet, or network that has the ports you want to exclude from external scanning.
   2. In the **Protocol** field, select the port protocol: **UDP** or **TCP**.
   3. Enter one or more ports that you want to exclude. Use a dash or colon to indicate a range  (for example, 1-10001). Separate multiple ports or port ranges with a comma (for example, 11234, 11311, 12000-12010).
   4. Click **EXCLUDE AND ADD ANOTHER**.
      You can remove ports from the exclusion list at any time to include the ports in scanning. To remove ports from the exclusion list, click **REMOVE**.      9. After you apply your exclusions, close the **Exclusions** window.
10. On the **Scope of Protection** page, click **SAVE**.

    If you exclude assets or ports that are selected in the Scope or Ports tab in an active scan schedule, the assets or ports remain selected   but are not included in future scans.    #### Internal scanning

To exclude assets or ports from internal scanning:

1. Click **EXCLUSIONS**.
2. Click the **Internal Scanning** tab.
3. To exclude assets, click **ASSETS** to search for available assets to exclude, and then click **EXCLUDE** for the asset you want to exclude.                 You can remove an asset from the exclusion list at any time to include the asset in scanning. To remove an asset from the exclusion list, click **CANCEL**.
4. To exclude ports, click **PORTS**, and then do the following:
   1. Search for the host, subnet, or network that has the ports you want to exclude from internal scanning.
   2. In the **Protocol** field, select the port protocol: **UDP** or **TCP**.
   3. Enter one or more ports that you want to exclude. Use a dash or colon to indicate a range  (for example, 1-10001). Separate multiple ports or port ranges with a comma (for example, 11234, 11311, 12000-12010).
   4. Click **EXCLUDE AND ADD ANOTHER**.
      You can remove ports from the exclusion list at any time to include the ports in scanning. To remove ports from the exclusion list, click **REMOVE**.      9. After you apply your exclusions, close the **Exclusions** window.
10. On the **Scope of Protection** page, click **SAVE**.

    If you exclude assets or ports that are selected  in an active scan schedule in the Scope or Ports tab, the items remain selected   but are not included in future scans.    #### Network IDS Whitelist

**To whitelist assets from Network IDS:**

1. Click **EXCLUSIONS**.
2. Select the **Network IDS Whitelist** tab to exclude CIDRs.
3. In the **Network(s)** field, click the drop-down menu to select a network or leave **All networks** selected.
4. In the **Protocol(s)** field, click the drop-down menu to select a protocol.  Select **TCP**, **UDP**, or **ICMP**, or  select ***** to select all IP protocols.
5. Enter the network CIDR network address you want to exclude. You must enter a range of network addresses using CIDR format.
Enter 10.0.0.0/24 to exclude IP addresses in the range 10.0.0.0-10.0.0.255.
6. Click the drop-down menu to select the port. You can enter a single port, a port range, or ***** to select all ports.             
Enter 443 for a single port. Enter 1:1024 for a port range.
7. Click **EXCLUDE AND ADD ANOTHER**. Repeat the steps to add more CIDRs.               You can remove an asset from the exclusion list at any time  to include the asset in scanning. To remove an asset from the exclusion list, click **REMOVE**.
8. After you apply all the necessary exclusions, close  the **Exclusions** window.
9. On the **Scope of Protection** page, click **SAVE**.

## Scheduling

Alert Logic automatically performs certain scans. You can schedule how often and when you want Alert Logic  to scan for vulnerabilities from the **Internal Scanning** and **External Scanning** tabs.

### Internal scans and External scans

To schedule how often you want  to scan for vulnerabilities, choose one of the following scan frequency options:

* **Scan as often as necessary**—Select this option if you want  to scan known assets for vulnerabilities once a day or, if significant changes  to an asset are detected, twice a day.—Select this option if you want  to scan assets for vulnerabilities up to twice  a day or when significant changes  to an asset are detected, such as the addition of a network. This option automatically scans all the assets you selected on the Scope tab at least once in a 24-hour period. The option attempts a second scan depending on resources and changes to your environment. Scans on networks or hosts added that day, for example, occur immediately and take priority over second scans. Assets that were not scanned twice take priority the next day.
* Scan once a day
* Scan once a week
* Scan once a month
* **Scan once**—Select this option if you want to scan assets selected on the Scope tab once, starting at a specific time. For example, to verify a patch or remediation action, you could use this option to schedule a scan of several assets to start within the next five minutes  instead of waiting for the next regularly scheduled scan.

To schedule when you want  to scan for vulnerabilities, choose one of the following options:

* **Scan whenever necessary**—Select this option if you do not want to limit  scans to particular days or times.
* **Scan only during certain times on certain days**
* **Scan only on a certain day** (AWS and Azure deployments only)

To schedule when you want  to scan for vulnerabilities, choose one of the following scan window options:

* **Scan any time**—Select this option if you do not want to limit  scans to certain days or times.
* **Scan only during certain times**—Select this option to choose the specific days and hours for this scan. You can define multiple scan windows if you chose **Scan as often as necessary**, **Scan once a week**, or **Scan once a month** as the frequency.
* **Scan only during certain times on certain days** (available if you choose **Scan once a month** as the scan frequency)

If you chose **Scan once** as the frequency, specify the time zone, start day and time, and an option for the end day and time for the scan:

* **Scan until done**
* **Specify end date and time**

Click **SAVE**, and then click **NEXT**.

## Options

### Configure Cross-Network Protection

You have the option to set up Cross-Network Protection to create connections across networks, in the same or different deployment, but within the same account. Cross-Network Protection allows other networks to use resources from a protecting network with an assigned network appliance. The common places for  Cross-Network Protection use are Amazon Web Services (AWS) VPC Peering, AWS Transit Gateway, and Microsoft Azure VNet Peering.

A protecting network hosts the appliance. The network protected by the  protecting network is the protected network. For more information on Cross-Network Protection, see [Cross-Network Protection](../cross-network-protection.md).

Only manual mode deployments have the Cross-Network Protection option.

**To configure Cross-Network Protection:**

1. On the side navigation, click **Options** under **Protection**.
2. On the Cross-Network Protection tab, click the network or region you want to protect in the topology diagram, or in the **Search Assets** field, search for the network or region you want to protect.
3. Click the search field to search or type the name of a protecting network, and then select one.
4. Click **SAVE**.

The protecting network and protected network are now visible in the topology diagram with distinguishing icons. The Cross-Network Protection** Breakdown**, on the top left of the topology graph, provides an overview of your Cross-Network Protection connections.

#### View protected networks 

**To view protected networks**:

1. Click the protecting network icon (![](../../Resources/Images/Cross-network-protection/protecting-another-network.png)) to see the number of protected networks currently connected.
2. Click the details icon (![](../../Resources/Images/Cross-network-protection/View-networks-protecting-this-network_27x22.png)) to see a slideout panel that contains  protected network names.

#### View protecting networks 

To view protecting networks, click the protected network icon (![](../../Resources/Images/Cross-network-protection/protected-by-another-network.png)).

## Configuration Topology

This topology diagram provides an overview of your scope of protection. You can see which assets are unprotected, or being scanned at the Essentials, Professional, or Enterprise levels. Click a VNet in the diagram to view its subnets, instances, and hosts.

The protection breakdown displays  how many assets are unprotected, excluded, and protected, along with the number of protected assets in each level.

![](../../Resources/Images/TopologyConfigurationOverviewProtectionBreakdown.png)

## Deploy IDS appliances

Azure deployments require that you deploy an IDS appliance into each VNet you want to protect.

You must set up your RBAC role before you deploy the IDS appliance. If you do not set up your RBAC role Alert Logic cannot claim the appliance. For more information about RBAC role configuration, see [Configure App Registration and RBAC for Microsoft Azure Resources](../../prepare/azure-rbac-role-setup.md#top).

**To deploy an Azure IDS appliance:**

1. Log into the [Azure portal](https://portal.azure.com/).
2. From the Azure Dashboard, click **All services**, and then click **Marketplace**.
3. In the Marketplace search bar, type <kbd>Alert Logic</kbd>, and then select one of the following:
   * Alert Logic MDR Professional** BYOL**
   * Alert Logic MDR Enterprise** BYOL**
   If you are an Alert Logic MDR Essentials customer, select Alert Logic MDR Professional** BYOL**.
5. Click **Create**.
6. On the Basics page, provide the following information:
   1. Click **Next : Disks**.
   1. In the **Virtual machine name** field, type a name for the IDS appliance.
   2. From the **Region** drop-down menu, select the region where you want to create the IDS appliance.
   3. From the **Availability options** drop-down menu, select **No infrastructure redundancy required**.
   4. From the **Image** drop-down menu, keep the default selection.
   5. From the **Size** drop-down menu you can:
      * Keep the default.
      * For an Essentials subscription, select **A2_v2**.
      * For a Professional subscription select  **A4_v2**, which is the smallest fully-supported IDS appliance size.
      * For a Professional or Enterprise subscription with many hosts with agents, select, **A8_v2**.If you require additional capacity, Alert Logic recommends that you deploy another IDS appliance, which is less costly than a more powerful single appliance.
   7. For **Authentication type**, select **Password**.
   8. In the **Username** field, type a user name for the appliance
   9. In the **Password** field, type a password for the appliance, and then type the password again to confirm the password. The user name and password are an Azure requirement to create and deploy the appliance. Alert Logic does not use these credentials, or provide you with SSH access to the appliance.
   1. From the **Subscription** drop-down menu, select the appropriate Azure subscription.
   2. Under the **Resource group** drop-down menu, click **Create new**.
   Do not choose an existing resource group. If the appliance deployment is not successful, Azure will save the changes made to an existing resource group, and you will have to manually revert all changes. 
10. On the Disks page, click **Next : Networking**.
11. On the Networking page, provide the following information:
   1. Keep the default settings for:
      * Configure network security group
      * Accelerated networking
      * Load balancing
   1. From the **Subnet** drop-down menu, select the subnet where you want to deploy the appliance.
   2. From the **Public IP** drop-down menu, select the public IP address you want to use, or create a new public IP if needed.
   If you create a new public IP, you may keep the defaults.
   1. From the **Virtual network** drop-down menu, select the VNet where you want to deploy the IDS appliance.
   When you created the resource group, you created a new VNet. Do not select the VNet created with the resource group.
15. Click **Next : Management**.
16. On the Management page, click **Next : Advanced**.
17. On the Advanced page, click **Next : Tags**.
18. On the Tags page, you can create tags, but they are not required.
19. Click **Review + create**.
20. Review your settings, make any necessary changes, and then click **Create**.

    Deployment of the IDS appliance can take up to five minutes. The appliance can take up to 35 minutes for Alert Logic to auto claim.    ## Installation instructions

### Agents

Alert Logic provides a single agent that collects data used for analysis, such as log messages and network traffic, metadata, and host identification information. Click the links below for more information and to download the appropriate agent:

* [Install the Alert Logic Agent for Linux](../../prepare/alert-logic-agent-linux.md)
* [Install the Alert Logic Agent for Windows](../../prepare/alert-logic-agent-windows.md)

## Log sources

If you have a Professional subscription, you can set up log collection. To add log sources for data you want to collect, see [Log Sources](../log-sources.md#top).

## Verify the health of your deployment

After you create your deployment, access the Health console in the Alert Logic console to determine the health of your networks, appliances, and agents, and then make any necessary changes.
