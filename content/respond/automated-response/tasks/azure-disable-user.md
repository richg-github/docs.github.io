# Configure a Disable Azure AD User  Task (Beta)

In your automated response playbook, you can configure a Disable Azure AD User task to disable a  user in Azure Active Directory (AD).

A typical use case is to disable an Office 365 user that is the victim of an incident.

The source of the incident  can be any of the following:

* Incident that meets the conditions of a trigger for the playbook. For more information, see [link to topic about playbook triggers].
* Incident that a user selects to run the playbook on manually. For more information, see [link to topic about running a playbook on an incident].
* Sample incident payload used to test the playbook. For more information, see [link to topic about playbook testing].

Complete the following steps to successfully configure the Disable Azure AD User task:

1. [Create a connection target for Microsoft Azure](#CreateaconnectiontargetforMicrosoftAzure)
2. [Add the task to your playbook](#Addthetasktoyourplaybook)
3. [Configure the task input](#Configurethetaskinput)
4. [Configure the task output (optional)](#Configurethetaskoutputoptional)

## Create a connection target for Microsoft Azure

The Disable Azure AD User  task requires a Microsoft Azure  connection target  that grants Alert Logic access to manage users in Azure AD.

To check whether it exists,  in the Alert Logic console, click ![](../../../Resources/Images/dashboard/configure-icon.png)**Configure** in the navigation menu (![](../../../Resources/Images/dashboard/menu-icon.png)),  click **Connectors**, and then click the **Connection Targets** tab.

If any Microsoft Azure connection targets appear in the list, review their configurations to determine whether the one you need already exists.

If you do not have a connection target for Microsoft Azure already, complete the instructions in [Configure Microsoft Azure Connection Target (Beta)](../../../configure/connectors-beta/connection-targets/azure.md).

## Add the task to your playbook

If you have not added the  task to your playbook, complete the instructions in [Add a task in the workflow diagram](../add-task.md#Addataskintheworkflowdiagram) and [Add task details (optional)](../add-task.md#Addtaskdetailsoptional).

## Configure the task input

Complete these instructions to provide the input values for your  Disable Azure AD User task.

**To configure the task input:**

1. On the task **Input** tab, select the connection target in **Microsoft Azure Connection Target** that you created or identified in [Create a connection target for Microsoft Azure](#CreateaconnectiontargetforMicrosoftAzure).
2. In ** Azure User Name**, leave the YAQL expression `<% ctx().payload.victim %>` to reference the victim, or enter the expression `<% ctx().payload.attacker.value %>` to reference the attacker.
3. (Optional) If you want to validate whether the action would succeed but do not want to apply changes, select the **Dry Run** check box.

### Insert a YAQL expression in an input field

Any field that supports one or more [Yet Another Query Language](https://yaql.readthedocs.io/en/latest/) (YAQL) expressions has a **SELECT VARIABLE** drop-down list above the field. A YAQL expression can  reference a value in the playbook context, such as a field in the incident payload, or the published result of a previous task.

To insert a YAQL expression, place your cursor in the field where you want to insert the reference, click **SELECT VARIABLE**, and then select the variable. A YAQL expression that references the selected value appears in the field.

## Configure the task output (optional)

This task does not generate results that you can publish as output. For other ways to publish output, see [Configure task output (optional)](../add-task.md#Configuretaskoutputoptional).

## Technical reference

[Ideally this paragraph would state why the following information is useful, what to do with it...]

### Action Name

Disable Azure AD User

### Action Type

user_disable

### Permissions

User.ReadWrite.All permission in Azure AD

### Limitations

[Include this section if needed. Example: This action only works in AWS regions supported by Alert Logic.]
