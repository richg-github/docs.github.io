# Log Management Syslog Policies

Syslog policies allow you to collect syslog messages, which are a way for network devices to send event messages to a logging server—usually known as a syslog server.

Alert Logic also allows you to create other types of Log Management policies. These policies dictate how Alert Logic collects log messages, and allows you to reuse this common configuration for several log sources of the same type. To learn more about other log management policies, see the link below:

* [Log Management Flat File Policy](log-management-flat-file-policy.md)
* [Log Management Windows Event Log Policies](log-management-windows-event-policies.md)
* [Log Management S3 Policies](log-management-s3-policies.md)

## Configure syslog collection policies

To access the Log Management policies page, click **CONFIGURATION**, click **Log Management**, and then click **Policies** in the left navigation panel.

If you update, archive, or delete any collections or policies, you could break interconnected configurations.

### Create a syslog collection policy

**To create a syslog collection policy**:

1. Access the Log Management Policies page and click the **Syslog** tab.
2. Click the add icon (![](../Resources/Images/Icons/cdAddPlus.png)).
3. In **Syslog Policy Name**, type a descriptive name.
4. In **Syslog Listen Port**, type the port where the agent receives syslog messages.
5. In **Local Syslog Cache Disk Limit (MB)**, type the maximum amount of disk space you want to allow to store syslog messages before they are transmitted to Alert Logic. Larger values allow the agent to store more message when the agent is unable to transmit message to Alert Logic.
6. In **Collection Schedule Blackout Periods**, select or create a collection schedule:
   * To select a collection schedule, keep the default selection: **Use an existing schedule**, and then from **Choose a schedule**, select a schedule.
   * To create a new collection schedule:
      1. Select **Create a new schedule**.
      2. Enter and select the schedule options.
      3. Type a **Schedule Name**.
      4. Select a **Schedule Time Zone**.
      5. Select **Blackout** to enable blackout periods, or add or remove extra blackout periods.
8. Click **SAVE**.

### Update a syslog collection policy

**To update a syslog collection policy**:

1. Access the Log Management Policies page and click the **Syslog** tab.
2. In the list of syslog collection policies, click the pencil icon (![](../Resources/Images/pencil icon.png)) for the syslog collection policy to edit.
3. Make the necessary updates. For more information, see [Create a syslog collection policy](#Create2).
4. Click **SAVE**.

### Delete a syslog collection policy

**To delete a syslog collection policy**:

1. Access the Log Management Policies page and click the **Syslog** tab.
2. Click the trash icon (![](../Resources/Images/Icons/trash icon.png)) for the syslog collection policy to delete.
3. Click **DELETE**.
