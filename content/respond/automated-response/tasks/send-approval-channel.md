# Configure a Send Approval Request via Connection Target Task (Draft)

In your automated response playbook, you can configure a Send Approval Request via Connection Target task to send an approval request to third-party applications for which you have a [connection target](../../../configure/connectors-beta/connection-targets/connection-target.md)  configured.

[Need  a typical use case to go here, maybe one that involves incidents]

The source of the incident  can be any of the following:

* Incident that meets the conditions of a trigger for the playbook. For more information, see [link to topic about playbook triggers].
* Incident that a user selects to run the playbook on manually. For more information, see [link to topic about running a playbook on an incident].
* Sample incident payload used to test the playbook. For more information, see [link to topic about playbook testing].

Complete the following steps to successfully configure the Send Approval Request via Connection Target task:

1. [Create a  connection target for the third-party application](#Createaconnectiontargetforthethirdpartyapplication)
2. [Add the task to your playbook](#Addthetasktoyourplaybook)
3. [Configure the task input](#Configurethetaskinput)
4. [Configure the task output (optional)](#Configurethetaskoutputoptional)

## Create a  connection target for the third-party application

The Send Approval Request via Connection Target task requires a  connection target for the third-party application that you want to receive the requests.

To check whether it exists,  in the Alert Logic console, click ![](../../../Resources/Images/dashboard/configure-icon.png)**Configure** in the navigation menu (![](../../../Resources/Images/dashboard/menu-icon.png)),  click **Connectors**, and then click the **Connection Targets** tab.

If you do not have the connection target already, follow the relevant instructions in [Connection Targets Configuration Guide (Beta)](../../../configure/connectors-beta/connection-targets/connection-target.md)   to set it up.

## Add the task to your playbook

If you have not added the  task to your playbook, complete the instructions in [Add a task in the workflow diagram](../add-task.md#Addataskintheworkflowdiagram) and [Add task details (optional)](../add-task.md#Addtaskdetailsoptional).

## Configure the task input

Complete these instructions to provide the input values for your Send Approval Request via Connection Target task.

**To configure the task input:**

1. On the task **Input** tab, select one or more Connection Targets. You can use the search bar to help you find names and email addresses.
2. In **Message Subject**, edit the subject for the approval message, or use the one provided.
3. In **Message**, edit the approval message, or use the one provided.
4. In **Approval Expiration in Minutes**, enter a wait time before automatic task failure in minutes, or keep the default value: 60. The minimum  is 60.

### Insert a YAQL expression in an input field

Any field that supports one or more [Yet Another Query Language](https://yaql.readthedocs.io/en/latest/) (YAQL) expressions has a **SELECT VARIABLE** drop-down list above the field. A YAQL expression can  reference a value in the playbook context, such as a field in the incident payload, or the published result of a previous task.

To insert a YAQL expression, place your cursor in the field where you want to insert the reference, click **SELECT VARIABLE**, and then select the variable. A YAQL expression that references the selected value appears in the field.

## Configure the task output (optional)

This task generates the following results when it completes. You can publish a current task result or other values by adding them as output. Published output  is available for reference in later playbook tasks. For instructions, see [Configure task output (optional)](../add-task.md#Configuretaskoutputoptional).

* **response** (*string*)—Accepted or Rejected message
   * *Suggested rewrite:* Response to the request (values: approved, rejected)

## Technical reference

[Ideally this paragraph would state why the following information is useful, what to do with it...]

### Action Name

Send Approval Request via Connection Target

### Action Type

send_approval_channels

### Permissions

[Include this section if needed. Example:  Azure permissions.]

### Limitations

[Include this section if needed. Example: This action only works in AWS regions supported by Alert Logic.]
