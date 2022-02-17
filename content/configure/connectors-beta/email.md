# Configure a Universal Email Connector

You can configure a universal email connector in the Alert Logic console  to send [incident notifications](../notifications/incident.md) to  any public-facing web server configured to accept email requests. Email connectors allow you to send notifications about threats or changes in your environment directly to a third-party application in near real time so you can respond quickly.

When  you set up a notification and subscribe an email connector, the connector sends the event to the target email you configured and can generate a message or IT service management (ITSM) ticket for the incident automatically.

For example, you can configure an email connector for an ITSM such as ServiceNow or Jira Service Desk and subscribe it to receive notifications. When an incident occurs that meets the notification criteria, Alert Logic sends the incident notification to the configured email address, and the third-party application generates a service ticket. The email subject configured in the Alert Logic connector becomes the ticket summary. The body of the Alert Logic email notification becomes the ticket description. The description includes a link to the [incident](../../analyze/incidents.md) in the Alert Logic console.

Complete the following steps to successfully receive Alert Logic notifications or generate service tickets  in your application:

1. [Set up the third-party application](#Setupthethirdpartyapplication)
2. [Create the email connector from the Alert Logic console](#Createtheemailconnectorfromthe)
3. [Subscribe your email connector to receive notifications](#Subscribeyouremailconnectortoreceivenotifications)

## Set up the third-party application

Before you create the email connector in the Alert Logic console, you must find or configure the target email address in the third-party application that can accept Alert Logic notifications or ticket creation requests. The target email address must belong to a registered user or account in the application to which you want to connect. Note the email address because you need it to configure your connector. This table lists common examples:

| Application | Email Address  | Notes |
|---|---|---|
| Jira Service Desk | *myjiraproject*@*myjira.atlassian.net* | Replace *myjiraproject* with the name of the specific Jira Service Desk project you want to connect to and *myjira.atlassian.net* with your cloud instance URL. |
| Jira Software | *myjiraproject*@*myjira.atlassian.net* | Replace *myjiraproject* with the name of the specific Jira project you want to connect to and *myjira.atlassian.net* with your cloud instance URL. |
| ServiceNow | *myinstance*@service-now.com | Replace *myinstance* with the name specified in your cloud instance URL. |

You may also want to set up how you want Alert Logic incident notifications to be processed in the external application. In Jira Service Desk, for example, you can create a specific request type for Alert Logic security incidents. You can also configure the Jira Service Desk fields that you want to include in that request type and assign them to  fields in the Alert Logic [incident payload](../connectors/incident.md).  A good practice is to configure a custom request type instead of using a generic type such as "Report a system problem" because it allows you to restrict access for security incidents.

See the documentation for the third-party application for more information about the target email address and configuration options.

## Create the email connector from the Alert Logic console

After you identify the target email address for the third-party application to which you want to connect, you can create and test the email connector from the Connectors page in the Alert Logic console.

**To create an email connector:**

1. Click the navigation menu icon (![](../../Resources/Images/dashboard/menu-icon.png)), click ![](../../Resources/Images/dashboard/configure-icon.png)**Configure**, and then click **Connectors**.
2. On the Connectors page, click the add icon (![](../../Resources/Images/Icons/cdAddPlus.png)), and then click **Email**.
3. On the Create an Email Connector page, type a descriptive name for the email connector—for example, "Jira Email Connector for Incidents."
4. Enter the email address for the third-party application that you noted previously.
5. (Optional) Customize the **Email Subject**. You can change the text and insert [variables](#Emailsubjectvariables) enclosed with double braces ({{*variable*}}).
6. Click **TEST** to send a test email to the target email address provided. For more information, see [Connector test results](#Connectortestresults).
7. If your email connector sent the test event to the target email successfully, click **SAVE**.

### Email subject variables

To customize the subject line of the email that you send to the third-party application, you can add these variables to the Email Subject field.

     For an example of the full incident JSON payload that Alert Logic sends for email connectors, see [Incident Schema](../connectors/incident.md). You can add any of the fields listed to the email subject, but some values are lengthier and not recommended.    <table>
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
      <td>Name of <a href="../notifications/log-correlation.md">correlation</a> that triggered the incident</td>
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
</table>### Connector test results

The test email that Alert Logic sends has the subject "Alert Logic Incident Report" and confirms the configuration was successful.

    After you subscribe your connector to receive [incident notifications](../notifications/incident.md), the notification emails use the email subject you configured.    
If the test is unsuccessful, Alert Logic displays an error message. For server response errors, you can use the error code and message that Alert Logic passes through to troubleshoot the issue.

### Information sent to your application

The email subject configured in the Alert Logic connector becomes the ticket title or message subject. The email body  uses the following information from the incident payload, transformed from Markdown to HTML. If any of the fields are empty, lines are empty in the resulting email.

| Field | Description | Example |
|---|---|---|
| incident.summary | Brief description of the incident that is suitable as a  title or message subject | Brute force attempt from 1.2.3.4 |
| incident.description | Incident explanation from the incident investigation report, if any | "<p><strong>Attack Detail</strong>:<br />\n<strong>Attacker:</strong> 172.31.37.117, local_ip<br />\n<strong>Targets:</strong> 122.99.34.111, 172.31.37.90,  and 172.31.39.79  </p>\n<p>We have detected a recon attack targeting a number of common server vulnerabilities. This is a vulnerability scan however we are unable to determine the specific tool or company performing this attack.</p>" |
| incident.recommendations | Recommendations from the incident investigation report, if any | "<p>A compromised host should be isolated from the network and cleaned. You will want to remove the back doors installed and check the system logs for other actions taken. Once a system is compromised, usually one of the first things done by an attacker is creating a secondary access channel. Assume that additional modifications have been made to the system beyond the initial breach.</p>" |
| incident.extra.incidentUrl | Links to the [incident](../../analyze/incidents.md) in the Alert Logic console | https://console.incidents.product.dev.alertlogic.com/#/incidents/*incidentId*/investigation |

## Subscribe your email connector to receive notifications

After you create and test your email connector, the next step in the Alert Logic console is to set up your incident notifications to subscribe to the connector. For instructions, see [Incident Notifications](../notifications/incident.md).

## Manage your email connectors

You can view the list of email connectors and edit or delete an existing one. For more information, see [Manage Connectors](../connectors/manage-connectors.md).
