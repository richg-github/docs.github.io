# Configure Slack Webhook Connector

You can configure a webhook connector in the Alert Logic console  to send [notifications](../notifications.md) to Slack in near real time. When  you set up a notification and subscribe a webhook connector, the connector sends the event to the target URL you configured and creates a message in Slack automatically.

Alert Logic notifications alert you to threats, changes, and scheduled events in your environment so you can respond quickly. From the Alert Logic console, you can subscribe your Slack webhook to receive:

* [Incident notifications](../notifications/incident.md)        —Send a message when incidents occur that meet specific criteria, such as escalated incidents.
* [Log correlation notifications](../notifications/log-correlation.md)        —Send a message when your log correlation rules trigger an incident or observation.
* Exposure alerts
* [Scheduled report notifications](../notifications/report.md)        —Send a message when Alert Logic generates a scheduled report  that is available for download.
* Scheduled search results

Complete the following steps to successfully send messages to Slack:

1. [Select or Create a Connection Target](#SelectorCreateaConnectionTarget)
2. [Generate the target URL](#GeneratethetargetURL)
3. [(Optional) Customize the payload template](#(Optional)Customizethesamplepayloadtemplate)
4. [Create the Slack webhook connector from the Alert Logic console](#CreatetheSlackwebhookconnectorfromtheAlertLogicconsole)
5. [Subscribe your webhook to receive notifications](#Subscribeyourwebhooktoreceivenotifications)

## Select or Create a Connection Target

Before creating a connector, you must first configure a connection target. Connection targets define common authentication path and credential references for external systems. For more information, see [Configure Slack Connection Target](../../Z-Sandbox/bbaskin/connectors-beta/connection-targets/slack.md).

## Generate the target URL

Before you create the webhook connector in the Alert Logic console, complete the instructions in the [Slack documentation](https://api.slack.com/messaging/webhooks) to generate the incoming webhook URL. Copy the URL, which you must paste into the Target URL field.

## (Optional) Customize the payload template

Decide which type of security information that you want Alert Logic to send to Slack: Incident, Observation (of a log correlation), or a Scheduled Report Notification payload.

    If you want to send more than one payload type, you must configure a connector for each one. Because the payload is different, each payload type requires a separate connector instance.     
Alert Logic provides a payload template for an incident and an observation in JSON format using Mustache template-like transformations where a field in the JSON payload can be referenced by enclosing it in braces ({{}}. For example, the threatRating field in the following JSON {'incident': {'threat.Rating': "critical"}} is specified as {{incident.threatRating}}. A payload template converts the Alert Logic security information to the format expected by Slack. You can add or remove lines in the sample template to meet your workflow requirements and security goals. If you want to create a Slack connector for scheduled report notifications, you will need to configure the payload template.

For definitions of the Alert Logic variables in the templates and the full  JSON that you can use to configure your payload template in JQ or JSON format, see:

* [Incident Schema](../connectors/incident.md)
* [Observation Schema](../connectors/observation.md)
* [Scheduled Report Notification Schema](../connectors/scheduled-report-notification-payload.md)

    For more information about Mustache, see the [Mustache Manual](https://mustache.github.io/mustache.5.html). For more complex transformations, you can use [JQ](https://stedolan.github.io/jq/#:~:text=jq). A helpful website for converting JSON to JQ is [jq play](https://jqplay.org/).    ### Incident payload template

JSON Template

| 1 | { |
| 2 | "text": "{{incident.summary}}", |
| 3 | "blocks": [{ |
| 4 | "type": "section", |
| 5 | "text": { |
| 6 | "text": "{{incident.summary}}", |
| 7 | "type": "plain_text" |
| 8 | } |
| 9 | }, { |
| 10 | "type": "section", |
| 11 | "text": { |
| 12 | "text": "{{desc}}", |
| 13 | "type": "mrkdwn" |
| 14 | } |
| 15 | }, { |
| 16 | "type": "section", |
| 17 | "text": { |
| 18 | "text": "{{incident.recommendations}}", |
| 19 | "type": "mrkdwn" |
| 20 | } |
| 21 | }] |
| 22 | } |

### Observation payload template

JSON Template

| 1 | { |
| 2 | "text": "{{fields.summary}}", |
| 3 | "blocks": [{ |
| 4 | "type": "section", |
| 5 | "text": { |
| 6 | "text": "*Summary:* {{fields.summary}}", |
| 7 | "type": "mrkdwn" |
| 8 | } |
| 9 | }, { |
| 10 | "type": "divider", |
| 11 | "block_id": "divider1" |
| 12 | }, { |
| 13 | "type": "section", |
| 14 | "text": { |
| 15 | "text": "*Description:* {{fields.desc}}", |
| 16 | "type": "mrkdwn" |
| 17 | } |
| 18 | }, { |
| 19 | "type": "divider", |
| 20 | "block_id": "divider2" |
| 21 | }, { |
| 22 | "type": "section", |
| 23 | "text": { |
| 24 | "text": "*Recommendations:* {{fields.recommendations}}", |
| 25 | "type": "mrkdwn" |
| 26 | } |
| 27 | }, { |
| 28 | "type": "divider", |
| 29 | "block_id": "divider3" |
| 30 | }, { |
| 31 | "type": "section", |
| 32 | "text": { |
| 33 | "text": "*Details*", |
| 34 | "type": "mrkdwn" |
| 35 | }, |
| 36 | "fields": [{ |
| 37 | "text": "*Customer ID:*", |
| 38 | "type": "mrkdwn" |
| 39 | }, { |
| 40 | "type": "plain_text", |
| 41 | "text": "{{id.account}}" |
| 42 | }, { |
| 43 | "type": "mrkdwn", |
| 44 | "text": "*Class:*" |
| 45 | }, { |
| 46 | "type": "plain_text", |
| 47 | "text": "{{fields.class}}" |
| 48 | }, { |
| 49 | "type": "mrkdwn", |
| 50 | "text": "*Subclass:*" |
| 51 | }, { |
| 52 | "type": "plain_text", |
| 53 | "text": "{{fields.subclass}}" |
| 54 | }, { |
| 55 | "type": "mrkdwn", |
| 56 | "text": "*Severity*" |
| 57 | }, { |
| 58 | "type": "plain_text", |
| 59 | "text": "{{fields.severity}}" |
| 60 | }] |
| 61 | }] |
| 62 | } |

## Create the Slack webhook connector from the Alert Logic console

After you generate the target URL and optionally customize  the payload template, the next step is to create the webhook in the Alert Logic console  and test the payload.

**To create a Slack webhook connector**:

1. In the Alert Logic console, click the navigation menu icon (![](../../Resources/Images/dashboard/menu-icon.png)), click ![](../../Resources/Images/dashboard/configure-icon.png)**Configure**, and then click **Connectors**.
2. On the Connectors page, click the add icon (![](../../Resources/Images/Icons/cdAddPlus.png)), and then click **Slack**.
3. On the Create a Slack Connector page, type a descriptive name for the webhook connector—for example, "Slack Webhook Connector for Incidents."
4. In  **Target URL**, paste the URL that you copied earlier.
5. Choose the **Payload Type**, which is the type of Alert Logic security information that you want to send: **Incident**, **Observation** (of a log correlation), or **Scheduled Report Notification**.
6. Choose the format of the payload template you customized earlier: **JSON**  or **JQ**.
7. Enter the payload template that you customized.
      A red bar next to a line indicates a syntax error. Code with errors is underlined with a jagged red line. You can hover the pointer over the underlined code to view a tip about the error.      9. Click **TEST** to send a test webhook request to the target URL provided. For more information, see [Connector test results](#Connectortestresults).
10. If your webhook connector sent the test event to the target URL successfully, click **SAVE**.

### Connector test results

If you receive a message that the connector was successfully tested, Alert Logic sends the payload template you configured and populates a message in Slack with sample data. Check Slack to ensure the results are expected, and adjust the payload template if necessary.

If the test is unsuccessful, Alert Logic displays an error message. For server response errors, you can use the error code and message that Alert Logic passes through to troubleshoot the issue. Alert Logic also informs you if your JSON or JQ payload template contains syntax errors.

## Subscribe your webhook to receive notifications

After you test and save the connector configuration, the last step is to set up your notification criteria and subscribe the webhook.

You can set up and manage a notification of any type directly from the Notifications page. For more information, see [Manage Notifications](../notifications/manage.md). You can create notifications from other pages according to notification type:

* For incidents, you can also create a notification from the Incidents page. For more information, see [Incident Notifications](../notifications/incident.md).
* For observations, you can also create a notification   from the Search page (Log Search tab or Correlations tab) during the process of creating the correlation or by editing an existing correlation listed on the Correlations tab. For more information, see [Correlations and Notifications](../notifications/log-correlation.md) and [Observation Notifications](../notifications/observation.md).
* For health exposures, you can also create a notification from the Health page. For more information, see [Health](../../analyze/health.md).
* For scheduled reports, you can also schedule the report and subscribe notification recipients from the Reports page. For more information, see [Scheduled Reports and Notifications](../notifications/report.md).
* For scheduled File Integrity Monitoring (FIM) searches, you can schedule a search and subscribe notification recipients from the Notifications page. For more information, see [File Integrity Monitoring Search Notification](../notifications/fim-search.md).

## Manage your connectors

You can view the list of connectors and edit or delete an existing one. For more information, see [Manage Connectors](../connectors/manage-connectors.md).
