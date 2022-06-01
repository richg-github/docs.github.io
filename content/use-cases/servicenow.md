# ServiceNow

<p>
  <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> Integration with ServiceNow allows you to:</p>

<ul>
  <li>Generate a ServiceNow Incident when <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> detects a Security Incident or Security Observation</li>
  <li>Generate a ServiceNow Incident when <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> discovers new vulnerabilities.</li>
  <li>Generate a ServiceNow Incident in response to a scheduled search or report execution.</li>
  <li>Customize and enrich <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />-generated output sent to ServiceNow by adding custom fields or applying jq transformations (<a href="https://stedolan.github.io/jq/">https://stedolan.github.io/jq/</a>)</li>
</ul>## Supported subscription types

<ul>
  <li>
    <MadCap:variable name="SDKVariables.SIEMless" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />
    <MadCap:variable name="SDKVariables.Essentials" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />
  </li>
  <li>
    <MadCap:variable name="SDKVariables.SIEMless" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />
    <MadCap:variable name="SDKVariables.Professional" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />
  </li>
  <li>
    <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />
    <MadCap:variable name="SDKVariables.CloudDefender" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />
  </li>
</ul>
The types of notifications you can send to ServiceNow depend on your subscription type.

## Architecture diagram

![](../Resources/Images/SNOW Integration/Architecture diagram_1.png)<MadCap:snippetBlock src="../Resources/Snippets/expand-image.flsnp" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />### Overview

<ol>
  <li>When <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> generates an incident, observation, report, or other record, the <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> Notification Service is notified.</li>
  <li>When there are active subscriptions that match notification criteria and use Integration as a notification target, the Integrations Service is called to deliver a notification to a target integration.</li>
  <li>The Integration Service applies any JSON transformations configured for a target Integration connection (in this example, ServiceNow).</li>
  <li>Integration Service executes HTTP POST request against target integration.</li>
  <li>Response status of HTTP POST is recorded and is accessible via audit trails.</li>
</ol>## Deployment and Configuration

### Create a new integration for ServiceNow

<p style="font-weight: bold;">To create an integration:</p>

<p class="p_7">On the <b>Integrations</b> page, select <b>ServiceNow</b> under <b>Ticketing Webhooks</b>.</p>

![A screenshot of a cell phone

Description automatically generated](../Resources/Images/SNOW Integration/Deployment and Configuration.png)

<MadCap:snippetBlock src="../Resources/Snippets/expand-image.flsnp" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /><p class="p_7">Provide the following details:</p>

<ol start="1">
  <li>Name of the integration connection</li>
  <li>ServiceNow target URL</li>
  <li>
    <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> Data Type for which you plan to use this integration. Choose from Incident, Observation, Report, Scheduled Search, or Vulnerability.</li>
  <li>Provide the ServiceNow Authorization Header</li>
  <ol start="1">
    <li>
      <p>In your shell, type:</p>
      <pre>
        <code>
$: echo -n "IntegrationUserName:IntegrationUserPassword" | base64</code>
      </pre>
      <p>This will return base64 encoded credentials:</p>
      <pre>
        <code>
SW50ZWdyYXRpb25Vc2VyTmFtZTpJbnRlZ3JhdGlvblVzZXJQYXNzd29yZA==</code>
      </pre>
    </li>
    <li>
      <p>Enter the following in the Authorization Header field:</p>
      <pre>
        <code>
Basic: SW50ZWdyYXRpb25Vc2VyTmFtZTpJbnRlZ3JhdGlvblVzZXJQYXNzd29yZA==</code>
      </pre>
    </li>
  </ol>
  <li>
    <p>
      <b>Payload</b> is populated with recommended settings, but you can customize it by providing extra JSON fields that are either static or reference Data Type schema. Click on ‘View Sample Data’ to see Data Type schema.</p>
    <img src="../Resources/Images/SNOW Integration/Deployment and Configuration_1.png" alt="" class="body" />
    <MadCap:snippetBlock src="../Resources/Snippets/expand-image.flsnp" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />
  </li>
  <li>
    <p>Optionally, you can also provide JQ transformation for the Data Type JSON.</p>
    <img src="../Resources/Images/SNOW Integration/Deployment and Configuration_2.png" alt="" class="body" />
    <MadCap:snippetBlock src="../Resources/Snippets/expand-image.flsnp" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />
  </li>
  <li>Click <b>Test</b> to test connection using Sample Payload</li>
  <li>Click <b>Save</b> to save the ServiceNow integration setup.</li>
</ol>### Create Notification 

You can create an Incident notification. Other notifications work similarly.

**To create a notification**:

1. Select the **Notifications** menu option under **Manage**.
2. Click  the add icon (![](../Resources/Images/Icons/cdAddPlus.png)) and select **Incidents**.
3. Provide Name and filter options for this notification.
4. In the **Recipients** section, select the **Subscribe Integration** option.
5. In the **Notification Delivery** section, select the ServiceNow integration you created.
6. Click **Save**.

For more information about notifications, see [Configure Notifications](https://docs.alertlogic.com/configure/notifications.htm).

## Best Practices

<ol>
  <li class="ListParagraph_3">Incidents—<MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> recommends you toggle <b>Escalations</b> on and only create tickets for high and critical incidents to start with. You can always add lower severity incidents later. If you do not toggle escalations on, you will receive incidents when they are created automatically and not after the SOC team analysizes it.</li>
  <li class="ListParagraph_3">Vulnerabilities—Select to group by remediations and leveraging asset groups.</li>
</ol>## Validation and Troubleshooting

<p>If the provided credentials are no longer valid, <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> creates a remediation.</p>
