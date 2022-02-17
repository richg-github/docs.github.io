# Get Started with Alert Logic Deployments

An Alert Logic deployment allows you to specify the assets—such as appliances, agents, hosts, and collectors—in your environments to monitor and protect. You must create a deployment, regardless of your subscription level, or your assets will not be monitored or protected. You can create deployments for assets found in your Amazon Web Services (AWS) and Microsoft Azure cloud platforms, and from other cloud-based or physical data centers.

Alert Logic discovers and organizes deployment assets into a visual topology where you can select the desired levels of protection, based on your Alert Logic subscription level, for the assets. Choose one of the following levels of coverage for each asset:

* Unprotected
* Alert Logic MDR Essentials coverage
* Alert Logic MDR Professional coverage (if you have a Professional or Enterprise subscription)

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

This is the general workflow for all deployments. For more detailed information and deployment creation instructions, see:

| Platform | Essentials | Professional |
|---|---|---|
| AWS | [Amazon Web Services (AWS) Deployment Configuration—Automatic Mode (Essentials Subscription)](../deploy/aws-auto-essentials.md) | [Amazon Web Services (AWS) Deployment Configuration—Automatic Mode (Professional Subscription)](../deploy/aws-auto-pro-ent.md) |
| [Amazon Web Services (AWS) Deployment Configuration—Manual Mode (Essentials Subscription)](../deploy/aws-manual-essentials.md) | [Amazon Web Services (AWS) Deployment Configuration—Manual Mode  (Professional Subscription)](../deploy/aws-manual-pro-ent.md) |
| Azure | [Microsoft Azure Deployment Configuration (Essentials Subscription)](../deploy/azure-essentials.md) | [Microsoft Azure Deployment Configuration (Professional Subscription)](../deploy/azure-pro-ent.md) |
| Google Cloud Platform | [Data Center Deployment Configuration for Google Cloud Platform (Essentials Subscription) ](../deploy/google-cloud-essentials.md) | [Data Center Deployment for Google Cloud Platform (Professional Subscription)](../deploy/google-cloud-pro-ent.md) |
| Oracle Cloud Platform | [Alert Logic Data Center Deployment for Oracle Cloud ](../deploy/oracle-cloud.md) |  |
| Data center/on-premesis | [Data Center Deployment Configuration (Essentials Subscription)](../deploy/data-center-essentials.md) | [Data Center Deployment Configuration (Professional Subscription)](../deploy/data-center-pro-ent.md) |

### Provide Alert Logic third-party access

When you create an AWS or Azure deployment, you must grant Alert Logic access to your cloud environments for asset discovery and scanning. The access granted to Alert Logic provides only the amount of access required to monitor the assets in your cloud environments.

### Asset discovery

After you grant Alert Logic access  to your cloud account or subscription, Alert Logic automatically discovers its assets. Alert Logic displays the assets discovered in your account in a visual topology diagram. To learn more about topology, see [Topology](../analyze/topology.md).

If Alert Logic does not discover all your assets, you can add external assets by domain name or IP address.

### Add assets

For Data Center deployments, Alert Logic suggests you add your assets by using discovery scans. Although you   can add your assets manually, weekly discovery scans ensure your Data Center deployments are configured with the right ranges.

### Define your scope of protection

You can define the scope of your protection per network basis. Each network appears within its protected region. Click a region or individual network to set the scan level or leave it unprotected. You also have the option to exclude assets or tags from external scanning, internal scanning, and Network IDS.

### Schedule scans

Alert Logic automatically performs certain scans. You can schedule when and how often you want Alert Logic to scan for new assets or perform vulnerability scans.

### File Integrity Monitoring (FIM)

FIM allows you to monitor changes to files and directories of assets in your deployments. You can configure monitoring or exclusions for specific file paths or entire directories  in your Windows and Linux systems. For more information, see [File Integrity Monitoring ](../configure/file-integrity-monitoring.md).

### Configuration topology overview

The topology diagram provides an overview of your scope of protection. You can see which assets are unprotected, or are scanned at the Essentials or Professional levels.

### Install appliances and agents

#### Appliances

Regardless of deployment type you create, you must configure appliances for scanning and network IDS. Your deployment type and subscription determine the appliances you need to set up.

####  Agents

If you have a Professional subscription, you must install an agent. Alert Logic provides a single agent that collects data used for analysis, such as log messages and network traffic, metadata, and host identification information. For more information about installing agents, see [Install the Alert Logic Agent for Linux](../prepare/alert-logic-agent-linux.md) or [Install the Alert Logic Agent for Windows](../prepare/alert-logic-agent-windows.md).For more information about installing agents, see [Install the Alert Logic Agent for Linux](../prepare/alert-logic-agent-linux.md), [Install the Alert Logic Agent for Windows](../prepare/alert-logic-agent-windows.md), or [Automate Alert Logic Agent Installation with AWS Systems Manager Distributor](../prepare/agent-install-automated-aws.md).

### Update the Alert Logic agent firewall rules

If you installed the Alert Logic agent, ensure the proper outbound firewall rules are in place for the node where you installed the agent. For information about firewall rules, see Alert Logic firewall rules for the [US](../requirements/us-firewall-rules.md) or [UK/EU](../requirements/uk-eu-firewall-rules.md).

### Update the Alert Logic appliance firewall rules

If you used a CloudFormation template or a Terraform template provided by Alert Logic for your appliance installation, you do not need to perform this step.

Ensure the proper inbound and outbound firewall rules are in place for the appliance. For information about firewall rules, see Alert Logic firewall rules for the [US](../requirements/us-firewall-rules.md) or [UK/EU](../requirements/uk-eu-firewall-rules.md).

### Configure ports for scanning

For internal scanning, Alert Logic recommends that the appliance IP should be able to communicate with target assets for scanning over ports 1-65535 to validate any open service running on any port on the assets. This configuration also allows Alert Logic to test for vulnerabilities that may exist for those services.

### Set up log sources

If you have a Professional subscription, you can set up log collection. To add log sources for data you want to collect, see [Log Sources](../deploy/log-sources.md) for more information.
