# Amazon Web Services (AWS) (AWS) Deployment Configuration

Alert Logic allows you to create AWS deployments within the Alert Logic console. The Deployments page appears under the Configuration tab in the Alert Logic console. To add a deployment, click the  add icon (![](../../Resources/Images/Icons/cdAddPlus.png)), and then enter the requested information to provide Alert Logic with third-party access to the specified cloud environment. For more information about adding deployments for other cloud environments, see [Microsoft Azure Deployment Configuration](azure.md) and [Data Center Deployment Configuration (Essentials Subscription)](../data-center-essentials.md).

## Name your deployment

In the Deployment Name field, type a descriptive name for the deployment you want to create, and then click **SAVE AND CONTINUE**.

## Choose a deployment mode

To protect your AWS deployment, you must set up an AWS IAM role and policy to allow Alert Logic access to your AWS account. Alert Logic provides AWS CloudFormation templates to automate creation of the correct policy and role for the deployment mode you choose. The deployment mode you choose determines how Alert Logic deploys your scanning instances. You can also choose to employ manual setup in which you log into the AWS console and create your IAM policy and role.

Choose from automatic, guided, or manual deployment modes. Each deployment mode allows a different level of control over the creation of scanning instances and subnets.

### Automatic Mode

Alert Logic recommends you use **Automatic Mode**  if you want Alert Logic to deploy and maintain new VPC subnets used for scanning instances.

### Manual Mode

Select **Manual Mode** if you want to use your own policy and role, and manage subnets for scanning instances when you create an AWS deployment.

## IAM policy and role setup

Alert Logic recommends you use the provided CloudFormation template for quick, convenient IAM policy and role creation.

Click **CLOUDFORMATION SETUP** to use the Alert Logic CloudFormation template to create the IAM role needed for deployment creation.

### Create a policy and role with Alert Logic CloudFormation template 

The CloudFormation template creates the appropriate IAM role that allows your deployment access to your AWS assets. To use the CloudFormation template:

1. Access the AWS [CloudFormation Create Stack page](https://console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks/create/review?templateURL=https:%2F%2Falertlogic-cloud-formation-templates-733251395267.s3.amazonaws.com%2Fci_full%2F2019-02-01&amp;stackName=alertlogic-iam-role-ci-full-2019-02-01&amp;param_ExternalId=10785703).
All the information required for the Alert Logic CloudFormation template to create the appropriate IAM policy and role for this deployment type is prepopulated.
**CAUTION**: Do not change any preselected items on the AWS CloudFormation Create Stack page, or this procedure will not complete successfully.
2. Select **I acknowledge that **AWS** CloudFormation might create IAM resources.**
3. From the AWS CloudFormation Create Stack page, click **Create**.
4. When the Status is CREATE_COMPLETE, click **Outputs**.
5. Copy the Role ARN Value, which you will need to create your deployment.
6. In the Alert Logic console, click **CONTINUE**.

## Enter your Role ARN

The role you created with the CloudFormation template grants only the minimum permissions required for Alert Logic to monitor your AWS environment. To maximize permissions:

1. Enter the ARN you copied from the AWS Create Stack page.
2. Click the **I want to configure centralized CloudTrail log collection for this deployment** slide bar, and then click **CONTINUE**.

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

You also have the option to exclude assets or AWS tags from external scanning, internal scanning, and Network IDS.

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

### Options

#### Configure Cross-Network Protection

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

This topology diagram provides an overview of your scope of protection. You can see which assets are unprotected, or being scanned at the Essentials, Professional, or Enterprise levels. Click a VPC in the diagram to view its subnets, instances, and hosts.

The protection breakdown displays  how many assets are unprotected, excluded, and protected, along with the number of protected assets in each level.

![](../../Resources/Images/TopologyConfigurationOverviewProtectionBreakdown.png)

You can search for specific assets. The protection breakdown updates as it finds specific assets.

## Install agent

Alert Logic provides a single agent that collects data used for analysis, such as log messages and network traffic, metadata, and host identification information. Click the links below for more information and to download the appropriate agent:

* [Install the Alert Logic Agent for Linux](../../prepare/alert-logic-agent-linux.md)
* [Install the Alert Logic Agent for Windows](../../prepare/alert-logic-agent-windows.md)

## Log sources

You can set up log collection. To add log sources for data you want to collect, see [Log Sources](../log-sources.md).
