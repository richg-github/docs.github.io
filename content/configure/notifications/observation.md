# Observation Notifications

When a log [correlation](log-correlation.md) occurs that meets specific criteria, Alert Logic  can send you, other subscribed users, or a configured [connector](../connectors.md) (such as a webhook) an observation notification.

For more information about the Notifications feature in the Alert Logic console, see [Notifications](../notifications.md) and [Manage Notifications](manage.md).

## Create an observation notification

When you create a correlation, you can set up a notification in the next step. You can also add  notifications to a correlation at any time.

To create a correlation and add an observation notification:

If the log correlation for which you want to send notifications is not created yet, when you [create the correlation](log-correlation.md#Create),  select **Observation** as the type of correlation result to generate.

When you click **SAVE AND CONTINUE**, the Create an Observation Notification page opens with the correlation already added as a notification filter.

To add an observation notification to an existing correlation:

From the Search page, listed under ![](../../Resources/Images/dashboard/investigate-icon.png)**Investigate** in the Alert Logic console, click the **Correlations** tab to open the [Correlations page](log-correlation.md#View). Find the Observation type correlation for which  to add the notification, click **Preview**, and then do either of the following:

From the **Search** page, click the **Correlations** tab to open the [Correlations page](log-correlation.md#View). Find the Observation type correlation for which  to add the notification, click **Preview**, and then do either of the following:

* Click **+ADD** in the Notifications area of the detail view.
* Click the **EDIT** icon in the detail view, and then click **SAVE AND CONTINUE** in the Edit a Correlation page.

Using either of these methods, the Create an Observation Notification page opens with the correlation already added as a notification filter.

**To complete the Create an Observation Notification page:**

1. Type a descriptive name for the observation notification—for example, "Admin Failed Login Correlation."
2. Ensure  the correlation that you are creating the notification for is selected under **Correlation Rule**.
3. To subscribe users to receive a notification email, click **Subscribe User(s)**, and then, under **Notification Delivery**:
   1. Select the users that you want to receive the notification. The list includes your name and user names  in the managed accounts selected above, if applicable. You can use the search bar to help you find recipients.
   2. (Optional) Customize the **Email Subject**. You can change the text and insert  variables enclosed with double braces: {{*variable*}}. For the variable list, see [Email subject variables](#Emailsubjectvariables).
5. To subscribe a connector, click **Subscribe Connector**, and then, under **Notification Delivery**, select a configured connector. The connector URL will receive the payload listed.
6. Click **SAVE**.

## Email subject variables

To customize the subject line of an email notification, you can add the following variables to the Email Subject field:

| Variable | Description | Example |
|---|---|---|
| {{cid}} | Customer account ID | 12345678 |
| {{correlation_rule_id}} | Identifier of the [correlation](log-correlation.md) rule | D561C0E9-FE6A-48C8-869E-FDED55167FEE |
| {{correlation_rule_name}} | Name of the correlation that triggered the observation | Windows Users Added in Bulk by an Administrator |
| {{create_date}} | Observation creation date and time | 18th Feb 2020 22:27:41 GMT |
| {{customer_name}} | Name of the customer affected by the observation | XYZ Corporation |
| {{deployment_name}} | Name of the deployment affected by the observation | AWS Production Deployment |
| {{observation_id}} | Identifier of the observation | 00000000-1234-1234-1234-1234567890 |
| {{observation_summary}} | Summary of the observation | Windows users added in bulk to a security group by an Administrator |
| {{target_host}} | IP address, if determined, of the target affected by the observation | 10.1.2.3 |

## View and manage observation notifications

You can view and manage observation notifications from the Notifications page.  See [Manage Notifications](manage.md) for information about how to:

* Filter the list of notifications
* View notification details
* Edit notifications
* Delete notifications

From the Correlations page, you can view the notifications listed for a specific correlation and edit an observation notification. For more information, see [View and manage correlations](log-correlation.md#View).
