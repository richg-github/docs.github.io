# Configure a Disable AWS User Task (Draft)

In your automated response playbook, you can configure a Disable AWS User task to disable an Amazon Web Services (AWS) user.

Complete the following steps to successfully configure the Disable AWS User task:

1. [Create a connection target for the AWS IAM role](#CreateaconnectiontargetfortheAWSIAMrole)
2. [Add the task to your playbook](#Addthetasktoyourplaybook)
3. [Configure the task input](#Configurethetaskinput)
4. [Configure the task output (optional)](#Configurethetaskoutputoptional)

## Create a connection target for the AWS IAM role

The Disable AWS User task requires a connection target for the AWS IAM role that grants Alert Logic access to disable AWS users.

To check whether it exists,  in the Alert Logic console, click ![](../../../Resources/Images/dashboard/configure-icon.png)**Configure** in the navigation menu (![](../../../Resources/Images/dashboard/menu-icon.png)),  click **Connectors**, and then click the **Connection Targets** tab.

If any AWS IAM role connection targets appear in the list, review their configurations to determine whether the one you need already exists.

If you do not have a connection target for your AWS IAM role already, complete the instructions in [Configure AWS IAM Role Connection Target](../../../configure/connectors-beta/connection-targets/AWS-IAM-role.md).

## Add the task to your playbook

If you have not added the  task to your playbook, complete the instructions in [Add a task in the workflow diagram](../add-task.md#Addataskintheworkflowdiagram) and [Add task details (optional)](../add-task.md#Addtaskdetailsoptional).

## Configure the task input

Complete these instructions to provide the input values for your  Disable AWS User task.

**To configure the task input:**

1. On the task **Input** tab, select the connection target in **AWS IAM Role Connection Target** that you created or identified in [Create a connection target for the AWS IAM role](#CreateaconnectiontargetfortheAWSIAMrole).
2. In AWS** IAM User Name**, leave the YAQL expression `<% ctx().payload.attacker.value %>` to reference the attacker in the incident payload, or enter the attacker username (example: SomeAttacker).

### Insert a YAQL expression in an input field

Any field that supports one or more [Yet Another Query Language](https://yaql.readthedocs.io/en/latest/) (YAQL) expressions has a **SELECT VARIABLE** drop-down list above the field. A YAQL expression can  reference a value in the playbook context, such as a field in the incident payload, or the published result of a previous task.

To insert a YAQL expression, place your cursor in the field where you want to insert the reference, click **SELECT VARIABLE**, and then select the variable. A YAQL expression that references the selected value appears in the field.

## Configure the task output (optional)

This task generates the following results when it completes. You can publish a current task result or other values by adding them as output. Published output  is available for reference in later playbook tasks. For instructions, see [Configure task output (optional)](../add-task.md#Configuretaskoutputoptional).

* **access_keys_disabled** (*array*)—List of access keys which were disabled
   * *Suggested rewrite:* List of disabled AWS access keys

## Technical reference

[Ideally this paragraph would state why the following information is useful, what to do with it...]

### Action Name

Disable AWS User

### Action Type

user_disable

### Permissions

[Include this section if needed. Example:  Azure permissions.]

### Limitations

[Include this section if needed. Example: This action only works in AWS regions supported by Alert Logic.]
