# Incident Notifications

The Notifications feature in the Alert Logic console can alert you, other subscribed users, or a configured [connector](../connectors.md) (such as a webhook) when incidents that meet specific criteria  occur.

For example, you can subscribe recipients to receive email notifications about escalated incidents for a single account or all incidents in all the managed accounts of a partner, or all high and critical incidents in the production deployment of a managed account. You can also send incident notifications to a ticketing system, reducing manual effort.

For more information about the Notifications feature, see [Notifications](../notifications.md) and [Manage Notifications](manage.md).

## Create an incident notification

You can create an incident notification from the Incidents List or the Notifications page. Whichever method you use, the process is the same after  you open the Create an Incident Notification page.

Alert Logic recommends that you create the incident notification from the Incident List. After looking at historical incidents to develop and validate a filter (see [Incident filters](../../analyze/incidents.md#filters)),  apply the filter, and then create the notification. When you create the notification from the filtered list, Alert Logic applies the filter to the notification for you.

**To create an incident notification from the Incident List:**

1. In the Alert Logic console, click the menu icon (![](../../Resources/Images/dashboard/menu-icon.png)).
2. Click ![](../../Resources/Images/dashboard/respond-icon.png)**Respond**, and then click **Incidents** to access the Incidents page.
3. On the **Incidents** page in the Alert Logic console, click the **Lists** tab.
4. (Optional) Filter the Incident List so it displays the information you want to be notified about. For more information, see [Incident filters](../../analyze/incidents.md#filters).
5. Click ![](../../Resources/Images/dashboard/notifications-icon.png)  **NOTIFICATIONS**, and then click **Add Notification**.
6. Click **ADD NOTIFICATION**.
7. Complete the fields in the Create an Incident Notification page. If you filtered the Incident List, Alert Logic applies the filters to the notification automatically, which you can adjust.

To create an incident notification from the Notifications page:

1. In the Alert Logic console, click the menu icon (![](../../Resources/Images/dashboard/menu-icon.png)).
2. Click ![](../../Resources/Images/dashboard/manage-icon.png)**Manage**, and then click **Notifications** to access the Notifications page.
3. In the Alert Logic console, click the Settings icon (![](../../Resources/Images/supportThreeDots.png)), and then click **Notifications**.
4. On the **Alert Notifications** tab, click the add icon (![](../../Resources/Images/Icons/cdAddPlus.png)) , and then click **Incident**.
5. Complete the fields in the Create an Incident Notification page.

**To complete the Create an Incident Notification page:**

1. Type a descriptive name for the incident notification—for example, "Critical Incidents for On-Call Team."
2. If you want to send the notification, leave  **Notification Is Active** turned on. Turn it off if you want to save the definition but not activate the notification yet.
3. For an account without [managed accounts](../../prepare/users-roles.md#multiaccount), your customer account is preselected, and the account selector does not appear. If your account is a managing (parent) account, select one or more accounts for which you want to send notifications. You can use the search bar to help you find:
If you choose **Managed Accounts** or **My Account and Managed Accounts**, future  managed accounts will be automatically  subscribed to receive the notification.  You will not need to edit the notification later to add them manually.
   * **Individual accounts**            —Your account and  individual managed accounts
   * **Managed Accounts**            —This option selects all your managed accounts, excluding your own account, plus any managed accounts added later on.
   * **My Account and Managed Accounts**            —This option selects your account and all your managed accounts, plus any managed accounts added later.
5. (Optional) If you do not want to receive a notification for incidents escalated by Alert Logic, turn off **Escalated Incidents**. Alert Logic escalates an incident to bring it to your attention, based on the severity and validity of the incident, and recommends that you leave this setting turned on.
6. (Optional) Under **Threat Levels**, select one or more incident threat levels for which you want to receive notifications.

Incident threat levels convey the severity of each incident raised for protected assets, which allows you to assess and prioritize the actions to take toward threat remediation. Alert Logic categorizes incidents with the following icons and colors:   * ![](../../Resources/Images/Icons/threat_critical_icon.png) Critical
   * ![](../../Resources/Images/Icons/threat_high_icon.png) High
   * ![](../../Resources/Images/Icons/threat_medium_icon.png) Medium
   * ![](../../Resources/Images/Icons/threat_low_icon.png) Low
   * ![](../../Resources/Images/Icons/threat_info_icon.png) Info
      If you select the escalation option and a threat level, an incident must match both criteria to trigger a notification. Alert Logic sends a notification for the escalation only to prevent duplicate notifications. By combining the Threat Levels and Escalations settings, you can limit notifications for escalated incidents to only selected threat levels, regardless of whether Alert Logic considers the incidents worthy of escalation.      10. Select other filters you want to include in the notification rule:
   * **Threat Level**—To receive notifications for incidents that reach one or more [threat levels](../../analyze/incidents.md#aboutThreatLevels), which can range in severity from Info to Critical.
   * **Classification**—To receive notifications for specific incident [classification types](../../analyze/incidents.md#aboutIncidentClasses) such as a brute force attack or worm activity.
   * **Detection Source**—To receive notifications related to specific incident detection source—for example, GuardDuty or IDS.
   * **Deployment**—To receive notifications for incidents that pertain to a specific deployment.
   * **Assets**—To receive notifications for incidents that pertain to assets, such as specific networks.
12. To subscribe users to receive a notification email, click **Subscribe User(s)**, and then, under **Notification Delivery**:6. To subscribe a connector, click **Subscribe Connector**, and then, under **Notification Delivery**, select a configured connector. The connector URL or connector email address will receive the payload listed.
7. Click **SAVE**.
   1. Select the users that you want to receive the notification. The list includes your name and user names  in the managed accounts selected above, if applicable. You can use the search bar to help you find recipients.
   2. (Optional) Customize the **Email Subject**. You can change the text and insert variables enclosed with double braces: {{*variable*}}. For the variable list, see [Email subject variables](#Emailsubjectvariables).

    You can configure log message [correlations](log-correlation.md) to generate an incident when the correlation criteria are met. If you choose to create a notification for a correlation incident, Alert Logic selects your account and the correlation rule as the criteria for the incident notification and excludes settings that are not applicable such as Escalations and Threat Levels.     ## Email subject variables

To customize the subject line of an email notification, you can add the following variables to the Email Subject field:

| Variable | Description | Example |
|---|---|---|
| {{attack_summary}} | Brief description of the incident | Brute force attempt from 203.0.113.1 |
| {{cid}} | Customer account ID | 12345678 |
| {{class}} | Incident classification type | brute-force |
| {{correlation_rule_name}} | Name of the [correlation](log-correlation.md) that triggered the incident | Admin Failed Login Correlation |
| {{create_date}} | Incident creation date and time | 24th May 2020 22:35:26 GMT |
| {{customer_name}} | Name of customer affected by the incident | XYZ Corporation |
| {{deployment_name}} | Name of deployment affected by the incident | AWS Production Deployment |
| {{incident_id}} | Short incident ID | 8fn5sf |
| {{is_escalated}} | Escalation status | true |
| {{location_ip}} | One or more IP addresses, if determined, of the attacker for this incident | 192.0.2.1 192.0.2.25 |
| {{start_date}} | Date and time that incident automated analysis started. For some incidents, start_date equals create_date. | 24th May 2020 22:36:06 GMT |
| {{target_host}} | IP address, if determined, of the target affected by the incident | 10.1.2.3 |
| {{threat}} | Incident threat level | Critical |

Note to Info Dev: The following are the variables for the connectors project and might eventually be used for notifications. The snippet has already had an ID edit.

<table>
  <col />
  <col />
  <col />
  <thead>
    <tr>
      <th>Variable</th>
      <th>Description</th>
      <th>Example</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <p>{{accountId}}</p>
      </td>
      <td>Customer account identifier</td>
      <td>12345678</td>
    </tr>
    <tr>
      <td>{{correlation_name}}</td>
      <td>Name of <a href="log-correlation.md">correlation</a> that triggered the incident</td>
      <td>
        <p>Admin Failed Login Correlation</p>
      </td>
    </tr>
    <tr>
      <td>{{createtime_str}}</td>
      <td>Incident creation date and time in UTC</td>
      <td>2020-08-10T11:22:27.799796+00:00</td>
    </tr>
    <tr>
      <td>{{customer}}</td>
      <td>Customer name of the Alert Logic account affected by the incident</td>
      <td>XYZ Corporation</td>
    </tr>
    <tr>
      <td>{{deployment}}</td>
      <td>Name of deployment affected by the incident</td>
      <td>AWS Production Deployment</td>
    </tr>
    <tr>
      <td>{{extra.location_ip}}</td>
      <td>One or more IP addresses, if determined, of the attacker for this incident</td>
      <td>192.0.2.1 192.0.2.25</td>
    </tr>
    <tr>
      <td>{{extra.target_host}}</td>
      <td>One or more IP addresses, if determined, of the target affected by the incident</td>
      <td>10.1.2.3</td>
    </tr>
    <tr>
      <td>
        <p>{{humanFriendlyId}}</p>
      </td>
      <td>Short incident ID</td>
      <td>8fn5sf</td>
    </tr>
    <tr>
      <td>
        <p>{{incident_attack_class}}</p>
      </td>
      <td>Incident classification type</td>
      <td>brute-force</td>
    </tr>
    <tr>
      <td>{{incident_escalated}}</td>
      <td>Escalation status</td>
      <td>
        <p>Valid values:</p>
        <ul>
          <li>true</li>
          <li>false</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>
        <p>{{incident.summary}}</p>
      </td>
      <td>Brief description of the incident that is suitable as a title or message subject</td>
      <td>Brute force attempt from 1.2.3.4</td>
    </tr>
    <tr>
      <td>{{incident_threat_rating}}</td>
      <td>Incident threat level</td>
      <td>Critical</td>
    </tr>
  </tbody>
</table>## View and manage incident notifications

You can view and manage incident notifications from the Notifications page.  See [Manage Notifications](manage.md) for information about how to:

* Filter the list of notifications
* View notification details
* Edit notifications
* Delete notifications

Alert Logic processes each notification rule independently, so it is possible to receive multiple notifications for a single incident.

## View and manage incident notifications

The Incident Notifications page  lists your existing incident notifications. You can [create](#createFromAlertsPage), view, and manage incident notifications  from this page.

To narrow the set of incident notifications listed, you can use the filters in the left navigation. You can also group and sort the notifications with tools available toward the top of the page.

To access the Incident Notifications page, from the Incidents page, click the **Notifications** tab.

You can click **View** next to a specific notification to see its details and manage the notification.

For more information, see:

* [Filter the incident notifications list](#filter)
* [Organize the incident notifications list](#organize)
* [Search the incident notifications list](#search)
* [Delete incident notifications](#Delete)
* [Edit an incident notification](#Edit)
* [View and manage incident notifications from the detail view](#view)

    You can also view and manage incident notifications from the [Manage Notifications page](manage.md).    ### Filter the incident notifications list

The Incident Notifications page displays all active incident notifications created from the customer account and its managed accounts. You can also display inactive or deleted notifications and apply additional filters to narrow the list to a specific set of notifications.

To filter the incident notifications list:

1. In the left navigation, click the notification status of interest:
   * **Active**
   * **Inactive** (notification is saved but not turned on)
   * **Deleted**
3. Click any of the following filters to further narrow the list. Available filters vary according to the notifications in your environment and filters you select:
   * Account
   * Recipients
   * Threat Level
   * Classification
   * Detection Source
   * Deployment
To display your own notifications, you can select yourself as the recipient.6. To search for a filter, type a filter value in **Search filters**.
For example, to quickly find notifications about incidents classified as application attacks type **attack**.10. To clear filters and start over, delete any text you typed in **Search filters** or select **CLEAR ALL FILTERS**.

### Organize the incident notifications list

You can organize the incident notifications list by grouping and sorting the notifications. Alert Logic groups your alerts by threat and sorts them by date within each grouping. You can group and sort the notifications by other criteria to suit your needs.

To organize your incident notifications:

1. To change the grouping, click **Group by**, and then click the option you want. Available options match the filters listed in the left panel.
2. To change the way the list of alert notifications is sorted within each grouping, click **Sort by**, and then click the option you want. Available options include Name, Create Time, and Updated Time. Available options include Date and filters listed in the left panel.

### Search the incident notifications list

You can use the search bar  to filter the list to include only notifications that contain specific words in important fields, like the notification name.

You can use the search bar  to filter the list to include only notifications that contain specific search words. You can search by notification name, recipients, and filter names.

### Delete incident notifications

In the incident notifications list, click the notification icon (![](../../Resources/Images/Icons/icon-notification.png))  next to each notification that you want to delete. On  the bottom of the page, click ![](../../Resources/Images/Icons/trash icon.png)**DELETE**.

If you want to delete all notifications currently listed, select the check box at the top of the list. On the bar that appears at the bottom of the page, click ![](../../Resources/Images/Icons/trash icon.png)**DELETE**).

### Edit an incident notification

You can edit an incident notification from the incidents list. For example, you can:

* Make the notification active or inactive
* Change notification filters
* Subscribe or unsubscribe users or a connector
* Change delivery options

To edit an incident notification:

1. In the incident notifications list, click the notification icon (![](../../Resources/Images/Icons/icon-notification.png)) next to the notification that you want to edit.
2. On the bottom of the page, click ![](../../Resources/Images/pencil icon.png)**EDIT**.
3. In the Edit an Incident Notification page, change any of the settings.

### View and manage incident notifications from the detail view

You can view the details about a specific incident notification. The detail view includes information such as the last time the notification was sent, creation and last modification date, notification rules (filter conditions for creating the alert), subscribed users or connector, and delivery options.

From the detail view, you can edit the notification, delete it,  and access the Incident List filtered to show incidents that meet the notification rules.

**To view details about a notification:**

1. From the Incidents page, click the **Notifications** tab.
2. To the right of the notification you want to view, click **View** .
3. When you are finished viewing notification details, click **Hide**.

To delete an incident notification:

1. From the Incidents page, click the **Notifications** tab.
2. To the right of the notification you want to delete, click **View**.
3. Toward the bottom of the detail view, click ![](../../Resources/Images/Icons/trash icon.png)**DELETE**.

Deleted notifications are moved from Active to Deleted status.

      An alternative to deleting a notification is to deactivate it. Edit the notification you want to deactivate, and then turn off **Send Notifications**.      
To edit an incident notification:

1. From the Incidents page, click the **Notifications** tab.
2. To the right of the notification you want to edit, click **View**.
3. Toward the bottom of the detail view, click ![](../../Resources/Images/pencil icon.png)**EDIT**.
4. In the Edit an Incident Alert page, change any of the settings.

**To open a list of incidents corresponding to the notification criteria:**

1. From the Incidents page, click the **Notifications** tab.
2. To the right of the notification, click **View**.
3. Toward the bottom of the detail view, click (icon) **INCIDENT LIST**.

Open the list of incidents  to evaluate the notification criteria. You can review the  incidents that the notification triggers.
