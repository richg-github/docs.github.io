# Get Started with Your Alert Logic Essentials Subscription

Your account subscription dictates the level of protection you can assign assets in each deployment you create. You can create deployments for assets found in your Amazon Web Services (AWS) and Microsoft Azure cloud platforms, and from other cloud-based or physical data centers.

For more information about Alert Logic subscriptions, see [Alert Logic Subscription Levels](subscription-levels.md).

## Create your deployment

When you create a deployment, the Alert Logic console prompts you through the following steps:

1. Configure   third-party access to cloud-based assets (AWS and Azure deployments only)
2. Assets
   * Discover assets (AWS and Azure deployments)
   * Add assets (Data Center deployments)
4. Define the scope of your protection
5. Schedule scans
6. Set up File Integrity Monitoring (FIM)
7. Install appliances
8. Update firewall rules and configure ports for scanning

For more detailed information and deployment creation instructions for customers with Essentials subscriptions, see:

* [Amazon Web Services (AWS) Deployment Configuration—Automatic Mode (Essentials Subscription)](../deploy/aws-auto-essentials.md#create-aws-auto-deployment)
* [Amazon Web Services (AWS) Deployment Configuration—Manual Mode (Essentials Subscription)](../deploy/aws-manual-essentials.md)
      To determine whether you should use an Automatic Mode or Manual Mode deployment creation procedure for an AWS Deployment, see [About  Deployment Types](about-deployment-types.md).    
* [Microsoft Azure Deployment Configuration (Essentials Subscription)](../deploy/azure-essentials.md)
* [Data Center Deployment Configuration (Essentials Subscription)](../deploy/data-center-essentials.md)

### Provide Alert Logic third-party access

When you create an AWS or Azure deployment, you must grant Alert Logic access to your cloud environments for asset discovery and scanning. The access granted Alert Logic provides only the amount of access required to monitor the assets in your cloud environments.

### Asset discovery

After you grant Alert Logic access  to your cloud account or subscription, Alert Logic automatically discovers its assets. Alert Logic displays the assets discovered in your account in a visual topology diagram. To learn more about topology, see [Topology](../../../../analyze/topology.md).

If you have external-facing assets, you can add them by domain name or IP address.

### Add assets

For Data Center deployments, you must manually add the following assets

* Internal assets: Network and subnet
* External assets: Domain name or IP address

### Define your scope of protection

You can define the scope of your protection per network basis. Click a region or individual network to set the protection level or leave it unprotected. You also have the option to exclude assets or tags from external scanning, and internal scanning.

### Schedule scans

Alert Logic automatically performs discovery and vulnerability scans once a day. You can schedule when and how often you want Alert Logic to scan for new assets or perform vulnerability scans.

### Configuration topology overview

This topology diagram provides an overview of your scope of protection. You can see which assets are unprotected, or are protected at the Essentials level.

    You will only see protection levels that your subscription level allows.     ### Install appliances

Appliances

An Essentials subscription requires only an appliance for scanning. For AWS, you do not need to deploy an IDS appliance for an Essentials subscription.

**Agents**

Alert Logic provides a single agent that collects data used for analysis, such as log messages and network traffic, metadata, and host identification information. For more information about installing agents, see [Install the Alert Logic Agent for Linux](../../prepare/alert-logic-agent-linux.md) or [Install the Alert Logic Agent for Windows](../../prepare/alert-logic-agent-windows.md).

## Update the Alert Logic agent firewall rules

Ensure the proper outbound firewall rules are in place for the node where you installed the agent. For information about firewall rules, see [Alert Logic Firewall Rules](https://docs.alertlogic.com/requirements/us-firewall-rules.htm).

## Update the Alert Logic appliance firewall rules

If you used an automation template provided by Alert Logic for your appliance installation, you do not need to perform this step.

Ensure the proper inbound and outbound firewall rules are in place for the appliance. For information about firewall rules, see [Alert Logic Firewall Rules](https://docs.alertlogic.com/requirements/us-firewall-rules.htm).

### Configure ports for scanning

For internal scanning, Alert Logic recommends that the appliance IP be able to communicate with target assets for scanning over ports 1-65535 to validate any open service running on any port on the assets. This configuration also allows Alert Logic to test for vulnerabilities that may exist for those services.
