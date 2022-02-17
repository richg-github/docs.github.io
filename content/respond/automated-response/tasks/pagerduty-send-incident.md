# Configure a Send Incident to PagerDuty Task (Draft)

In your automated response playbook, you can configure a Send Incident to PagerDuty task to send Alert Logic incident details to PagerDuty via a [connector](../../../configure/connectors-beta/connectors.md).

The source of the incident  can be any of the following:

* Incident that meets the conditions of a trigger for the playbook. For more information, see [link to topic about playbook triggers].
* Incident that a user selects to run the playbook on manually. For more information, see [link to topic about running a playbook on an incident].
* Sample incident payload used to test the playbook. For more information, see [link to topic about playbook testing].

Complete the following steps to successfully configure the Send Incident to PagerDuty task:

1. [Create a PagerDuty connector](#CreateaPagerDutyconnector)
2. [Add the task to your playbook](#Addthetasktoyourplaybook)
3. [Configure the task input](#Configurethetaskinput)
4. [Configure the task output (optional)](#Configurethetaskoutputoptional)

## Create a PagerDuty connector

The Send Incident to PagerDuty task requires a PagerDuty connector  with the following configuration:

* **Connection Target**—PagerDuty connection target for the channel to which you want to send the incident details
* **Payload Type**—Incident
* **Payload Template Format**—JSON
* **Payload Template**—Edited to include the details that you want to send to PagerDuty, if you want to change the message content

To check for an existing connector that meets these requirements,  in the Alert Logic console, click ![](../../../Resources/Images/dashboard/configure-icon.png)**Configure** in the navigation menu (![](../../../Resources/Images/dashboard/menu-icon.png)), and then click **Connectors**. If any PagerDuty connectors appear in the list, review the configuration.

If you do not have a PagerDuty connector with the specified configuration already, complete the instructions in [Configure PagerDuty Webhook Connector](../../../configure/connectors-beta/pagerduty.md), and refer to the requirements as you set it up.

## Add the task to your playbook

If you have not added the  task to your playbook, complete the instructions in [Add a task in the workflow diagram](../add-task.md#Addataskintheworkflowdiagram) and [Add task details (optional)](../add-task.md#Addtaskdetailsoptional).

## Configure the task input

Complete these instructions to provide the input values for your Send Incident to PagerDuty task.

**To configure the task input:**

1. On the task **Input** tab, select the connector in **PagerDuty Connector** that you created or identified in [Create a PagerDuty connector](#CreateaPagerDutyconnector).
2. In **Incident Payload**, leave the YAQL expression to reference the incident payload that the playbook is running on: 
`<% ctx().payload %>`

The selected PagerDuty connector controls the incident details that the playbook sends.

### Insert a YAQL expression in an input field

Any field that supports one or more [Yet Another Query Language](https://yaql.readthedocs.io/en/latest/) (YAQL) expressions has a **SELECT VARIABLE** drop-down list above the field. A YAQL expression can  reference a value in the playbook context, such as a field in the incident payload, or the published result of a previous task.

To insert a YAQL expression, place your cursor in the field where you want to insert the reference, click **SELECT VARIABLE**, and then select the variable. A YAQL expression that references the selected value appears in the field.

## Configure the task output (optional)

This task does not generate results that you can publish as output. For other ways to publish output, see [Configure task output (optional)](../add-task.md#Configuretaskoutputoptional).

## Technical reference

[Ideally this paragraph would state why the following information is useful, what to do with it...]

### Action Name

Send Incident to PagerDuty

### Action Type

connectors_send_notification_pagerduty

### Permissions

[Include this section if needed. Example:  Azure permissions.]

### Limitations

[Include this section if needed. Example: This action only works in AWS regions supported by Alert Logic.]
