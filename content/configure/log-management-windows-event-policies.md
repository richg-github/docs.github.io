# Log Management Windows Event Log Policies

Windows Event log files track significant events on a Windows server. A Windows event log policy allows you to collect event log files for Alert Logic to review.

Windows event log policies collect many types of logs, including:

* Program errors
* User logins
* PowerShell logs
* Network information

Alert Logic also allows you to create other types of Log Management policies. These policies dictate how Alert Logic collects log messages, and allows you to reuse this common configuration for several log sources of the same type. To learn more about other log management policies, see the links below:

* [Log Management Flat File Policy](log-management-flat-file-policy.md)
* [Log Management Syslog Policies](log-management-syslog-policies.md)
* [Log Management S3 Policies](log-management-s3-policies.md)

## Configure Windows event log collection policies

To access the Log Management policies page, click **CONFIGURATION**, click **Log Management**, and then click **Policies** in the left navigation panel.

If you update, archive, or delete any collections or policies, you could break interconnected configurations.

### Create a Windows event log collection policy

**To create a Windows Event Log collection policy**:

1. Access the Log Management Policies page and click the **Windows Event Log** tab.
2. Click the add icon (![](../Resources/Images/Icons/cdAddPlus.png)).
3. In **Windows Event Log Policy Name**, type a descriptive name.
4. In **Collection Schedule Blackout Periods**, select or create a collection schedule:
   * To create a new collection schedule:
      1. Select **Create a new schedule**.
      2. Enter and select the schedule options.
      3. Type a **Schedule Name**.
      4. Select a **Schedule Time Zone**.
      5. Select **Blackout** to enable blackout periods, or add or remove extra blackout periods.
   * To select a collection schedule, keep the default selection: **Use an existing schedule**, and then from **Choose a schedule**, select a schedule.
7. Choose one of the following:
   * To collect specific Windows event log streams, clear **Collect All Available Event Log Streams** and select your desired streams under **Alert and Collect on Selected Streams**.
   * To collect all Windows event log streams, keep the default selection **Collect All Available Event Log Streams** selected.
10. Click **SAVE**.

### View streams collected under a policy

To view specific streams collected under a Windows event log collection policy:

1. Access the Log Management Policies page and click the **Windows Event Log** tab.
2. In the list of Windows event log policies, click the pencil icon (![](../Resources/Images/pencil icon.png)) for the Windows event log policy you want to view.
3. The last section shows all the available event log streams.
   * Streams with check boxes selected are collected.
   * Click the blue + icon (![](../Resources/Images/Icons/blue-tree.png)) to open a group of streams.
   * Some streams have more than one option for related information, for example, "Microsoft-Windows-PowerShell" and "Windows PowerShell."
5. Click **SAVE**.

### Update a Windows event log collection policy

**To update a Windows event log collection policy**:

1. Access the Log Management Policies page and click the **Windows Event Log** tab.
2. In the list of Windows event log policies, click the pencil icon (![](../Resources/Images/pencil icon.png)) for the Windows event log policy you want to edit.
3. Make the necessary updates. For more information, see [Create a Windows event log collection policy](#Create).
4. Click **SAVE**.

### Delete a Windows event log collection policy

**To delete a Windows event log collection policy**:

1. Access the Log Management Policies page and click the **Windows Event Log** tab.
2. Click the trash icon (![](../Resources/Images/Icons/trash icon.png)) for the Windows event log policy to delete.
3. Click **DELETE** to confirm.
