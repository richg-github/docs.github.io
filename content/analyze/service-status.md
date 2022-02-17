# Service Status

The Alert Logic Service Status page allows  customers to monitor the status of their subscribed region and product capabilities. Alert Logic provides updates for incidents in progress, including the overall status of Alert Logic regions and products, statuses for individual product capabilities, and details about past incidents. Alert Logic customers can also subscribe to notifications when Alert Logic creates, updates, or resolves an incident.

To access the Service Status page, in the Alert Logic console, open the ![](../Resources/Images/dashboard/manage-icon.png)**Manage** menu item, and then select **Service Status**. You can also access the Service Status page directly from [status.alertlogic.com](https://status.alertlogic.com/).

## Overall status

Alert Logic provides details and frequent updates on incidents in progress until the status is "Operational."

### Individual statuses 

You can view the status of individual Alert Logic capabilities for each data center (US-West-1, US-East-1, and UK-West-1). To view individual statuses, click the plus icon (![](../Resources/Images/Icons/settings/plus.png)).

The icon displayed indicates the status of each Alert Logic capability in a data center. Possible statuses include:

* Operational (![](../Resources/Images/Icons/settings/check.png)) – This capability is healthy
* Degraded Performance (![](../Resources/Images/Icons/settings/degraded.png)) –Intermittent issues are occurring
* Partial Outage (![](../Resources/Images/Icons/settings/partial.png)) – Some elements of this capability are unavailable
* Major Outage (![](../Resources/Images/Icons/settings/major.png)) – This capability is unavailable
* Maintenance (![](../Resources/Images/Icons/settings/maintenance.png)) – There is ongoing maintenance that may impact access to or performance of this capability

#### Scheduled Maintenance

Alert Logic posts upcoming scheduled maintenance messages in advance. The message includes details such as the type of maintenance, the date and expected duration, and the data center impacted.

## Past incidents

When Alert Logic resolves an incident, details and updates about the incident appear in the Past Incidents section. These details are available for three weeks before being removed from the page. If you do not subscribe to status notifications, this section can be helpful to keep you informed of any recent incidents.

## Subscribe to status notifications 

You can subscribe to notifications when Alert Logic creates, updates, or resolves an incident to the region or product capabilities you choose. Notifications can be sent by email (![](../Resources/Images/Icons/settings/email.png)), SMS (![](../Resources/Images/Icons/settings/text.png)), WebHook (![](../Resources/Images/Icons/settings/webhook.png)), or RSS or Atom feed (![](../Resources/Images/Icons/settings/rss.png)).

**To subscribe to notifications**:

1. On the top right of the page, click **Subscribe To Updates**
2. Select the tab for the type of notifications you want to receive, and then complete the required fields. For the RSS feed, click **Atom Feed** or **RSS Feed** to view the corresponding XML file link.
3. Click **Subscribe** to be redirected to Notification Subscription page.
4. Select the components in each region for  notifications you want to receive.
5. Click **Update Preferences**.

If you subscribed to email notifications, Alert Logic sends and email with instructions you must follow to confirm your subscription and start receiving notifications.

### Manage status notifications

You can change your notification preferences or unsubscribe from notifications on the Notification Subscription page at any time.

To access the Notification Subscription page:

1. From the Service Status page, click **Subscribe To Updates**, and then select the tab for the type of notification you want to manage.
2. Click **Subscribe**.

To unsubscribe, click **Cancel Subscription**, and then click **UNSUBSCRIBE FROM UPDATES**.

To change your preferences,  select or clear components in each region as needed, and then click **Update Preferences**.
