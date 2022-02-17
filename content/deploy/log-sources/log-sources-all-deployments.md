# Configure Log Sources for All Deployments

Alert Logic supports the following log source types for all deployments, including Data Center:

**All deployments:**

* **[Flat File logs](#flatFileLogs)**—Log messages stored in flat text files collected by an Alert Logic agent or appliance
* **[Syslog](#syslogLogs)**—A way for network devices to send event messages to a logging server

    You cannot create a Syslog source through the Alert Logic console. You can only do so if you install an agent on a supported *NIX system or if you configure a source device to send messages in the RFC 5424 Syslog format to an Alert Logic appliance or remote collector.    
For more information about other log source types, see [Configure Log Sources for Microsoft Azure](log-sources-azure.md) or [Configure Log Sources for Amazon Web Services (AWS)](log-sources-aws.md).

After you provision and install the Alert Logic agent on your target host, the agent automatically creates an associated log source in the Alert Logic console and configures it with the default collection configuration policy for that log source type. You must create and configure new collection sources with existing collection policies to meet more specific requirements. For more information about Log Management policies, see [Log Management Policies](../../configure/log-management-policies.md).

## Configure Flat File log sources

Before you can create a Flat File collection source, you must create a Flat File collection policy. For more information, see [Log Management Flat File Policy](../../configure/log-management-flat-file-policy.md).

To create a Flat File collection source:

1. From the Deployments page, click the  deployment for which you want to create a Flat File collection source.
2. Click **CONFIGURE LOG SOURCES**.
3. Click the **add** icon (![](../../Resources/Images/Icons/cdAddPlus.png)).
4. From **Source Log Type**, select **Flat File Collection**.
5. In **Source Name**, enter a descriptive name.
6. Select **Enable Collection**.
7. Select **Use an Appliance** or **Use an Agent**, as appropriate to your setup.You can use only a physical appliance for remote flat file log collection.
   * To use an agent to collect flat file logs, select **Use an Agent**, and then **Select a Host** from the drop-down menu.
   * To use a physical appliance to collect flat file logs, select a **Collector** and the corresponding **IP address** (of the log source, not the appliance).
10. Select **Use an existing Policy** or **Create a New Policy**.
   * To use an existing policy, select the policy from the drop-down menu.
   * To create a new policy, see [Create a Flat File collection policy](../../configure/log-management-flat-file-policy.md#Create).
12. Under **Collection Alerts**, select one or more alert options.
13. In the **Tags** field, type one or more easily filtered tags.
14. Click **SAVE**.

**To update a Flat File collection source:**

1. From the Deployments page, click the  deployment for which you want to update the log source.
2. Click **CONFIGURE LOG SOURCES**.
3. Place your cursor over the desired collection source  and click the pencil icon (![](../../Resources/Images/pencil icon.png)).
4. Make the necessary updates.
5. Click **SAVE**.

## Configure Syslog source  

You cannot create a Syslog source through the Alert Logic console. You can create a Syslog collection source only if you install an agent on a supported *NIX system or if you configure a source device to send messages in the RFC 5424 Syslog format to an Alert Logic appliance or remote collector.

## Additional Tasks

To learn how to perform additional tasks, such as viewing source information, mass editing sources, and archiving and restoring collection sources, see [View log source information](../log-sources.md#viewCollectionSourceInformation).
