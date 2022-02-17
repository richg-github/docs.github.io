# Get started with the Alert Logic Cloud Defender suite

Alert Logic Cloud Defender is a comprehensive suite of security software, including Threat Manager, Log Manager, and Web Security Manager. All customers that subscribe to one or more of the listed products will use the Alert Logic console. The  suite is available for cloud environments, physical environments, and any hybrid environment.

<!--<p MadCap:conditions="Primary.NOTinBHOOF">Much of this information will be provided to you by your Deployment Services contact, and this guide is intended to supplement that guidance. If you have any questions, call your assigned Deployment Services contact.</p>-->
## Set up firewall rules

Cloud Defender requires that you update your firewall rules to allow Alert Logic access to your system. For more information, see the  guide.

## Integrate Cloud Defender with cloud deployments

Before Alert Logic can manage the protection of your AWS and Azure accounts, you must provide Alert Logic with access to your account.

[Configure cross-account roles in AWS](../prepare/aws-cross-account-role-setup.md)

[Configure RBAC roles in Azure](../prepare/azure-rbac-role-setup.md)

Manual deployments using a physical appliance have no extra steps for Cloud Defender integration.

## Create a deployment

The Deployments page in the Alert Logic console shows all the implementations of Cloud Defender, and it allows you to add, edit, and delete deployments.

**To create a deployment:**

1. In the Alert Logic console, click **CONFIGURATION**, and then click **Deployments**.
2. Click the add icon (![](../Resources/Images/Icons/cdAddPlus.png)).
3. Select the appropriate cloud service.
4. Enter the requested information.

* For an AWS deployment:
   * Enter the Role ARN.
   * Check the box at the bottom if you want to use cross-account CloudTrail to centralize CloudTrail log collection, and then enter the Role ARN for the receiving account.
* For a Microsoft Azure deployment:
* Enter the Environment Name
* Enter the Subscription ID
* Enter the Active Directory ID
* Enter the User Name
* Enter the Password

1. Click **SAVE**.

For more detailed information about Deployments, see .

## Install appliance

Deployments on cloud services use the roles created above to automatically install appliances. Manual deployments must follow this set of instructions.

When an appliance is automatically provisioned, the system creates one or two assignment policies, using the following guidelines:

* Alert Logic creates an assignment policy for each appliance during the provisioning process.
* If no VPC or VNet assignment policy exists, Alert Logic creates one and assigns the appliance to it.
* If a VPC or VNet assignment policy exists, Alert Logic assigns the appliance to it.

Determine how you will deploy Cloud Defender, and then install the appropriate physical or virtual appliance.

      You will need your unique registration key for the appliance installation. To locate your unique registration key, browse to the Support page in the Alert Logic console. Click **Downloads**, and your unique registration key appears on the tab.      | Log Manager | Threat Manager | Web Security Manager |
|---|---|---|
| [Install and Configure the  Physical Appliance](../prepare/alert-logic-physical-appliance.md) | [Install and Configure the  Physical Appliance](../prepare/alert-logic-physical-appliance.md) | Not applicable |
| [Install and Configure the  Virtual Appliance](../prepare/virtual-appliance.md) |  |

    Web Security Manager has no additional steps. Deployment Services enables Web Security Manager features once you deploy the Threat Manager appliance.    ## Configure agents and agentless collection

To use Cloud Defender suite functions, you must install the Alert Logic agent, or set up agentless collection, and then configure the collection sources to send data to the appliance for your systems to be monitored.

If you have an active IAM or RBAC role (for AWS or Azure, respectively), and have configured agents to automatically update, the agent you install automatically assigns itself to the local appliance and you need not enter the Unique Registration Key.

* Install the Alert Logic agent:
   * [Linux](../prepare/alert-logic-agent-linux.md)
   * [Windows](../prepare/alert-logic-agent-windows.md)
* Set up Agentless collection (Log Manager only):
   * [Remote collector - Linux](../prepare/remote-log-collector-linux.md)
   * [Remote collector - Windows](../prepare/remote-log-collector-windows.md)
   * [Syslog configuration](../prepare/collect-syslog-no-agent.md)

## Configure product

After deployment is complete, you must configure each product for use.

### Threat Manager policies

The Threat Manager appliance deploys with default policies. AWS deployments automatically configure these policies for you for their environment. To create and edit Threat Manager policies, see .

### Log Manager collection sources and policies

To set up Log Manager, you must:

1. Set up collection sources.
2. Modify policies. Log Manager deploys with default policies. AWS deployments automatically configure these policies for you for their environment. To create and edit Log Manager policies, refer to the Log Manager policies guide.

### Web Security Manager

Alert Logic prefers that customers work with their assigned Project Manager to complete deployment of Web Security Manager.
