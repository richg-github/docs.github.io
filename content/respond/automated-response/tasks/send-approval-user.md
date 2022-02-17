# Configure a Send Approval Request to User Task (Draft)

In your automated response playbook, you can configure a Send Approval Request to User task to request approval from a user via an email or a push notification to the Alert Logic Mobile App.

You can send approval requests to multiple users [in your account?], but only the first to respond can approve or reject the task. A message informs subsequent responders that the inquiry already received a response.

[Need  a typical use case to go here, maybe one that involves incidents]

The source of the incident  can be any of the following:

* Incident that meets the conditions of a trigger for the playbook. For more information, see [link to topic about playbook triggers].
* Incident that a user selects to run the playbook on manually. For more information, see [link to topic about running a playbook on an incident].
* Sample incident payload used to test the playbook. For more information, see [link to topic about playbook testing].

Complete the following steps to successfully configure the Send Approval Request to User task:

1. [Add the task to your playbook](#Addthetasktoyourplaybook)
2. [Configure the task input](#Configurethetaskinput)
3. [Configure the task output (optional)](#Configurethetaskoutputoptional)

## Add the task to your playbook

If you have not added the  task to your playbook, complete the instructions in [Add a task in the workflow diagram](../add-task.md#Addataskintheworkflowdiagram) and [Add task details (optional)](../add-task.md#Addtaskdetailsoptional).

## Configure the task input

Complete these instructions to provide the input values for your Send Approval Request to User task.

**To configure the task input:**

1. On the task **Input** tab, select one or more approval recipients in **User(s)**. You can use the search bar to help you find names and email addresses.
2. In **Message Subject**, edit the subject for the approval message, or use the one provided. You can enter text and/or YAQL expressions.
3. In **Message**, edit the approval message, or use the one provided.
4. Choose one or more approval delivery methods:
   * Send Email
   * Send to Alert Logic Mobile App
6. In **Approval Expiration in Minutes**, enter a wait time before automatic task failure in minutes, or keep the default value: 60. The minimum  is 60.

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

Send Approval Request to User

### Action Type

send_approval_user

### Permissions

[Include this section if needed. Example:  Azure permissions.]

### Limitations

[Include this section if needed. Example: This action only works in AWS regions supported by Alert Logic.]
