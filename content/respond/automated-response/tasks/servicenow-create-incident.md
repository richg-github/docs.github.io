# Configure a Create ServiceNow Incident Task (Draft)

In your automated response playbook, you can configure a Create ServiceNow Incident task to create a ServiceNow incident from an Alert Logic incident sent via a [connector](../../../configure/connectors-beta/connectors.md).

The source of the incident  can be any of the following:

* Incident that meets the conditions of a trigger for the playbook. For more information, see [link to topic about playbook triggers].
* Incident that a user selects to run the playbook on manually. For more information, see [link to topic about running a playbook on an incident].
* Sample incident payload used to test the playbook. For more information, see [link to topic about playbook testing].

Complete the following steps to successfully configure the Create ServiceNow Incident task:

1. [Create a ServiceNow connector](#CreateaServiceNowconnector)
2. [Add the task to your playbook](#Addthetasktoyourplaybook)
3. [Configure the task input](#Configurethetaskinput)
4. [Configure the task output (optional)](#Configurethetaskoutputoptional)

## Create a ServiceNow connector

The Create ServiceNow Incident task requires a ServiceNow connector  with the following configuration:

* **Connection Target**—ServiceNow connection target for the ServiceNow instance to which you want to send the incident details
* **Payload Type**—Incident
* **Payload Template Format**—JSON
* **Payload Template**—Edited to include the details that you want to send to ServiceNow, if you want to change the incident content

To check for an existing connector that meets these requirements,  in the Alert Logic console, click ![](../../../Resources/Images/dashboard/configure-icon.png)**Configure** in the navigation menu (![](../../../Resources/Images/dashboard/menu-icon.png)), and then click **Connectors**. If any ServiceNow connectors appear in the list, review the configuration.

If you do not have a ServiceNow connector with the specified configuration already, complete the instructions in [Configure ServiceNow Webhook Connector](../../../configure/connectors-beta/servicenow.md), and refer to the requirements as you set it up.

## Add the task to your playbook

If you have not added the  task to your playbook, complete the instructions in [Add a task in the workflow diagram](../add-task.md#Addataskintheworkflowdiagram) and [Add task details (optional)](../add-task.md#Addtaskdetailsoptional).

## Configure the task input

Complete these instructions to provide the input values for your Create ServiceNow Incident task.

**To configure the task input:**

1. On the task **Input** tab, select the connector in **ServiceNow Connector** that you created or identified in [Create a ServiceNow connector](#CreateaServiceNowconnector).
2. In **Incident Payload**, leave the YAQL expression to reference the incident payload that the playbook is running on: 
`<% ctx().payload %>`

The selected ServiceNow connector controls the incident details that the playbook sends.

### Insert a YAQL expression in an input field

Any field that supports one or more [Yet Another Query Language](https://yaql.readthedocs.io/en/latest/) (YAQL) expressions has a **SELECT VARIABLE** drop-down list above the field. A YAQL expression can  reference a value in the playbook context, such as a field in the incident payload, or the published result of a previous task.

To insert a YAQL expression, place your cursor in the field where you want to insert the reference, click **SELECT VARIABLE**, and then select the variable. A YAQL expression that references the selected value appears in the field.

## Configure the task output (optional)

This task generates the following results when it completes. You can publish a current task result or other values by adding them as output. Published output  is available for reference in later playbook tasks. For instructions, see [Configure task output (optional)](../add-task.md#Configuretaskoutputoptional).

* **snow_id** (*string*)—ServiceNow id of incident
   * *Suggested rewrite:* ServiceNow incident number

## Technical reference

[Ideally this paragraph would state why the following information is useful, what to do with it...]

### Action Name

Create ServiceNow Incident

### Action Type

connectors_send_notification_snow

### Permissions

[Include this section if needed. Example: Azure permissions.]

### Limitations

[Include this section if needed. Example: This action only works in AWS regions supported by Alert Logic.]
