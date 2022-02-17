# Configure a Send Incident to Microsoft Teams Task (Beta)

In your automated response playbook, you can configure a Send Incident to Microsoft Teams task to send Alert Logic incident details to Teams via a connector[connector](../../../configure/connectors-beta/connectors.md).

The source of the incident  can be any of the following:

* Incident that meets the conditions of a trigger for the playbook. For more information, see [link to topic about playbook triggers].
* Incident that a user selects to run the playbook on manually. For more information, see [link to topic about running a playbook on an incident].
* Sample incident payload used to test the playbook. For more information, see [link to topic about playbook testing].

Complete the following steps to successfully configure the Send Incident to Microsoft Teams task:

1. [Create a Microsoft Teams connector](#CreateaMicrosoftTeamsconnector)
2. [Add the task to your playbook](#Addthetasktoyourplaybook)
3. [Configure the task input](#Configurethetaskinput)
4. [Configure the task output (optional)](#Configurethetaskoutputoptional)

## Create a Microsoft Teams connector

The Send Incident to Microsoft Teams task requires a Microsoft Teams connector  with the following configuration:

* **Connection Target**—Microsoft Teams connection target for the channel to which you want to send the incident details
* **Payload Type**—Incident
* **Payload Template Format**—JSON
* **Payload Template**—Edited to include the details that you want to send to Teams, if you want to change the message content

To check for an existing connector that meets these requirements,  in the Alert Logic console, click ![](../../../Resources/Images/dashboard/configure-icon.png)**Configure** in the navigation menu (![](../../../Resources/Images/dashboard/menu-icon.png)), and then click **Connectors**. If any Teams connectors appear in the list, review the configuration.

If you do not have a Teams connector with the specified configuration already, complete the instructions in [Configure Microsoft Teams Webhook Connector](../../../configure/connectors-beta/teams.md), and refer to the requirements as you set it up.

## Add the task to your playbook

If you have not added the  task to your playbook, complete the instructions in [Add a task in the workflow diagram](../add-task.md#Addataskintheworkflowdiagram) and [Add task details (optional)](../add-task.md#Addtaskdetailsoptional).

## Configure the task input

Complete these instructions to provide the input values for your Send Incident to Microsoft Teams task.

**To configure the task input:**

1. On the task **Input** tab, select the connector in **Microsoft Teams Connector** that you created or identified in [Create a Microsoft Teams connector](#CreateaMicrosoftTeamsconnector).
2. In **Incident Payload**, leave the YAQL expression to reference the incident payload that the playbook is running on: 
`<% ctx().payload %>`

The selected Teams connector controls the incident details that the playbook sends.

### Insert a YAQL expression in an input field

Any field that supports one or more [Yet Another Query Language](https://yaql.readthedocs.io/en/latest/) (YAQL) expressions has a **SELECT VARIABLE** drop-down list above the field. A YAQL expression can  reference a value in the playbook context, such as a field in the incident payload, or the published result of a previous task.

To insert a YAQL expression, place your cursor in the field where you want to insert the reference, click **SELECT VARIABLE**, and then select the variable. A YAQL expression that references the selected value appears in the field.

## Configure the task output (optional)

This task does not generate results that you can publish as output. For other ways to publish output, see [Configure task output (optional)](../add-task.md#Configuretaskoutputoptional).

## Technical reference

[Ideally this paragraph would state why the following information is useful, what to do with it...]

### Action Name

Send Incident to Microsoft Teams

### Action Type

connectors_send_notification_msteams

### Permissions

[Include this section if needed. Example:  Azure permissions.]

### Limitations

The Teams channel cannot be configured in this task. The channel that the task uses is the one configured in the connection target.
