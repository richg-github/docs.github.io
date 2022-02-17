# Avoid orphaning agents and appliances

An orphaned agent or appliance is an asset that can no longer protect or be protected because critical configuration variables are missing. An orphaned agent or appliance often manifests after a user deletes a network, subnet, or deployment. This is also difficult to self-diagnose because these assets are not visible in the asset model due to this condition.

The following highlights common scenarios and solutions that can help address orphaned assets if you suspect you may have them in your environment.

## Possible solutions

Alert Logic can assist you with several actions if you have orphaned agents and appliances.

Alert Logic will contact you if we have detected orphaned agents.

### Non-Environment Specific

    Reason: outdated agent    
If the agent is outdated, you cannot reclaim the agent, and must reinstall the agent. Refer to the following documentation:

* [Uninstall the Alert Logic Agent for Linux](../prepare/alert-logic-agent-linux-uninstall.md) and or [Uninstall the Alert Logic Agent for Windows](../prepare/alert-logic-agent-windows-uninstall.md)
* [Install the Alert Logic Agent for Linux](../prepare/alert-logic-agent-linux.md) and or [Install the Alert Logic Agent for Windows](../prepare/alert-logic-agent-windows.md)

**Alert Logic** provides other methods of deploying the **Alert Logic** agent.

### Orphaned agents for Azure or AWS deployments

    Reason: deleted deployment    
If you deleted the deployment, you must create a new deployment with proper credentials for that AWS account or Azure subscription. Refer to the documentation below:

* [Azure Deployments](../get-started/about-deployment-types.md#AzureDeployments)
* [AWS Deployments](../get-started/about-deployment-types.md#Coverageprotectionlevels)

    Reason: deployment not properly discovered    
You must review and fix your credentials. Refer to the documentation below:

These documents are specifically for customers who are upgrading to our newest platform but the requirement for orphaned agents is the same.

* [AWS Prepare for upgrade](../get-started/update-aws-roles-for-upgrade.md)
* [Azure Prepare for upgrade](../get-started/update-azure-deployments-for-upgrade.md)

### Orphaned agents for Data Center deployments

    Reason: deleted subnet, network, and deployments    
You must create a network CIDR in one of the Data Center deployments.

To create a new Data Center deployment, refer to [Data Center Deployment Configuration (Professional Subscription)](../deploy/data-center-pro-ent.md).

If you already have a Data Center deployment you can add a network CIDR to that network by following the instructions [Add assets](../deploy/data-center-pro-ent.md#Add_Assets) section.

    Reason: legacy claim key    
When installing Alert Logic Agents to new hosts in the environment, you must use the associated network claim key rather than the legacy claim key you used when on the older Cloud Defender platform. You can find the correct claim key by following the steps below:

1. Click the “Burger Menu” icon at the top right of the screen
2. Click **Configure**.
3. Click **Deployments**.
4. Click on the deployment you wish to claim the orphan agents to.
5. Click on **Installation Instructions**.
6. One or more Unique Registration Keys will be presented. You will need to update the legacy claim key with the appropriate new Unique Registration Key.

**To update to a new Unique Registration Key**

For Scripted methods in Linux, update the script as instructed in step 5 of the [Install the agent](../prepare/alert-logic-agent-linux.htm?Highlight=agent#Installtheagent1) documentation.

For scripted methods in Windows, [update the value](../prepare/alert-logic-agent-windows.md) “prov_key”.

For base image, uninstall and reinstall the agent using the new claim key.

* [Uninstall the Alert Logic Agent for Linux](../prepare/alert-logic-agent-linux-uninstall.md) or [Uninstall the Alert Logic Agent for Windows](../prepare/alert-logic-agent-windows-uninstall.md)
* [Install the Alert Logic Agent for Linux](../prepare/alert-logic-agent-linux.md) or [Install the Alert Logic Agent for Windows](../prepare/alert-logic-agent-windows.md)

    Reason: networks    
When a network is not found, you must create a CIDR in your Data Center deployment.

To create a new Data Center deployment, refer to [Data Center Deployment Configuration (Professional Subscription)](../deploy/data-center-pro-ent.md).

    Reason: multiple networks    
When there are multiple CIDR intersections,  an Alert Logic team member will contact you about the issue and will work internally to resolve it.

    Reason: full reclaim required    
A full reclaim can be required if you recently upgraded or migrated some of your services or features. An Alert Logic team member who will contact you about the issue.
