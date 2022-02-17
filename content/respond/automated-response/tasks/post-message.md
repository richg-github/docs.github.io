# Configure a Send Message to Slack Task (Draft)

In your automated response playbook, you can configure a Send Message to Slack task to send  a message from Alert Logic to Slack via a [connection target](../../../configure/connectors-beta/connection-targets/connection-target.md).

Complete the following steps to successfully configure the Send Message to Slack task:

1. [Create a Slack connection target](#CreateaSlackconnectiontarget)
2. [Add the task to your playbook](#Addthetasktoyourplaybook)
3. [Configure the task input](#Configurethetaskinput)
4. [Configure the task output (optional)](#Configurethetaskoutputoptional)

## Create a Slack connection target

The Send Incident to Slack task requires a Slack connection target.

To check whether it exists,  in the Alert Logic console, click ![](../../../Resources/Images/dashboard/configure-icon.png)**Configure** in the navigation menu (![](../../../Resources/Images/dashboard/menu-icon.png)),  click **Connectors**, and then click the **Connection Targets** tab.

If any Slack connection targets appear in the list, review the configured base URL for one that contains the identifier for your Slack workspace.

* In Slack, the workspace identifier is the part of the path that follows "client/": https://app.slack.com/client/XNNNXXXXXXNX/….
* In the connection target, the identifier is the part of the path that follows "services/": https://hooks.slack.com/services/XNNNXXXXXXNX/….

If you do not have a connection target for your Slack workspace already, complete the instructions in [Configure Slack Connection Target](../../../configure/connectors-beta/connection-targets/slack.md).

## Add the task to your playbook

If you have not added the  task to your playbook, complete the instructions in [Add a task in the workflow diagram](../add-task.md#Addataskintheworkflowdiagram) and [Add task details (optional)](../add-task.md#Addtaskdetailsoptional).

## Configure the task input

Complete these instructions to provide the input values for your Send Incident to Slack task.

**To configure the task input:**

1. On the task **Input** tab, select the connection target in **Slack Connection Target** that you created or identified in [Create a Slack connection target](#CreateaSlackconnectiontarget).
2. In **Message**, enter the message that you want to send. 
Slack supports the following character formatting:Example goes here
   * For bold, enclose the text with one asterisk (*) character  (example: *bold*).
   * For italic, enclose the text with one underscore (_) character (example: _italic_).
4. (Optional) To specify the channel to send the message to, enter its name preceded by the number sign (#) character (example: #other-channel). If you leave **Channel** blank, the task sends the message to the channel that the user specified in Slack when the incoming webhoook was configured.
5. (Optional) To replace the default message icon in Slack, do one of the following:
   * In **Custom Icon Emoji**, enter the emoji code enclosed with the colon (:) character (example: :shield:) .
   * In **Custom Icon Image URL**, enter the URL for the replacement image.
7. To disable formatting in the message and treat the message as text, not code, select the **Message is plain text** check box.

### Insert a YAQL expression in an input field

Any field that supports one or more [Yet Another Query Language](https://yaql.readthedocs.io/en/latest/) (YAQL) expressions has a **SELECT VARIABLE** drop-down list above the field. A YAQL expression can  reference a value in the playbook context, such as a field in the incident payload, or the published result of a previous task.

To insert a YAQL expression, place your cursor in the field where you want to insert the reference, click **SELECT VARIABLE**, and then select the variable. A YAQL expression that references the selected value appears in the field.

## Configure the task output (optional)

This task does not generate results that you can publish as output. For other ways to publish output, see [Configure task output (optional)](../add-task.md#Configuretaskoutputoptional).

## Technical reference

[Ideally this paragraph would state why the following information is useful, what to do with it...]

### Action Name

Send Message to Slack

### Action Type

post_message

### Permissions

[Include this section if needed. Example:  Azure permissions.]

### Limitations

[Include this section if needed. Example: This action only works in AWS regions supported by Alert Logic.]
