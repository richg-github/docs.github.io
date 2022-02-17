# Configure a Universal Webhook Connector

You can configure a universal webhook connector in the Alert Logic console  to send [notifications](../notifications.md) to  any public-facing  HTTP endpoint. Connectors  allow you to send data directly to a third-party application in near real time. When  you set up a notification and subscribe a webhook connector, the connector sends the event to the target URL you configured and can generate a message or service ticket  automatically.

Alert Logic notifications alert you to threats, changes, and scheduled events in your environment so you can respond quickly. From the Alert Logic console, you can subscribe a webhook to receive:

* [Incident notifications](../notifications/incident.md)        —Send an alert or generate a service ticket when incidents occur that meet specific criteria, such as escalated incidents.
* [Log correlation notifications](../notifications/log-correlation.md)        —Send an alert or generate a service ticket when your log correlation rules trigger an incident or observation.
* Exposure alerts
* [Scheduled report notifications](../notifications/report.md)        —Send a notification or generate as service ticket when Alert Logic generates a scheduled report  that is available for download.
* Scheduled search results

Complete the following steps to successfully receive Alert Logic notifications or generate service tickets  in your application:

1. [Set up the third-party application](#Setupthethird-partyapplication)
2. [Create the universal webhook connector from the Alert Logic console](#Createtheuniversalwebhookconnector)
3. [Subscribe your webhook to receive notifications ](#Subscribeyourwebhooktoreceivenotifications)

    Alert Logic provides several fully supported webhoook connectors for commonly used messaging and ticketing systems. Customers are responsible for correctly configuring a universal webhook to connect to other applications. To assist your experienced DevOps professional with troubleshooting, Alert Logic passes through all error messages sent by the target application.    ## Set up the third-party application

Before you create the webhook connector in the Alert Logic console, gather the information that your third-party application requires by consulting the vendor documentation. Webhooks for third-party applications require some or all of the following information:

**Target URL**—Note the URL for your application that can accept Alert Logic notifications or ticket creation requests. Some applications require that you generate a target URL that includes a token for authorization.

**Custom headers**—Some applications require one or more HTTP custom headers. Custom headers are name-value pairs in the format *Header-Name*: *value* with each header field on a separate line, for example:

| Accept: application/json |
| Content-Type: application/json |

**Authorization header**—Some applications require an HTTP Authorization request header. If your system requires a Basic Authorization header (user name and password encoded with base64), you can complete the instructions in [Generate an Authorization header](#Generateauthorizationheader) to specify the header. Alert Logic stores your Authorization header securely when you save the connector.

**Payload type**—Decide which type of security information that you want Alert Logic to send to your application: Incident, Observation (of a log correlation), or a Scheduled Report notification. If you want to send more than one payload type, configure a connector for each one. Separate connectors are required because each payload is different.

**Payload template**—Alert Logic provides payload templates for an incident and an observation in JSON format. A payload template converts the Alert Logic security information to the representation expected by your third-party application. You must customize  the payload template to meet the requirements of your  application and your security goals.

### Generate an Authorization header

If the third-party application to which you want to connect requires a Basic HTTP Authorization request header, you can use these instructions to generate the header. The command requires the valid user name and password in the application to which you want to connect, and it encodes the credentials with base64.

In the Authorization Header field, you enter the word "Basic" (which is the Authorization header type), a space, and then the  base64-encoded credentials.

**To generate the header on Linux and Mac OS X:**

1. In the command line, type the following command, including the single quotation marks:
<kbd>echo -n '&amp;lt;user_name&amp;gt;:&amp;lt;password&amp;gt;' | base64</kbd>
where you must replace <user_name> and <password> with a valid user name and password for the third-party application.
2. Copy the following string, which you must enter in the **Authorization Header** field when you create the connector:
<kbd>Basic &amp;lt;resulting_base64_encoded_string&amp;gt;</kbd>

If the user name is "admin" and the password is "testpassword" for example, the command is:

<kbd>echo -n 'admin:testpassword' | base64</kbd>

and the command produces this output: 

<kbd>YWRtaW46dGVzdHBhc3N3b3Jk</kbd>

So, in the **Authorization Header** field, you would paste:

<kbd>Basic YWRtaW46dGVzdHBhc3N3b3Jk</kbd>

**To generate the header in Windows PowerShell:**

1. In the command line, type the following commands, including the quotation marks:
PS c:\Temp><kbd>$auth  = [System.Text.Encoding]::UTF8.GetBytes("&amp;lt;user_name&amp;gt;:&amp;lt;password&amp;gt;")</kbd>
where you must replace <user_name> and <password> with a valid user name and password for your third-party application.
PS c:\Temp><kbd>[System.Convert]::ToBase64String($auth)</kbd>
2. Copy the following string, which you must enter in the **Authorization Header** field when you create the connector:
<kbd>Basic &amp;lt;resulting_base64_encoded_string&amp;gt;</kbd>

If the user name is "admin" and the password is "testpassword" for example, the commands are:

PS C:\Temp><kbd>$auth  = [System.Text.Encoding]::UTF8.GetBytes("admin:testpassword")</kbd>

PS C:\Temp><kbd>[System.Convert]::ToBase64String($auth)</kbd>

and the command produces this output: 

<kbd>YWRtaW46dGVzdHBhc3N3b3Jk</kbd>

So, in the **Authorization Header** field, you would paste:

<kbd>Basic YWRtaW46dGVzdHBhc3N3b3Jk</kbd>

### Customize the sample payload template

Alert Logic provides sample Incident and Observation payload templates  to help you get started in JSON format using Mustache template-like transformations where a field in the JSON payload can be referenced by enclosing it in braces ({{}}. For example, the threatRating field in the following JSON {'incident': {'threat.Rating': "critical"}} is specified as {{incident.threatRating}}. You must replace the attributes with the appropriate ones for your system. You can also add or remove lines. For definitions of the Alert Logic variables in the samples and the full  JSON that you can use to configure your payload template, see:

* [Incident Schema](incident.md)
* [Observation Schema](observation.md)
* [Scheduled Report Notification Schema](scheduled-report-notification-payload.md)

    For more information about Mustache, see the [Mustache Manual](https://mustache.github.io/mustache.5.html). For more complex transformations, you can use [JQ](https://stedolan.github.io/jq/#:~:text=jq). A helpful website for converting JSON to JQ is [jq play](https://jqplay.org/).    #### Sample Incident payload template

JSON Template

| 1 | { |
| 2 | "account_id": "{{accountId}}", |
| 3 | "customer_name": "{{customer}}", |
| 4 | "deployment_name": "{{assets.al__deployment}}", |
| 5 | "short_incident_id": "{{humanFriendlyId}}", |
| 6 | "long_incident_id": "{{incidentId}}", |
| 7 | "summary": "{{summary}}", |
| 8 | "description": "{{incident.description}}", |
| 9 | "recommendations": "{{incident.recommendations}}", |
| 10 | "attacker": "{{attacker.value}}", |
| 11 | "victim": "{{victim.value}}", |
| 12 | "timestamp": "{{createtime_str}}", |
| 13 | "threat_rating": "{{incident_threat_rating}}", |
| 14 | "incident_class": "{{incident_class}}", |
| 15 | "status": "{{customer_status.status}}" |
| 16 | } |

#### Sample Observation payload template

JSON Template

| 1 | { |
| 2 | "account_id": "{{id.account}}", |
| 3 | "summary": "{{fields.summary}}", |
| 4 | "description": "{{fields.desc}}", |
| 5 | "severity": "{{fields.severity}}", |
| 6 | "class": "{{fields.class}}", |
| 7 | "subclass": "{{fields.subclass}}", |
| 8 | "recommendations": "{{fields.recommendations}}", |
| 9 | "message": "{{fields.keys.message}}" |
| 10 | } |

## Create the universal webhook connector from the Alert Logic console

After you gather the information required by your third-party application and configure the payload template, the next step is to create a universal webhook in the Alert Logic console  and test the payload.

If your application does not require information such as the custom headers or Authorization header, leave the field blank.

**To add a universal webhook connector**:

1. In the Alert Logic console, click the navigation menu icon (![](../../Resources/Images/dashboard/menu-icon.png)), click ![](../../Resources/Images/dashboard/configure-icon.png)**Configure**, and then click **Connectors**.
2. On the Connectors page, click the add icon (![](../../Resources/Images/Icons/cdAddPlus.png)), and then click **Webhook**.
3. On the Create a Webhook Connector page, type a descriptive name for the webhook connector—for example, "*My Third-Party Application* Webhook Connector for Incidents."
4. Enter the target URL that you noted previously.
5. If your application requires one or more custom headers, enter each header that you noted previously on a separate line.
6. If your application requires an HTTP Authorization request header, paste it in the **Authorization Header** field.
7. Choose a **Payload Type**, which is the type of Alert Logic security information that you want to send: **Incident**, **Observation** (of a log correlation), **Scheduled Report Notification**.
8. Choose the format of the payload template you customized: **JSON**  or **JQ**.
9. Enter the payload template that you customized.
      A red bar next to a line indicates a syntax error. Code with errors is underlined with a jagged red line. You can hover the pointer over the underlined code to view a tip about the error.      11. Click **TEST** to send a test webhook request to the target URL provided. For more information, see [Connector test results](#Connectortestresults).
12. If your webhook connector sent the test event to the target URL successfully, click **SAVE**.

### Connector test results

If you receive a message that the connector was successfully tested, Alert Logic sends the payload template you configured and populates the notification or ticket with sample data. Check your third-party application to ensure the results are expected, and adjust the payload template if necessary.

If the test is unsuccessful, Alert Logic displays an error message. For server response errors, you can use the error code and message that Alert Logic passes through to troubleshoot the issue. Alert Logic also informs you if your JSON or JQ payload template contains syntax errors.

## Subscribe your webhook to receive notifications

After you test and save the connector configuration, the last step is to set up your notification criteria and subscribe the webhook.

You can set up and manage a notification of any type directly from the Notifications page. For more information, see [Manage Notifications](../notifications/manage.md). You can create notifications from other pages according to notification type:

* For incidents, you can also create a notification from the Incidents page. For more information, see [Incident Notifications](../notifications/incident.md).
* For observations, you can also create a notification   from the Search page (Log Search tab or Correlations tab) during the process of creating the correlation or by editing an existing correlation listed on the Correlations tab. For more information, see [Correlations and Notifications](../notifications/log-correlation.md) and [Observation Notifications](../notifications/observation.md).
* For health exposures, you can also create a notification from the Health page. For more information, see [Health](../../analyze/health.md).
* For scheduled reports, you can also schedule the report and subscribe notification recipients from the Reports page. For more information, see [Scheduled Reports and Notifications](../notifications/report.md).
* For scheduled File Integrity Monitoring (FIM) searches, you can schedule a search and subscribe notification recipients from the Notifications page. For more information, see [File Integrity Monitoring Search Notification](../notifications/fim-search.md).

## Manage your webhook connectors

You can view the list of webhook connectors and edit or delete an existing one. For more information, see [Manage Connectors](manage-connectors.md).
