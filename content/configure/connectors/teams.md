# Configure Microsoft Teams Webhook Connector

You can configure a webhook connector in the Alert Logic console  to send [notifications](../notifications.md) to Microsoft Teams in near real time. When  you set up a notification and subscribe a webhook connector, the connector sends the event to the target URL you configured and creates a message in Microsoft Teams automatically.

Alert Logic notifications alert you to threats, changes, and scheduled events in your environment so you can respond quickly. From the Alert Logic console, you can subscribe your Microsoft Teams webhook to receive:

* [Incident notifications](../notifications/incident.md)        —Send a message when incidents occur that meet specific criteria, such as escalated incidents.
* [Log correlation notifications](../notifications/log-correlation.md)        —Send a message when your log correlation rules trigger an incident or observation.
* Exposure alerts
* [Scheduled report notifications](../notifications/report.md)        —Send a message when Alert Logic generates a scheduled report  that is available for download.
* Scheduled search results

Complete the following steps to successfully send messages to Microsoft Teams:

1. [Generate the target URL](#GeneratethetargetURL)
2. [(Optional) Customize the payload template](#(Optional)Customizethesamplepayloadtemplate)
3. [Create the Microsoft Teams webhook connector from the Alert Logic console](#CreatetheJirawebhookconnector)
4. [Subscribe your webhook to receive notifications](#Subscribeyourwebhooktoreceivenotifications)

## Generate the target URL

Before you create the webhook connector in the Alert Logic console, complete the instructions in the [Microsoft Teams documentation](https://docs.microsoft.com/en-us/microsoftteams/platform/webhooks-and-connectors/how-to/add-incoming-webhook) to generate the incoming webhook URL. Copy the URL, which you must paste into the Target URL field.

## (Optional) Customize the payload template

Decide which type of security information that you want Alert Logic to send to Microsoft Teams: Incident, Observation (of a log correlation), or a Scheduled Report Notification payload.

    If you want to send more than one payload type, you must configure a connector for each one. Because the payload is different, each payload type requires a separate connector instance.     
Alert Logic provides a payload template for an incident and an observation in JSON format using Mustache template-like transformations where a field in the JSON payload can be referenced by enclosing it in braces ({{}}. For example, the threatRating field in the following JSON {'incident': {'threat.Rating': "critical"}} is specified as {{incident.threatRating}}. A payload template converts the Alert Logic security information to the format expected by Microsoft Teams. You can add or remove lines in the sample template to meet your workflow requirements and security goals. If you want to create a Microsoft Teams connector for scheduled report notifications, you will need to configure the payload template.

For definitions of the Alert Logic variables in the templates and the full  JSON that you can use to configure your payload template in JQ or JSON format, see:

* [Incident Schema](incident.md)
* [Observation Schema](observation.md)
* [Scheduled Report Notification Schema](scheduled-report-notification-payload.md)

    For more information about Mustache, see the [Mustache Manual](https://mustache.github.io/mustache.5.html). For more complex transformations, you can use [JQ](https://stedolan.github.io/jq/#:~:text=jq). A helpful website for converting JSON to JQ is [jq play](https://jqplay.org/).    ### Incident payload template

JSON Template

| 1 | { |
| 2 | "@context": "https://schema.org/extensions", |
| 3 | "@type": "MessageCard", |
| 4 | "themeColor": "0072C6", |
| 5 | "title": "Alert Logic Incident Created", |
| 6 | "summary": "Incident Created Card", |
| 7 | "sections": [{ |
| 8 | "activityTitle": "{{incident.summary}}", |
| 9 | "activitySubtitle": "ID: {{humanFriendlyId}} | Customer: {{customer}} | Deployment: {{assets.al__deployment}}", |
| 10 | "facts": [{ |
| 11 | "name": "Threat Rating", |
| 12 | "value": "{{incident.threatRating}}" |
| 13 | }, { |
| 14 | "name": "Incident ID", |
| 15 | "value": "{{humanFriendlyId}}" |
| 16 | }, { |
| 17 | "name": "Escalated:", |
| 18 | "value": "{{incident.escalated}}" |
| 19 | }, { |
| 20 | "name": "Recommendations:", |
| 21 | "value": "{{incident.recommendations}}" |
| 22 | } |
| 23 | ], |
| 24 | "text": "{{incident.description}}" |
| 25 | }], |
| 26 | "potentialAction": [{ |
| 27 | "@type": "OpenUri", |
| 28 | "name": "See Incident in Alert Logic", |
| 29 | "targets": [{ |
| 30 | "os": "default", |
| 31 | "uri": "{{extra.incidentUrl}}" |
| 32 | }] |
| 33 | }] |
| 34 | } |

### Observation payload template

JSON Template

| 1 | { |
| 2 | "@context": "https://schema.org/extensions", |
| 3 | "@type": "MessageCard", |
| 4 | "themeColor": "0072C6", |
| 5 | "title": "Alert Logic Observation Created", |
| 6 | "summary": "Incident Created Card", |
| 7 | "sections": [{ |
| 8 | "activityTitle": "**Summary**: {{fields.summary}}", |
| 9 | "activitySubtitle": "**Customer:** {{id.account}} | **ID:** {{fields.id}}", |
| 10 | "facts": [{ |
| 11 | "name": "Severity:", |
| 12 | "value": "{{fields.severity}}" |
| 13 | }, { |
| 14 | "name": "Class:", |
| 15 | "value": "{{fields.class}}" |
| 16 | }, { |
| 17 | "name": "Subclass:", |
| 18 | "value": "{{fields.subclass}}" |
| 19 | }, { |
| 20 | "name": "Recommendations:", |
| 21 | "value": "{{fields.recommendations}}" |
| 22 | }, { |
| 23 | "name": "Message:", |
| 24 | "value": ">{{fields.keys.message}}", |
| 25 | "wrap": true |
| 26 | } |
| 27 | ], |
| 28 | "text": "**Description:** {{fields.desc}}" |
| 29 | }] |
| 30 | } |

## Create the Microsoft Teams webhook connector from the Alert Logic console

After you generate the target URL and optionally customize  the payload template, the next step is to create the webhook in the Alert Logic console  and test the payload.

**To create a Microsoft Teams webhook connector**:

1. In the Alert Logic console, click the navigation menu icon (![](../../Resources/Images/dashboard/menu-icon.png)), click ![](../../Resources/Images/dashboard/configure-icon.png)**Configure**, and then click **Connectors**.
2. On the Connectors page, click the add icon (![](../../Resources/Images/Icons/cdAddPlus.png)), and then click **Microsoft Teams**.
3. On the Create a Microsoft Teams Connector page, type a descriptive name for the webhook connector—for example, "Microsoft Teams Webhook Connector for Incidents."
4. In  **Target URL**, paste the URL that you copied earlier.
5. Choose the **Payload Type**, which is the type of Alert Logic security information that you want to send: **Incident**, **Observation** (of a log correlation), or **Scheduled Report Notification**.
6. Choose the format of the payload template you customized earlier: **JSON**  or **JQ**.
7. Enter the payload template that you customized.
      A red bar next to a line indicates a syntax error. Code with errors is underlined with a jagged red line. You can hover the pointer over the underlined code to view a tip about the error.      9. Click **TEST** to send a test webhook request to the target URL provided. For more information, see [Connector test results](#Connectortestresults).
10. If your webhook connector sent the test event to the target URL successfully, click **SAVE**.

### Connector test results

If you receive a message that the connector was successfully tested, Alert Logic sends the payload template you configured and populates a message in Microsoft Teams with sample data. Check Microsoft Teams to ensure the results are expected, and adjust the payload template if necessary.

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

You can view the list of connectors and edit or delete an existing one. For more information, see [Manage Connectors](manage-connectors.md).
