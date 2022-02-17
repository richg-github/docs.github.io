# Microsoft Azure Deployment Configuration (Essentials Subscription)

Alert Logic allows you to add Microsoft Azure deployments to the Alert Logic console. You can access the Deployments page from the ![](../Resources/Images/dashboard/configure-icon.png)**Configure** menu item in the Alert Logic console. To add a deployment, click the add icon (![](../Resources/Images/Icons/cdAddPlus.png)), and then enter the requested information to provide Alert Logic with third-party access to the specified cloud environment.

## Name your deployment

In the Deployment Name field, type a descriptive name for the deployment you want to create, and then click **SAVE AND CONTINUE**.

## Allow access to Azure subscription

To protect your Azure deployment, you must set up an Azure RBAC role to allow Alert Logic to access your account. Fill out the required fields, and then click **SAVE**. If you need help, see [Configure App Registration and RBAC for Microsoft Azure Resources](../prepare/azure-rbac-role-setup.md).

## Asset Discovery

Allow Alert Logic a moment to discover your assets. When discovery is complete, click **CONTINUE**. Alert Logic displays the assets discovered in your account in topology diagrams. To learn more about topology, click [Topology](../analyze/topology.md).

### Add external assets

You can add external assets by domain name or IP address. Alert Logic will scan these external assets that you define.

    External assets are also used for non-PCI external scans.     
**To add external assets:**

1. Click the Add icon (![](../Resources/Images/Icons/cdAddPlus.png)) and choose the DNS name or IP address.
   * If you chose the DNS name, enter your fully-qualified domain name in the field.
   * If you chose IP address, name your external IP address, and then enter the IP address in the field.
3. Click **SAVE**.

## Scope of protection

Alert Logic discovers and organizes deployments into a visual topology where you can select the desired levels of protection for your assets.

You can define the scope of your protection per region or network. Each network  appears within its protected region. Click a region or individual network to set the service level  or leave it unprotected, and then click **SAVE**.  You must choose one of the following levels of coverage:

* Unprotected
* Alert Logic Essentials coverage

The choices available for scope of protection correspond directly with your entitlement. Although a Professional subscription includes all the features of Essentials, a Professional customer cannot set the protection scope to Essentials unless the account has a separate Essentials subscription. Likewise, an Enterprise customer cannot set the protection scope to Essentials or Professional unless the account has separate subscriptions for those.

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

Alert Logic performs scans to protect your deployment. When you create a new deployment, Alert Logic automatically creates default scan schedules to perform external and internal vulnerability scans on all non-excluded assets. The default scan schedules also perform external and internal vulnerability scans on all non-excluded TCP ports and common UDP ports. You can schedule when you want  to perform specific scans for all or selected assets  and ports  from the **Internal Scanning** and **External Scanning** tabs. For more information, see [Manage Scan Schedules](../analyze/manage-scans-and-results/schedules.md).

After reviewing the schedules and making any changes, click **NEXT**.

## Agent-based Scanning

You have the option to enable agent-based scanning. Agent-based scanning improves the efficiency, accuracy, and usability of Alert Logic vulnerability scanning features. Agent-based scanning provides the vulnerability assessment coverage of authenticated network scanning without the need to manage credentials and with a reduction in network traffic and impact. To learn more about agent-based scanning, see [Agent-Based Scanning](../analyze/manage-scans-and-results/agent-based-scan.md).

## File Integrity Monitoring (FIM)

FIM allows you to monitor changes to files and directories of assets in your deployments. You can configure monitoring or exclusions for specific file paths or entire directories  in your Windows and Linux systems.

FIM is composed of two subsections: Monitoring and Exclusions. On the **Monitoring** page, you can set up files and directories for monitoring from the default file types listed on the page. In the **Exclusions** page, you can exclude files and directories  from monitoring, which will override a previously configured file monitoring setup. For more information, see [File Integrity Monitoring ](../configure/file-integrity-monitoring.md).

After creating FIM or exclusion setups, click **NEXT**.

## Options

### Configure Cross-Network Protection

You have the option to set up Cross-Network Protection to create connections across networks, in the same or different deployment, but within the same account. Cross-Network Protection allows other networks to use resources from a protecting network with an assigned network appliance. The common places for  Cross-Network Protection use are Amazon Web Services (AWS) VPC Peering, AWS Transit Gateway, and Microsoft Azure VNet Peering.

A protecting network hosts the appliance. The network protected by the  protecting network is the protected network. For more information on Cross-Network Protection, see [Cross-Network Protection](cross-network-protection.md).

Only manual mode deployments have the Cross-Network Protection option.

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

## Configuration Topology

This topology diagram provides an overview of your scope of protection. You can see which assets are unprotected, or being scanned at the Essentials, Professional, or Enterprise levels. Click a VNet in the diagram to view its subnets, instances, and hosts.

The protection breakdown displays  how many assets are unprotected, excluded, and protected, along with the number of protected assets in each level.

![](../Resources/Images/TopologyConfigurationOverviewProtectionBreakdown.png)

## Deploy appliances

Azure deployments require that you deploy an appliance into each VNet you want to scan.

You must set up your RBAC role before you deploy the scanning appliance. If you do not set up your RBAC role, Alert Logic cannot claim the appliance. For more information about RBAC role configuration, see [Configure App Registration and RBAC for Microsoft Azure Resources](../prepare/azure-rbac-role-setup.md#top).

**To deploy an Azure scanning appliance:**

1. Log into the [Azure portal](https://portal.azure.com/).
2. From the Azure Dashboard, click **All services**, and then click **Marketplace**.
3. In the Marketplace search bar, type <kbd>Alert Logic</kbd>, and then select Alert Logic MDR Professional** BYOL**.
4. Click **Create**.
5. On the Basics page, provide the following information:
   1. Click **Next : Disks**.
   1. In the **Virtual machine name** field, type a name for the scanning appliance.
   2. From the **Region** drop-down menu, select the region where you want to create the scanning appliance.
   3. From the **Availability options** drop-down menu, select **No infrastructure redundancy required**.
   4. From the **Image** drop-down menu, keep the default selection.
   5. From the **Size** drop-down menu, select **F2s_v2**. For more information, see [Requirements for Managed Detection and Response for Microsoft Azure](../requirements/microsoft-azure.md).
   6. For **Authentication type**, select **Password**.
   7. In the **Username** field, type a user name for the appliance
   8. In the **Password** field, type a password for the appliance, and then type the password again to confirm the password. The user name and password are an Azure requirement to create and deploy the appliance. Alert Logic does not use these credentials or provide you with SSH access to the appliance.
   1. From the **Subscription** drop-down menu, select the appropriate Azure subscription.
   2. Under the **Resource group** drop-down menu, click **Create new**.
   Do not choose an existing resource group. If the appliance deployment is not successful, Azure will save the changes made to an existing resource group, and you will have to manually revert all changes. 
9. On the Disks page, click **Next : Networking**.
10. On the Networking page, provide the following information:
   1. Keep the default settings for:
      * Configure network security group
      * Accelerated networking
      * Load balancing
   1. From the **Subnet** drop-down menu, select the subnet where you want to deploy the appliance.
   2. From the **Public IP** drop-down menu, select **None**.
   1. From the **Virtual network** drop-down menu, select the VNet where you want to deploy the scanning appliance.
   When you created the resource group, you created a new VNet. Do not select the VNet created with the resource group.
14. Click **Next : Management**.
15. On the Management page, click **Next : Advanced**.
16. On the Advanced page, click **Next : Tags**.
17. On the Tags page, you can create tags, but they are not required.
18. Click **Review + create**.
19. Review your settings, make any necessary changes, and then click **Create**.

    Deployment of the scanning appliance can take up to five minutes. The appliance can take up to 35 minutes for Alert Logic to auto claim.    ## Install agents

Alert Logic provides a single agent for metadata and host identification information. Click the links below for more information and to download the appropriate agent:

* [Install the Alert Logic Agent for Linux](../prepare/alert-logic-agent-linux.md)
* [Install the Alert Logic Agent for Windows](../prepare/alert-logic-agent-windows.md).

## Update the Alert Logic agent firewall rules

Ensure the proper outbound firewall rules are in place for the node where you installed the agent. For information about firewall rules, see[Alert Logic Firewall Rules](https://docs.alertlogic.com/requirements/us-firewall-rules.htm).

## Update the Alert Logic appliance firewall rules

If you used a Terraform template provided by Alert Logic for your appliance installation, you do not need to perform this step.

Ensure the proper inbound and outbound firewall rules are in place for the appliance. For information about firewall rules, see [Alert Logic Firewall Rules](https://docs.alertlogic.com/requirements/us-firewall-rules.htm).

## Log sources

If you have a Professional subscription, you can set up log collection. To add log sources for data you want to collect, see [Log Sources](log-sources.md#top).

## Verify the health of your deployment

After you create your deployment, access the Health console in the Alert Logic console to determine the health of your networks, appliances, and agents, and then make any necessary changes.
