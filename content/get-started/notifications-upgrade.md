# Notifications Upgrade

Alert Logic upgraded the Notifications feature in Managed Detection and Response (MDR) to add new notification types. If you previously subscribed to incident or health status notifications  in the Alert Logic console, your notifications are still active and sent to  subscribed recipients.

For more information about the updated Notifications feature, see [Notifications](../configure/notifications.md) and [Manage Notifications](../configure/notifications/manage.md).

## New notification types in MDR

Alert Logic added two new types of notifications:

* [Log correlations](../configure/notifications/log-correlation.md)        —You can now set up and save a log correlation rule and configure it to create an observation or an incident and send a notification when a match occurs.
* [Scheduled reports](../configure/notifications/report.md)        —You can set up and save a report schedule to generate a report periodically  and send a notification when the report is generated. If you previously set up a Health Status notification, Alert Logic [upgraded](#health-migration) it as a scheduled report. After a scheduled report is generated, Alert Logic saves it for viewing and download.

## Information for Cloud Defender customers upgrading to MDR

For Cloud Defender customers, your upgrade to MDR provides feature parity for notifications, including:

* Incident notifications
* Report scheduling, with a new capability to send a notification
* Log correlation notifications

The upgrades to these features are also available in Cloud Defender. If you are upgrading to MDR and had not upgraded to the newer notification experience, your notifications

Migration precheck says:

In MDR, a health summary report notification replaces your Cloud Defender collection alerts. If you  subscribe to receive collection alerts, Alert Logic schedules the [Daily Health Summary](../analyze/reports/service/health/daily-health-summary.md) report for you and subscribes the same recipients to receive a notification when the report is generated. You can change the schedule and recipients or unsubscribe. For more information, see [Scheduled Reports and Notifications](../configure/notifications/report.md).

Your existing scheduled reports cannot be migrated because the Reports offering is upgraded in MDR. For help finding similar information from Cloud Defender Scheduled reports in MDR, see [Managed Detection and Response Reports Upgrade](upgrade-reports.md). For information about scheduling the reports, see [Scheduled Reports and Notifications](../configure/notifications/report.md).

## Incident notification upgrade

Alert Logic created equivalent subscriptions that trigger on the same conditions.

### How to find your incident notifications

You can view and manage your existing incident notifications from the Notifications page, which you can access from the Incidents page or the Manage group in the navigation menu.

To access incident notifications from the Incidents page:

1. In the Alert Logic console, click the menu icon (![](../Resources/Images/dashboard/menu-icon.png)).
2. Click ![](../Resources/Images/dashboard/respond-icon.png)**Respond**, and then click **Incidents**.
3. Click ![](../Resources/Images/dashboard/notifications-icon.png)**NOTIFICATIONS** at the top right, and then click **View Notifications**.
4. On the **Incidents** page, click the **ADD NOTIFICATION** drop-down menu, and then click **View Notifications**.

Your incident notifications appear  on the Notifications page in the Alert Notifications tab. Alert Logic filters the list to show only the Incidents notification type.

To access incident notifications from the Manage navigation group:

1. In the Alert Logic console, click the menu icon (![](../Resources/Images/dashboard/menu-icon.png)).
2. Click ![](../Resources/Images/dashboard/manage-icon.png)**Manage**, and then click **Notifications**.
3. In the Alert Logic console, click the Settings icon (![](../Resources/Images/supportThreeDots.png)), and then click **Notifications**
4. (Optional) In the left panel, click **Incidents**, under **Type**, to filter the list to show only your incident notifications.

To view details for a migrated incident notification:

Click **View** to the right of the notification for which you want to view details. You can see the notification rule, recipients, and more.

### How your incident notifications were upgraded

Alert Logic mapped your existing incident notifications to new ones:

* For escalated incident notifications, the notifications list includes a notification with "Escalated" in the name.
* For incident notifications based on threat level, the notifications list includes one notification per threat level category.

    If you set up notifications for multiple threat levels such as high and critical, but prefer  managing fewer notifications, you can delete those notifications and create one new notification for threat level categories of high and above. For information about how to delete notifications and create a new one, see [Incident Notifications](../configure/notifications/incident.md).    
Alert Logic subscribed the email recipients that were set up in the original notification. To see the subscribed recipients, you can click **View** to the right of the notification name.

## Health Status notification upgrade

If you  previously set up Health Status email notifications, Alert Logic upgraded them as scheduled health report notifications. You can also set up alert style [ Health Notifications](../configure/notifications/health.md) to alert you, subscribed users, or a configured connector when an agent, appliance, or API collector is collecting data or offline (unhealthy).

### How to find Health alert notifications

You can view and manage  alert style [ Health Notifications](../configure/notifications/health.md) from the Notifications page, which you can access from the Health page or the Manage group in the navigation menu.

**To create a health notification from the Health page:**

1. In the Alert Logic console, click the menu icon (![](../Resources/Images/dashboard/menu-icon.png)).
2. Click ![](../Resources/Images/dashboard/respond-icon.png)**Respond**, and then click **Health** to access the Health page.
3. Click ![](../Resources/Images/dashboard/notifications-icon.png)  **NOTIFICATIONS**, and then click **View Notifications**.

To create a health notification from the Notifications page:

1. In the Alert Logic console, click the menu icon (![](../Resources/Images/dashboard/menu-icon.png)).
2. Click ![](../Resources/Images/dashboard/manage-icon.png)**Manage**, and then click **Notifications** to access the Notifications page.
3. (Optional) In the left panel, click **Health**, under **Type**, to filter the list to show only your health notifications.

### How to find your existing Health Status notifications

Your Health Status notifications were upgraded as [scheduled report notifications](../configure/notifications/report.md). For more information about how they were upgraded, see [How your Health Status notifications were upgraded](#health-migration). You can view and manage your Health Status notifications  from the Notifications page, which you can access from the Reports page or the Manage group in the navigation menu.

To access scheduled health report notifications from the Reports page:

1. In the Alert Logic console, click the menu icon (![](../Resources/Images/dashboard/menu-icon.png)).
2. Click ![](../Resources/Images/dashboard/validate-icon.png)**Validate**, and then click **Reports**.
3. Click ![](../Resources/Images/dashboard/notifications-icon.png)**NOTIFICATIONS** at the top right, and then click **View Notifications**.

Your report schedules and their notifications appear  on the Notifications page in the Schedules tab.

To access scheduled health report notifications from the Manage navigation group:

1. In the Alert Logic console, click the menu icon (![](../Resources/Images/dashboard/menu-icon.png)).
2. Click ![](../Resources/Images/dashboard/manage-icon.png)**Manage**, and then click **Notifications**.
3. Click the **Schedules** tab to open the report schedule list on the Notifications page.

To view details for a migrated health notification:

Click **View** to the right of the notification for which you want to view details. You can see the report schedule, notification rule, recipients, and more.

### How your Health Status notifications were upgraded

Alert Logic mapped your existing Health Status notifications to the new [Daily Health Summary](../analyze/reports/service/health/daily-health-summary.md) report. The report will be generated automatically according to the frequency set up in the former Health Status notification.

Alert Logic mapped your existing Health Status notifications to the new [Daily Health Summary](../analyze/reports/service/health/daily-health-summary.md), [Weekly Health Summary](../analyze/reports/service/health/weekly-health-summary.md), or Monthly Health Summary reports. The frequency set up in the former Health Status notification determines which report will be generated automatically.

Recipients subscribed in the original notification will receive an email notification with the report attached in PDF format when the report is generated. To see the subscribed recipients, you can click **View** to the right of the report schedule name. To see the list of reports generated by the schedule, you can click the Downloads tab on the Reports page.
