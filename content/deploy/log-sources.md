# Log Sources

A log source is a software or hardware component that produces log data. Multiple types of sources exist, and multiple methods exist to retrieve log data from the sources. The Alert Logic console allows you to create, edit, and update log sources, archive or restore old sources, and perform other tasks.

## Supported log sources

Alert Logic supports log source types for all deployments, including Data Center, Amazon Web Services (AWS), and Microsoft Azure. For more information about creating, editing, and updating log sources for a specific deployment, see:

* [Configure Log Sources for All Deployments](log-sources/log-sources-all-deployments.md)
* [Configure Log Sources for Amazon Web Services (AWS)](log-sources/log-sources-aws.md)
* [Configure Log Sources for Microsoft Azure](log-sources/log-sources-azure.md)
* [Alert Logic Log Collector for Microsoft Azure Event Hubs](../prepare/azure-event-hubs-log-collector.md)

**To access the Log Sources page**:

1. In the Alert Logic console, click the menu icon (![](../Resources/Images/dashboard/menu-icon.png)) to see the navigation menu.
2. Click ![](../Resources/Images/dashboard/configure-icon.png)**Configure**, and then click **Deployments**.
3. Click the deployment for which you want to configure log sources.
4. On the bottom left of the screen, click **CONFIGURE LOG SOURCES**.

## View log source information

Click any log source to view a slideout panel that contains the following details about the log source:

* **Details** :This tab displays all information about the collection source, including the account number, the public host name, when it was created or modified, and the host ID.

The **Status** field lists any current errors.* **Metadata History**: This tab displays only the metadata history for the collection source.
* **Status History**: This tab displays only the status history, including the current status of the collection source.
* **Stats**: This tab displays only the statistics of the most recent log messages received, including the date, size, count for the hour, day, and month.

## Mass edit sources

The Mass Edit feature allows you to edit policies and tags for all   sources, filtered sources, or sources you specify. The feature also includes mass archive options.

The mass edit and mass archive/delete features have a maximum number of entries that they can handle. If you have an issue using the feature on a large number of entries, use the Alert Logic API instead.

**To mass edit log sources:**

1. On the Log Sources page, click the gear icon (![](../Resources/Images/Icons/gear icon.png)).
2. Select **Mass Edit**.
3. In **Apply changes to**, select:
   * **All Sources** to mass edit all sources
   * **Only Filtered Sources** to mass edit only filtered sources
   * **Only Selected Sources** to mass edit only selected sources
5. From **Collection Policy**, select the collection policy to use.
6. From **Replace Collection Alerts**, select an alert to apply to the selected sources.        This action overrides the current alerts that correspond to the selected sources. If you leave this option blank, current alerts will not change.
7. Select **Enable Collection**.
8. In **Tags**, select a tag option from the drop-down menu. Below, type a tag to follow the rule selected in the drop-down menu.
9. In **Archive Sources**, select an option from the drop-down menu.
10. Click **SAVE**.

## Archive and restore log sources

Archive a collection source to remove the log source entry from the Log Sources page, and make it available for use at a later time.

To archive a collection source:

1. From the Deployments page, click the  deployment for which you want to archive log sources.
2. Click **CONFIGURE LOG SOURCES**.
3. Place your cursor over the desired collection source and click the **Archive** icon (![](../Resources/Images/archive.png)).
4. Click **ARCHIVE**.

    You cannot archive a log source that stops log collection.    
To restore an archived log source:

1. From the Deployments page, click the  deployment to which you want to restore an archived log source.
2. Click **CONFIGURE LOG SOURCES**.
3. Above the log source table, select **Show Archive**.
4. Place your cursor over the desired collection source  and click the **Archive** icon (![](../Resources/Images/archive.png)).
5. Click **RESTORE**.

If your host credentials change frequently  as part of a security best practice,           Alert Logic recommends you use an agent for log collection. If you use the agent for log collection, your host credentials cannot expire.
