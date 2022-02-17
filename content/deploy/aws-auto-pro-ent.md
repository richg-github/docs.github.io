# Amazon Web Services (AWS) Deployment Configuration—Automatic Mode (Professional Subscription)

Alert Logic recommends Automatic Mode for AWS deployment creation if you want Alert Logic to deploy and maintain new VPC subnets used for network IDS and scanning instances.

Deployment creation requires that you be logged into your [Alert Logic account](http://console.overview.alertlogic.com/) and the [AWS account](http://aws.amazon.com/) you want this deployment to monitor and protect.

    If you manage more than one Alert Logic account, be sure you are logged into the correct account.    
To start creating your AWS deployment:

1. In the Alert Logic console, click the ![](../Resources/Images/dashboard/configure-icon.png)**Configure** menu item, and then click **Deployments**.
2. Click the  add icon (![](../Resources/Images/Icons/cdAddPlus.png)), and then select Amazon Web Services (AWS).
3. Type a name for your deployment, and then click **SAVE AND CONTINUE**.
4. Select Automatic Mode, and then click **SAVE &amp; CONTINUE**.

## IAM policy and role creation

To protect your AWS deployment, you must set up an AWS IAM policy and role to allow Alert Logic access to your AWS account. Alert Logic provides an AWS CloudFormation template to automate creation of the correct policy and role for the deployment. You can also choose to manually set up the IAM policy and role.

Cross-account roles allow Alert Logic to access your AWS account. AWS role creation requires that you provide an AWS policy, a document that specifies the permissions assigned to the AWS role you create for Alert Logic to access to your AWS account.

Alert Logic recommends you set up AWS cross-account roles using the default procedures in the Alert Logic console, which allow Alert Logic to make all the necessary changes to your AWS account. The full permission policy documents do not allow Alert Logic to:

* Retrieve secret keys or credentials from IAM
* Retrieve data from data stores other than S3
* Perform these actions from any other AWS account
* Grant access to the protected account to any other AWS account or user
* Modify IAM credentials or policies

### IAM policy and role setup using AWS CloudFormation 

Alert Logic recommends you use the Alert Logic CloudFormation template for quick, convenient IAM policy and role creation. The CloudFormation template creates the appropriate IAM role that allows your deployment access to your AWS assets.

Click **CLOUDFORMATION SETUP**, and then follow the instructions in the Alert Logic console and the AWS console.

### IAM policy and role setup using manual IAM setup

Select manual IAM set up if your AWS account permissions allow you to create an IAM policy, but does not have the permissions to run CloudFormation.

Click **MANUAL IAM SETUP**, and then follow the instructions on the screen.

## Enter your Role ARN

In the Alert Logic console, enter the ARN you copied from the AWS console after you created the IAM role.

If you want to configure cross-account access for centralized CloudTrail log collection, click the **I want to configure centralized CloudTrail log collection for this deployment** slide bar, and enter a second Role ARN you created for this purpose. For more information about centralized log collection, see [Should you centralize CloudTrail log collection?](../prepare/aws-cross-account-role-setup.md#ShouldyoucentralizeCloudTraillogcollection).

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

You can define the scope of your protection per region or network. Each network  appears within its protected region. Click a region or individual network to set the service level  or leave it unprotected, and then click **SAVE**. You can also use tags  in the internal scanning tab of **EXCLUSIONS** to exclude assets from scanning, including subnets. You must choose one of the following levels of coverage:

* Unprotected
* Alert Logic Essentials coverage
* Alert Logic Professional coverage

The choices available for scope of protection correspond directly with your entitlement. Although a Professional subscription includes all the features of Essentials, a Professional customer cannot set the protection scope to Essentials unless the account has a separate Essentials subscription. Likewise, an Enterprise customer cannot set the protection scope to Essentials or Professional unless the account has separate subscriptions for those.

You can [change the protection level](change-protection.md) later as needed.

### Exclusions

You can exclude assets or ports from external and internal scanning and Network IDS. You can also exclude assets from internal scanning by using AWS tags.

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

To exclude assets, ports, or AWS tags from internal scanning:

1. Click **EXCLUSIONS**.
2. Click the **Internal Scanning** tab.
3. To exclude assets, click **ASSETS** to search for available assets to exclude, and then click **EXCLUDE** for the asset you want to exclude.                 You can remove an asset from the exclusion list at any time to include the asset in scanning. To remove an asset from the exclusion list, click **CANCEL**.
4. To exclude ports, click **PORTS**, and then do the following:
   1. Search for the host, subnet, or network that has the ports you want to exclude from internal scanning.
   2. In the **Protocol** field, select the port protocol: **UDP** or **TCP**.
   3. Enter one or more ports that you want to exclude. Use a dash or colon to indicate a range  (for example, 1-10001). Separate multiple ports or port ranges with a comma (for example, 11234, 11311, 12000-12010).
   4. Click **EXCLUDE AND ADD ANOTHER**.
      You can remove ports from the exclusion list at any time to include the ports in scanning. To remove ports from the exclusion list, click **REMOVE**.      9. To exclude assets by using AWS tags, click **TAGS** to search for available tags to exclude, and then click **EXCLUDE** for the tag you want to exclude.
      You can remove a tag from the exclusion list at any time to include the tag in scanning. To remove a tag from the exclusion list, click **CANCEL**.      13. After you apply your exclusions, close the **Exclusions** window.
14. On the **Scope of Protection** page, click **SAVE**.

    If you exclude assets, tags, or ports that are selected  in an active scan schedule in the Scope or Ports tab, the items remain selected   but are not included in future scans.    #### Network IDS

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

## Scan Schedules

Alert Logic performs scans to protect your deployment. When you create a new deployment, Alert Logic automatically creates default scan schedules to perform external and internal vulnerability scans on all non-excluded assets and ports in your AWS security groups. You can also schedule when you want  to perform specific scans for all or selected assets  and ports  from the **Internal Scanning** and **External Scanning** tabs. For more information, see [Manage Scan Schedules](../analyze/manage-scans-and-results/schedules.md).

After reviewing the schedules and making any changes, click **NEXT**.

## Agent-based Scanning

You have the option to enable agent-based scanning. Agent-based scanning improves the efficiency, accuracy, and usability of Alert Logic vulnerability scanning features. Agent-based scanning provides the vulnerability assessment coverage of authenticated network scanning without the need to manage credentials and with a reduction in network traffic and impact. To learn more about agent-based scanning, see [Agent-Based Scanning](../analyze/manage-scans-and-results/agent-based-scan.md).

## File Integrity Monitoring (FIM)

FIM allows you to monitor changes to files and directories of assets in your deployments. You can configure monitoring or exclusions for specific file paths or entire directories  in your Windows and Linux systems.

FIM is composed of two subsections: Monitoring and Exclusions. On the **Monitoring** page, you can set up files and directories for monitoring from the default file types listed on the page. In the **Exclusions** page, you can exclude files and directories  from monitoring, which will override a previously configured file monitoring setup. For more information, see [File Integrity Monitoring ](../configure/file-integrity-monitoring.md).

After creating FIM or exclusion setups, click **NEXT**.

## Configuration Topology

This topology diagram provides an overview of your scope of protection. You can see which assets are unprotected, or being scanned at the Essentials, Professional, or Enterprise levels. Click a VPC in the diagram to view its subnets, instances, and hosts.

The protection breakdown displays  how many assets are unprotected, excluded, and protected, along with the number of protected assets in each level.

![](../Resources/Images/TopologyConfigurationOverviewProtectionBreakdown.png)

## Install agent

Alert Logic provides a single agent that collects data used for analysis, such as log messages and network traffic, metadata, and host identification information. Click the links below for more information and to download the appropriate agent:

* [Install the Alert Logic Agent for Linux](../prepare/alert-logic-agent-linux.md)
* [Install the Alert Logic Agent for Windows](../prepare/alert-logic-agent-windows.md)

     If you have Amazon Web Services (AWS) Systems Manager managed instances, you can use [AWS Systems Manager Distributor](https://docs.aws.amazon.com/systems-manager/latest/userguide/distributor.html)     to install the  Alert Logic agent on the instances instead of installing the agent on each host manually. For more information, see [Automate Alert Logic Agent Installation with AWS Systems Manager Distributor](../prepare/agent-install-automated-aws.md).    ## Update the Alert Logic agent firewall rules

Ensure the proper outbound firewall rules are in place for the node where you installed the agent. For information about firewall rules, see [Alert Logic Firewall Rules](https://docs.alertlogic.com/requirements/us-firewall-rules.htm).

## Update the Alert Logic appliance firewall rules

If you used a CloudFormation template or a Terraform template provided by Alert Logic for your appliance installation, you do not need to perform this step.

Ensure the proper inbound and outbound firewall rules are in place for the appliance. For information about firewall rules, see [Alert Logic Firewall Rules](https://docs.alertlogic.com/requirements/us-firewall-rules.htm).

## Additional log sources

If you have a Professional subscription, you can set up log collection. To add log sources for data you want to collect, see [Log Sources](log-sources.md#top).

## Verify the health of your deployment

After you create your deployment, access the Health console in the Alert Logic console to determine the health of your networks, appliances, and agents, and then make any necessary changes.
