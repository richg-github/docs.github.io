# System Logs for Syslog Collection

The System Logs page  allows you to configure system log (syslog) collection. Syslog messages are a way for network devices to send event messages to a logging server—usually known as a syslog server. The syslog collection configuration in the Alert Logic console is a streamlined workflow to collect messages from Linux system logs, Linux remote system logs, and Windows event logs.

The syslog collection instances govern how Alert Logic collects log messages,  using tag and topology-based asset scoping. You can reuse a common configuration for several log sources of the same type with the duplicate feature. This features allows you to copy an existing syslog collection instance to create a new one and edit it as necessary.

To access the log collection setup, click the menu icon (![](../Resources/Images/dashboard/menu-icon.png)) from the Dashboards page. Click ![](../Resources/Images/dashboard/configure-icon.png)**Configure**, click **Deployments**, and then click the deployment for which to configure collections. On the left navigation panel, click **Logs**, and then click **System Logs**.

This document only applies to new Managed Detection and Response Professional and Enterprise customers who are configuring system logs for the first time. If you have previously configured syslog policies, see [Log Management Syslog Policies](log-management-syslog-policies.md).

## System logs page

The System Logs page lists syslogs that have templates with predefined fields, including ones that are not yet enabled. All system logs appear in the list by default. Click the drop-down menu to view only Linux System Logs, Remote Syslog Collector, or Windows Event Logs. You can use the search bar to find a specific log collection. You can view, edit, manage assets for, duplicate, and delete existing system logs from this page.

## Add a syslog collection

The collection determines from where to collect syslog messages for Linux System and for Linux Remote logs, and which type of event streams to collect syslog messages for Windows Event Logs. Asset scoping determines the asset tags, assets, or topology elements from which Alert Logic collects logs.

After you fill out all required fields and scope your assets, you must turn on **Collect** for the application to start collecting log data.

**To create a Linux System syslog collection**:

1. In the System Logs page, click the add icon (![](../Resources/Images/Icons/cdAddPlus.png)).
2. Click **Linux System Log**.
3. In **System Name**, type a descriptive name.
4. To automatically enable collection from the syslog, select the check box.
5. In **Syslog System Port**, type the port where the agent receives syslog messages. The default port is 1514.
6. In **Local Syslog Cache Disk Limit (MB)**, type the maximum amount of disk space you want to allow to store syslog messages before they are transmitted to Alert Logic. Larger values allow the agent to store more message when the agent is unable to transmit message to Alert Logic.The default limit is 500.
7. Select the check box to enable the agent to collect docker container logs.
8. Click **SAVE**.
9. In the Manage Assets section, search for assets from which to collect logs.
10. Select the tags or topology elements from the drop-down list. Tags are separated by <kbd>AND</kbd>, and topology elements are separated by <kbd>OR</kbd>. Tags and topology elements are separated by <kbd>OR</kbd>.
11. Click **SAVE**.
12. Ensure **Collect** is turned on for the application you just created in the Application Logs list.

**To create a Linux Remote syslog collection**:

1. In the System Logs page, click the add icon (![](../Resources/Images/Icons/cdAddPlus.png)).
2. Click **Linux Remote System Log**.
3. In**System Name**, type a descriptive name.
4. To automatically enable collection from the syslog, select the check box.
5. In **Syslog System Port**, type the port where the agent receives syslog messages. The default port is 1515.
6. In **Local Syslog Cache Disk Limit (MB)**, type the maximum amount of disk space you want to allow to store syslog messages before they are transmitted to Alert Logic. Larger values allow the agent to store more message when the agent is unable to transmit message to Alert Logic.The default limit is 10000.
7. Select the check box to enable the agent to collect docker container logs.
8. Click **SAVE**.
9. In the Manage Assets section, search for assets from which to collect logs.
10. Select the tags or topology elements from the drop-down list. Tags are separated by <kbd>AND</kbd>, and topology elements are separated by <kbd>OR</kbd>. Tags and topology elements are separated by <kbd>OR</kbd>.
11. Click **SAVE**.
12. Ensure **Collect** is turned on for the application you just created in the Application Logs list.

**To create a Windows Event syslog collection**:

1. In the System Logs page, click the add icon (![](../Resources/Images/Icons/cdAddPlus.png)).
2. Click **Windows Event Log**.
3. In**System Name**, type a descriptive name.
4. Under Event Streams, select the streams from which you want to collect, or select **Collect All** to collect from all streams available.
5. Click **SAVE**.
6. In the Manage Assets section, search for assets from which to collect logs.
7. Select the tags or topology elements from the drop-down list. Tags are separated by <kbd>AND</kbd>, and topology elements are separated by <kbd>OR</kbd>. Tags and topology elements are separated by <kbd>OR</kbd>.
8. Click **SAVE**.

## Manage syslogs

The System Logs page lists all configured system logs by default. You can use the  drop-down list to view only Linux System Logs or Windows Event Logs. You can further sort the page by log types or name, and organize the list by ascending or descending order.  You can also use the search bar to find a specific system log collection. Click **View** to view details on enabled application logs.

### Edit an existing syslog collection

To edit an existing syslog collection:

1. From the view,  click the edit icon (![](../Resources/Images/pencil icon.png)) for the syslog collection you want to edit.
2. Make the necessary changes. For more information, see [Add a syslog collection](#Add-new-application-rule).
3. Click **SAVE**.

### Manage assets for an existing syslog collection

**To manage assets for an existing syslog collection**:

1. From the view, click the assets icon (![](../Resources/Images/Icons/assets.png)) for the syslog collection you want to scope assets.
2. In the Manage Assets section, select or clear the tags or topology elements from the drop-down list. For more information, see [Add a syslog collection](#Add-new-application-rule).
3. Click **SAVE**.

### Duplicate an existing syslog collection

**To duplicate an existing syslog collection:**

1. From the view, click the duplicate icon (![](../Resources/Images/Icons/duplicate.png)) for the syslog collection you want to copy.
2. Make the necessary changes. For more information, see [Add a syslog collection](#Add-new-application-rule).
3. Click **SAVE**.

### Delete an existing syslog collection

To delete an existing syslog, from the view,  click the delete icon (![](../Resources/Images/Icons/trash icon.png)) for the syslog collection you want to edit.Click **DELETE**.

You cannot delete the default system log templates, including ones that are not enabled.
