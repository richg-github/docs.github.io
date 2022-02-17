# Alert Logic Data Center Deployment for Oracle Cloud 

Oracle Cloud Platform is a comprehensive, standards-based combination of Oracle3 and open source technologies to enable you to more efficiently build, deploy, integrate, secure and manage all your enterprise applications.

Alert Logic allows you to use a Data Center deployment to monitor your assets on the Oracle Cloud Platform. Before your deployment can monitor your assets, you must install an Alert Logic appliance and agents to your Oracle Cloud environment.

## Create a Data Center deployment for your Oracle Cloud assets

The appliance claim process requires information from your Alert Logic account, so you should create the Data Center deployment prior to creating and claiming the appliance VMs.

The Deployments page appears under the Configuration tab in the Alert Logic console. To add a Data Center deployment, click the add icon (![](../Resources/Images/Icons/cdAddPlus.png)), and then click **Data Center**.

### Name your deployment

In the Deployment Name field, type a descriptive name for the deployment you want to create, and then click **SAVE AND CONTINUE**.

### Add assets

For Data Center deployments, Alert Logic suggests you add your assets using discovery scans. While you   can add your assets manually, weekly discovery scans ensure your Data Center deployments are configured with the right ranges.

You can manualy add your assets by network, subnet, domain name, or IP address to be scanned. Add the requested information for every virtual network and subnet you want to monitor.

**To add a network:**

1. In the **Networks** tab, click the add icon (![](../Resources/Images/Icons/cdAddPlus.png)), and then select **Network**.
2. Type a name for the network, and add the **Private CIDR(s)** for each subnet.
Alert Logic recommends you add multiple /24 or smaller subnets instead of a CIDR over /16 to allow Alert Logic to operate and scan faster.
3. Select **Do not use agents for IDS traffic. My network automatically forwards traffic to my appliances through a port mirroring feature.** if your network equipment is configured to SPAN or another port mirroring feature.

A SPAN configured network forwards your Network IDS traffic to Alert Logic appliances, which allows Alert Logic to analyze that traffic.5. Click **SAVE**.

**To add a subnet:**

1. In the **Networks** tab, click the add icon (![](../Resources/Images/Icons/cdAddPlus.png)), and then select **Subnet**.
2. Name the subnet, select the network, add the **Private CIDR**, and then click **SAVE**.

**To add a domain name**:

1. In the **DNS Names and Public IPs** tab, click the add icon (![](../Resources/Images/Icons/cdAddPlus.png)), and then select **DNS Name**.
2. Add the domain name, and then click **SAVE**.

**To add an IP address: **

1. In the **DNS Names and Public IPs** tab, click the add icon (![](../Resources/Images/Icons/cdAddPlus.png)), and then select **Public IP**.
2. Name the IP address, add the CIDR, and then click **SAVE**.

When you are finished, click **NEXT**.

### Scope of protection

Alert Logic discovers and organizes deployments into a visual topology where you can select the desired levels of protection for your assets.

You can define the scope of your protection per region or network  or subnet. Each network and subnet appears within its protected region. Click a region or individual network or subnet to set the service level  or leave it unprotected, and then click **SAVE**.  You must choose one of the following levels of coverage:

* Unprotected

The choices available for scope of protection correspond directly with your entitlement. Although a Professional subscription includes all the features of Essentials, a Professional customer cannot set the protection scope to Essentials unless the account has a separate Essentials subscription.

You can [change the protection level](change-protection.md) later as needed.

#### Exclusions

You also have the option to exclude assets or tags from external scanning, internal scanning, and Network IDS.

External scanning

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

    If you exclude assets or ports that are selected in the Scope or Ports tab in an active scan schedule, the assets or ports remain selected   but are not included in future scans.    
**Internal scanning**

**To exclude assets or  tags for internal scanning**:

1. Select the **Internal Scanning** tab, and then click **ASSETS** or **TAGS** to search for assets or tags available to exclude.
2. Click **EXCLUDE** for the asset or  tag you want to exclude.                 You can remove an asset from the exclusion list at any time to include the asset in scanning. To remove an asset from the exclusion list, click **CANCEL**.
3. After you apply all the necessary exclusions, click out of **Exclusions**, and then on the **Scope of Protection** page, click **SAVE**.

Network IDS** Whitelist**

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

### Scheduling 

Alert Logic automatically performs certain scans. You can schedule how often and when you want Alert Logic to scan for new assets from the **Discovery Scans** tab and to scan for vulnerabilities from the **Internal Scans** and **External Scans** tabs.

#### Discovery scans

* **Scan once a day**

To schedule when you want  to scan for new assets, choose one of the following options:

* **Scan only during certain times**

Click **SAVE**, and then click **NEXT**.

#### Internal scans and External scans

To schedule how often you want  to scan for vulnerabilities, choose one of the following options:

* **Scan as often as necessary**
* Scan once a day
* Scan once a week
* Scan once a month

<!--<MadCap:snippetBlock src="../Resources/Snippets/Deployments/vulnerability-scans-when.flsnp" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />-->
Click **SAVE**, and then click **NEXT**.

### Options

#### Configure Cross-Network Protection

You have the option to set up Cross-Network Protection to create connections across networks, in the same or different deployment, but within the same account. Cross-Network Protection allows other networks to use resources from a protecting network with an assigned network appliance. The common places for  Cross-Network Protection use are Amazon Web Services (AWS) VPC Peering, AWS Transit Gateway, and Microsoft Azure VNet Peering.

A protecting network hosts the appliance. The network protected by the  protecting network is the protected network. For more information on Cross-Network Protection, see [Cross-Network Protection](cross-network-protection.md).

**To configure Cross-Network Protection:**

1. On the side navigation, click **Options** under **Protection**.
2. On the Cross-Network Protection tab, click the network or region you want to protect in the topology diagram, or in the **Search Assets** field, search for the network or region you want to protect.
3. Click the search field to search or type the name of a protecting network, and then select one.
4. Click **SAVE**.

The protecting network and protected network are now visible in the topology diagram with distinguishing icons. The Cross-Network Protection** Breakdown**, on the top left of the topology graph, provides an overview of your Cross-Network Protection connections.

#### View protected networks 

**To view protected networks**:

1. Click the protecting network icon (![](../Resources/Images/Cross-network-protection/protecting-another-network.png)) to see the number of protected networks currently connected.
2. Click the details icon (![](../Resources/Images/Cross-network-protection/View-networks-protecting-this-network_27x22.png)) to see a slideout panel that contains  protected network names.

#### View protecting networks 

To view protecting networks, click the protected network icon (![](../Resources/Images/Cross-network-protection/protected-by-another-network.png)).

### Configuration Topology

This topology diagram provides an overview of your scope of protection. You can see which assets are unprotected, or being scanned at the Essentials, Professional, or Enterprise levels.

The protection breakdown displays  how many assets are unprotected, excluded, and protected, along with the number of protected assets in each level.

![](../Resources/Images/TopologyConfigurationOverviewProtectionBreakdown.png)

You can search for specific assets. The protection breakdown updates as it finds specific assets.

## Upload the Alert Logic appliance image to Oracle Cloud

1. Download the latest [Alert Logic Virtual Appliance](https://docs.alertlogic.com/prepare/virtual-appliance.htm#Downloadthevirtualappliance).
2. Log into the [Oracle Cloud Console](https://cloud.oracle.com/en_US/sign-in).
3. In the Oracle console, browse to **Object Storage** and click **Create Bucket**.
4. Click **Upload Object**, and then select the Alert Logic virtual appliance.

## Import the Alert Logic appliance 

1. In the Oracle Cloud Console, open the navigation menu.
2. Under **Core Infrastructure**, select **Compute**, and then click **Custom Images**.
3. Click **Import Image**.
4. Select the compartment where you want to import the image.
5. Type a name for the image.
6. Specify the Object Storage URL where you stored the image. You must specify a preauthenticated request URL. You can find the object URL under the information section of the Object in the Bucket.
7. Select the image format.
8. Select **PARAVIRTUALIZED MODE**.
9. Apply tags, if needed.
10. Click **Import Image**.

The appliance appears in the Custom Images list for the compartment. When the import is complete, the status changes from "IMPORTING" to "AVAILABLE."

## Create the instance in Oracle Cloud

1. Open the navigation menu. Under Core Infrastructure, go to Compute and click Custom Images. Find the custom image you want to use.
2. Click the Actions icon (three dots), and then click Create Instance.
3. Provide additional launch options as described in Creating an Instance section of the Oracle Documentation.

## Update the Alert Logic firewall rules

Ensure the proper firewall rules are in place for the appliance. For information about firewall rules, see [Alert Logic Firewall Rules](https://docs.alertlogic.com/requirements/us-firewall-rules.htm).

Refer to the [Oracle Cloud Route Tables](https://docs.cloud.oracle.com/iaas/Content/Network/Tasks/managingroutetables.htm) documentation to add ingress and egress rules for your appliance network.

## Claim Alert Logic appliance

Before you can claim the Alert Logic appliance through Oracle Cloud, you must retrieve your Alert Logic Unique Registration ID. The Unique Registration ID is available only through the primary customer account. If your customer account is not the primary account, contact your account administrator for this information.

**To retrieve your Unique Registration ID:**

1. In the Alert Logic console, click the Settings icon (![](../Resources/Images/supportThreeDots.png)), and then select **Support Information**.
2. Copy your Unique Registration Key.

**To claim your appliance:**

1. In your browser, type: <kbd>http://&amp;lt;YourOracleApplianceIPAddress&amp;gt;</kbd>.
2. In **Unique Registration ID**, paste your unique registration key.
3. Click **Start Claim Process**.

To view your appliance provisioning status, click **Go To Detailed Status**.

## Install the agent

Alert Logic provides a single agent that collects data used for analysis, such as log messages and network traffic, metadata, and host identification information. Click the links below for more information and to download the appropriate agent:

* [Install the Alert Logic Agent for Linux](../prepare/alert-logic-agent-linux.md)
* [Install the Alert Logic Agent for Windows](../prepare/alert-logic-agent-windows.md)

## Configure log sources

If you have a Professional subscription, you can set up log collection. To add log sources for data you want to collect, see [Log Sources](log-sources.md#top).

## Verify the health of your deployment

After you create your deployment, access the Health console in the Alert Logic console to determine the health of your networks, appliances, and agents, and then make any necessary changes.

## Additional Oracle references

The following references to Oracle documentation provide additional information:

* [https://docs.cloud.oracle.com/iaas/Content/Compute/Tasks/importingcustomimage.htm](https://docs.cloud.oracle.com/iaas/Content/Compute/Tasks/importingcustomimage.htm)
* [https://docs.cloud.oracle.com/iaas/Content/Compute/Tasks/launchinginstance.htm](https://docs.cloud.oracle.com/iaas/Content/Compute/Tasks/launchinginstance.htm)
* [https://docs.cloud.oracle.com/iaas/Content/Compute/References/customimagesparavirtualizedmode.htm](https://docs.cloud.oracle.com/iaas/Content/Compute/References/customimagesparavirtualizedmode.htm)
