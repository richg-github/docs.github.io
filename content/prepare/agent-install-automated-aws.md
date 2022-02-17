# Automate Alert Logic Agent Installation with AWS Systems Manager Distributor

Alert Logic provides an agent that gathers data that Alert Logic must collect for analysis, such as log messages and network traffic, metadata, and host identification information.

If you have Amazon Web Services (AWS) Systems Manager managed instances, you can use [AWS Systems Manager Distributor](https://docs.aws.amazon.com/systems-manager/latest/userguide/distributor.html)     to install the  Alert Logic agent on the instances. Distributor   is a feature integrated with AWS Systems Manager that you can use to securely store and distribute software packages in your accounts. By integrating with  Distributor, you can install the  Alert Logic agent across multiple platforms to secure all your managed instances and keep the agent up to date automatically.

The Alert Logic agent is available in [supported AWS regions](../requirements/amazon-web-services.md#awsRegions).

To automate  agent installation with  Distributor, complete this process in AWS and the Alert Logic console:

1. [Prepare to install the Alert Logic agent](#PreparetoinstalltheAlertLogicagent)
2. [Create an IAM policy by importing a managed policy](#CreateanIAMpolicybyimportingamanagedpolicy)
3. [Create a role and assign the policy](#Createaroleandassignthepolicy)
4. [Schedule agent installation in Distributor](#ScheduleagentinstallationinDistributor)
5. [Verify agent installation](#Verifyagentinstallation)

## Supported subscription types

* Alert Logic MDR Professional
* Alert Logic MDR Enterprise

## Prepare to install the Alert Logic agent

Before you install the agent with  Distributor:

* Ensure the managed instances meet the minimum system requirements listed in [Requirements for the Alert Logic Agent](../requirements/agent.md).
* Ensure you have firewall rules in place:
   * US: [Agent or remote collector outbound rules](../requirements/us-firewall-rules.md#Agentorremotecollectoroutboundrules)
   * EU/UK: [Agent or remote collector outbound rules](../requirements/uk-eu-firewall-rules.md#Agentoutbound)

## Create an IAM policy by importing a managed policy

Each host that you want Distributor to install an agent on must be set up as an AWS Systems Manager managed instance. The first step is to create an IAM policy with the correct permissions in the AWS console.

Follow the instructions in the AWS document [Importing existing managed policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_create-console.html#access_policies_create-copy).

In the Import managed policies window, add the **AmazonSSMManagedInstanceCore** policy.

## Create a role and assign the policy

The next step for setting up each host as an AWS Systems Manager managed instance is to create an IAM role and assign the policy you just created.

Follow the instructions in the AWS document [Creating a role for an AWS service](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_create_for-service.html#roles-creatingrole-service-console).

In the Attach permissions policies window, add the **AmazonSSMManagedInstanceCore** permission.

## Schedule agent installation in Distributor

1. In the AWS console, go to **AWS Systems Manager**.
2. In the navigation pane on the left, under **Node Management**, click **Distributor**.
3. Find and select the AlertLogic-MDR package, and then click **Install on a schedule**.
4. In the Create Association page that opens, fill in the required fields. For **Installation Type**, Alert Logic recommends  the **In-place update** option.
5. Create a schedule. Using a scheduled State Manager Association ensures agents are always installed and up to date.
6. Click **Create Association**.

## Verify agent installation

1. In the Alert Logic console,  click the menu icon (![](../Resources/Images/dashboard/menu-icon.png)).
2. Click ![](../Resources/Images/dashboard/respond-icon.png)**Respond**, and then click **Health**.
3. Select the **Unhealthy** list, and then select the **Hosts with No Agent** view.
4. Check that no hosts in your deployments appear in the list.

Agent registration can take several minutes.

If you waited several minutes and the hosts do not have an agent installed, contact Technical Support for assistance.

Agents are  assigned to Alert Logic appliances automatically.

## Uninstall agents installed with  Distributor

To uninstall agents previously installed with Distributor, you can use the AWS Management Console or the AWS Command Line Interface. Follow the instructions in the AWS document [Uninstall a package](https://docs.aws.amazon.com/systems-manager/latest/userguide/distributor-working-with-packages-uninstall.html).
