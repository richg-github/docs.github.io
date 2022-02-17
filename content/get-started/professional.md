# Get Started with Your Alert Logic Professional Subscription

Your account subscription dictates the level of protection you can assign assets in each deployment you create. You can create deployments for assets found in your Amazon Web Services (AWS) and Microsoft Azure cloud platforms, and from other cloud-based or physical data centers.

If you do not know which Alert Logic subscription you have, contact your account administrator.

For more information about Alert Logic subscriptions, see [Alert Logic Subscription Levels](subscription-levels.md).

## Review system and platform requirements

Before you get started, make sure all necessary parts of your environment are ready to be used with Alert Logic Managed Detection and Response. Review the [Operating System and Browser Requirements ](../requirements/operating-system-browsers.md).

You also must check your cloud platforms to make sure they meet instance size and throughput requirements:

* [Requirements for Managed Detection and Response for Amazon Web Services (AWS)](../requirements/amazon-web-services.md)
* [Requirements for Managed Detection and Response for Microsoft Azure](../requirements/microsoft-azure.md)
* [Requirements for Managed Detection and Response for Google Cloud Platform](../requirements/google-cloud.md)

## Learn to use the Alert Logic console

## Deployment Creation Overview

When you create a deployment, the Alert Logic console prompts you through the following steps:

1. Configure   third-party access to cloud-based assets (AWS and Azure deployments only)
2. Assets
   * Discover assets (AWS and Azure deployments)
   * Add assets (Data Center deployments)
4. Define the scope of your protection
5. Schedule scans
6. Set up File Integrity Monitoring (FIM)
7. Install appliances and agents
8. Update firewall rules and configure ports for scanning
9. Set up log sources and remote collectors

This is the general workflow for all deployment types. For more detailed information and deployment creation instructions for customers with Professional subscriptions, see:

* [Amazon Web Services (AWS) Deployment Configuration—Automatic Mode (Professional Subscription)](../deploy/aws-auto-pro-ent.md)
* [Amazon Web Services (AWS) Deployment Configuration—Manual Mode  (Professional Subscription)](../deploy/aws-manual-pro-ent.md)
      To determine whether you should use an Automatic Mode or Manual Mode deployment creation procedure for an AWS Deployment, see [About  Deployment Types](about-deployment-types.md).    
* [Microsoft Azure Deployment Configuration (Professional Subscription)](../deploy/azure-pro-ent.md)
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

You can define the scope of your protection per network basis. Click a region or individual network to set the scan level or leave it unprotected. You also have the option to exclude assets or tags from external scanning, internal scanning, and Network IDS.

### Schedule scans

Alert Logic automatically performs discovery and vulnerability scans once a day. You can schedule when and how often you want Alert Logic to scan for new assets or perform vulnerability scans.

### Configuration topology overview

This topology diagram provides an overview of your scope of protection. You can see which assets are unprotected, or are protected at the Essentials (if applicable) or Professional levels.

    You will only see protection levels that your subscription level allows.     ### Install appliances and agents

Appliances

A Professional subscription requires that you install appliances for scanning and network IDS.

**Agents**

Alert Logic provides a single agent that collects data used for analysis, such as log messages and network traffic, metadata, and host identification information. For more information about installing agents, see [Install the Alert Logic Agent for Linux](../../prepare/alert-logic-agent-linux.md) or [Install the Alert Logic Agent for Windows](../../prepare/alert-logic-agent-windows.md).

**Remote Collectors**

Alert Logic provides remote syslog collection for networking equipment, like firewalls. For more information about installing remote collectors see [Install the Remote Collector for Windows](../prepare/remote-log-collector-windows.md) or [Install the  Remote Collector for Linux](../prepare/remote-log-collector-linux.md).

## Update firewall rules

### Update the Alert Logic agent firewall rules

Ensure the proper outbound firewall rules are in place for the node where you installed the agent. For information, see [Requirements for the Alert Logic Agent](../requirements/agent.md).

### Update the Alert Logic appliance firewall rules

If you used an automation template provided by Alert Logic for your appliance installation, you do not need to perform this step.

Ensure the proper inbound and outbound firewall rules are in place for the appliance. For information, see [Alert Logic Requirements for Virtual and Physical Appliances](../requirements/appliance-requirements.md).

### Configure ports for scanning

For internal scanning, Alert Logic recommends that the appliance IP be able to communicate with target assets for scanning over ports 1-65535 to validate any open service running on any port on the assets. This configuration also allows Alert Logic to test for vulnerabilities that may exist for those services.

## Set up log sources 

When you installed the agent, you allowed Alert Logic to automatically collect Syslog and Windows event logs. If you have a Professional subscription, you can choose to set up additional logs to collect. To add log sources for data you want to collect, see [Log Sources](../log-sources.md#top). When you installed the remote collector, Alert Logic automatically collects Syslog that is forwarded to the remote collector IP address.
