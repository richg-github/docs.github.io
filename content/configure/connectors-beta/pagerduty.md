# Configure PagerDuty Webhook Connector

You can configure a webhook connector in the Alert Logic console  to send [notifications](../notifications.md) to PagerDuty in near real time. When  you set up a notification and subscribe a webhook connector, the connector sends the event to the target URL you configured and creates a message in PagerDuty automatically.

Alert Logic notifications alert you to threats, changes, and scheduled events in your environment so you can respond quickly. From the Alert Logic console, you can subscribe your PagerDuty webhook to receive:

* [Incident notifications](../notifications/incident.md)        —Send a message when incidents occur that meet specific criteria, such as escalated incidents.
* [Log correlation notifications](../notifications/log-correlation.md)        —Send a message when your log correlation rules trigger an incident or observation.
* Exposure alerts
* [Scheduled report notifications](../notifications/report.md)        —Send a message when Alert Logic generates a scheduled report  that is available for download.
* Scheduled search results

Complete the following steps to successfully send messages to PagerDuty:

1. [Select or Create a Connection Target](#SelectorCreateaConnectionTarget)
2. [Customize the payload template](#Customizethesamplepayloadtemplate)
3. [Create the PagerDuty webhook connector from the Alert Logic console](#CreatethePagerDutywebhookconnectorfromtheAlertLogicconsole)
4. [Subscribe your webhook to receive notifications](#Subscribeyourwebhooktoreceivenotifications)

## Select or Create a Connection Target

Before creating a connector, you must first configure a connection target. Connection targets define common authentication path and credential references for external systems. For more information, see [Configure PagerDuty Connection Target](../../Z-Sandbox/bbaskin/connectors-beta/connection-targets/pagerduty.md).

To create a ticket in , you will use the default target URL provided in the Alert Logic console. Advanced API integration targeting can be done by modifying the target URL. See  documentation for advanced integration support.

Use the default Target URL.

## Customize the payload template

Decide which type of security information that you want Alert Logic to send to PagerDuty: Incident, Observation (of a log correlation), or a Scheduled Report Notification payload.

    If you want to send more than one payload type, you must configure a connector for each one. Because the payload is different, each payload type requires a separate connector instance.     
Alert Logic provides a payload template for an incident and an observation using JQ transformation. A payload template converts the Alert Logic security information to the format expected by PagerDuty. You can add or remove lines in the sample template to meet your workflow requirements and security goals. You must replace placeholder information in angle brackets with valid values. If you want to create a PagerDuty connector for scheduled report notifications, you will need to configure the payload template.

For definitions of the Alert Logic variables in the templates and the full  JSON that you can use to configure your payload template in JQ or JSON format, see:

* [Incident Schema](../connectors/incident.md)
* [Observation Schema](../connectors/observation.md)
* [Scheduled Report Notification Schema](../connectors/scheduled-report-notification-payload.md)

    To  generate the PagerDuty integration service routing key to replace the <ROUTING KEY> placeholder, see the [PagerDuty documentation](https://support.pagerduty.com/docs/services-and-integrations#section-events-api-v2). For more information about JQ, see [JQ](https://stedolan.github.io/jq/#:~:text=jq) . A helpful website for converting JSON to JQ is [jq play](https://jqplay.org/).    ### Incident payload template

JQ Template

| 1 | { |
| 2 | "routing_key": "<ROUTING KEY>", |
| 3 | "event_action": "trigger", |
| 4 | "dedup_key":  .dedup_hint, |
| 5 | "client": "Alert Logic", |
| 6 | "client_url": "https://console.account.alertlogic.com/", |
| 7 | "links": [{"href": .extra.incidentUrl, "text": "See Incident."}], |
| 8 | "payload": { |
| 9 | "summary": .incident.summary, |
| 10 | "severity": (if .incident.incident_threat_rating == "Critical" then "critical" elif .incident.incident_threat_rating == "High" then "critical" elif .incident.incident_threat_rating == "Medium" then "warning" else "info" end), |
| 11 | "group": "Security", |
| 12 | "class": "security incident", |
| 13 | "source": .victim.value, |
| 14 | "timestamp": .createtime_str |
| 15 | } |
| 16 | } |

### Observation payload template

JSON Template

| 1 | { |
| 2 | "routing_key": "<ROUTING KEY>", |
| 3 | "event_action": "trigger", |
| 4 | "dedup_key": .fields.id, |
| 5 | "client": "Alert Logic", |
| 6 | "client_url": "https://console.account.alertlogic.com/", |
| 7 | "payload": { |
| 8 | "summary": .fields.summary, |
| 9 | "severity": (if .fields.severity == "critical" then "critical" elif   .fields.severity == "high" then "critical" elif .fields.severity == "medium" then "warning" else "info" end), |
| 10 | "group": "Security", |
| 11 | "class": "security observation", |
| 12 | "source": .fields.path, |
| 13 | "timestamp": .fields.ts | todate, |
| 14 | "payload.custom_details": .fields.keys.message | fromjson |
| 15 | } |
| 16 | } |

## Create the PagerDuty webhook connector from the Alert Logic console

After you note your  instance name, generate the Authorization header, and optionally customize  the payload template, the next step is to create the webhook in the Alert Logic console  and test the payload.

**To create a  webhook connector**:

1. In the Alert Logic console, click the navigation menu icon (![](../../Resources/Images/dashboard/menu-icon.png)), click ![](../../Resources/Images/dashboard/configure-icon.png)**Configure**, and then click **Connectors**.
2. On the Connectors page, click the add icon (![](../../Resources/Images/Icons/cdAddPlus.png)), and then click ****.
3. On the Create a  Connector page, type a descriptive name for the webhook connector—for example, " Webhook Connector for Incidents."
4. Select or create a connection target.
5. In **Additional Header(s)**, leave the information as is. The field is prepopulated with the custom headers that  requires.
6. Choose the **Payload Type**, which is the type of Alert Logic security information that you want to send: **Incident**, **Observation** (of a log correlation), or **Scheduled Report Notification**.
7. Choose the format of the payload template you customized earlier: **JSON**  or **JQ**.
8. Choose an HTTP connector verb for the connector payload. If you are unsure, leave it as the default verb.
9. Enter the payload template that you customized.
      A red bar next to a line indicates a syntax error. Code with errors is underlined with a jagged red line. You can hover your pointer over the underlined code to view a tip about the error.       11. Click **TEST** to send a test webhook request to the  URL provided. For more information, see [Connector test results](#Connectortestresults).
12. If your webhook connector sent the test event to the  URL successfully, click **SAVE**.

### Connector test results

If you receive a message that the connector was successfully tested, Alert Logic sends the payload template you configured and populates a message in PagerDuty with sample data. Check PagerDuty to ensure the results are expected, and adjust the payload template if necessary.

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
