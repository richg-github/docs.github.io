# Data Center Deployment Configuration (Essentials Subscription)

Alert Logic allows you to add deployments to the Alert Logic console. You can access the Deployments page from the ![](../Resources/Images/dashboard/configure-icon.png)**Configure** menu item in the Alert Logic console. To add a Data Center deployment, click the add icon (![](../Resources/Images/Icons/cdAddPlus.png)), and then click **Data Center**.

## Name your deployment

In the Deployment Name field, type a descriptive name for the deployment you want to create, and then click **SAVE AND CONTINUE**.

## Add assets

Add your assets by network, subnet, domain name, or IP address to be scanned.

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
2. Name the IP address, add the public IP address, and then click **SAVE**.

When you are finished, click **NEXT**.

## Scope of protection

Alert Logic discovers and organizes deployments into a visual topology where you can select the desired levels of protection for your assets.
You can define the scope of your protection per region or network  or subnet. Each network and subnet appears within its protected region. Click a region or individual network or subnet to set the service level  or leave it unprotected, and then click **SAVE**.  You must choose one of the following levels of coverage:* Unprotected
* Alert Logic Essentials coverage

The choices available for scope of protection correspond directly with your entitlement. Although a Professional subscription includes all the features of Essentials, a Professional customer cannot set the protection scope to Essentials unless the account has a separate Essentials subscription.
You can [change the protection level](change-protection.md) later as needed.

### Exclusions

You can exclude assets or ports from external and internal scanning.

#### External scanning

**To exclude assets or ports from external scanning:**

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

    If you exclude assets or ports that are selected  in an active scan schedule in the Scope or Ports tab, the items remain selected   but are not included in future scans.    ## Scan Schedules

Alert Logic performs scans to protect your deployment. When you create a new Data Center deployment, Alert Logic automatically creates a default discovery scan schedule  to find new assets, and it creates default scan schedules to perform external and internal vulnerability scans on all non-excluded assets. The default scan schedules also perform external and internal vulnerability scans on all non-excluded TCP ports and common UDP ports. You can schedule when you want  to perform specific scans for all or selected assets  and ports  from the  **Discovery Scanning**, **Internal Scanning**, and **External Scanning** tabs. For more information, see [Manage Scan Schedules](../analyze/manage-scans-and-results/schedules.md).

    Port selection does not apply to discovery scan schedules.    
After reviewing the schedules and making any changes, click **NEXT**.

## Options

### Configure Cross-Network Protection

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

## Agent-based Scanning

You have the option to enable agent-based scanning. Agent-based scanning improves the efficiency, accuracy, and usability of Alert Logic vulnerability scanning features. Agent-based scanning provides the vulnerability assessment coverage of authenticated network scanning without the need to manage credentials and with a reduction in network traffic and impact. To learn more about agent-based scanning, see [Agent-Based Scanning](../analyze/manage-scans-and-results/agent-based-scan.md).

## Configuration Topology

This topology diagram provides an overview of your scope of protection. You can see which assets are unprotected, or being scanned at the Essentials, Professional, or Enterprise levels.

The protection breakdown displays  how many assets are unprotected, excluded, and protected, along with the number of protected assets in each level.

![](../Resources/Images/TopologyConfigurationOverviewProtectionBreakdown.png)

You can search for specific assets. The protection breakdown updates as it finds specific assets.

## Installation Instructions

### Appliances

You must assign appliances to your networks. Use the Unique Registration Key to assign one or more appliances to each network. For more information, see [Install and Configure the  Physical Appliance](../prepare/alert-logic-physical-appliance.md) or [Install and Configure the  Virtual Appliance](../prepare/virtual-appliance.md).

## Verify the health of your deployment

After you create your deployment, access the Health console in the Alert Logic console to determine the health of your networks, appliances, and agents, and then make any necessary changes.
