# Configure an Update Incident Task (Draft)

In your automated response playbook, you can configure an Update Incident  task to add a note for your organization to an Alert Logic [incident](../../../analyze/incidents.md) and update the threat assessment.

The source of the incident  can be any of the following:

* Incident that meets the conditions of a trigger for the playbook. For more information, see [link to topic about playbook triggers].
* Incident that a user selects to run the playbook on manually. For more information, see [link to topic about running a playbook on an incident].
* Sample incident payload used to test the playbook. For more information, see [link to topic about playbook testing].

Complete the following steps to successfully configure the Update Incident task:

1. [Add the task to your playbook](#Addthetasktoyourplaybook)
2. [Configure the task input](#Configurethetaskinput)
3. [Configure the task output (optional)](#Configurethetaskoutputoptional)

## Add the task to your playbook

If you have not added the  task to your playbook, complete the instructions in [Add a task in the workflow diagram](../add-task.md#Addataskintheworkflowdiagram) and [Add task details (optional)](../add-task.md#Addtaskdetailsoptional).

## Configure the task input

Complete these instructions to provide the input values for your Update Incident task.

**To configure the task input:**

1. On the task **Input** tab, leave the YAQL expression in **Incident ID** to reference the incident that you want the playbook to update:
`<% ctx().payload.incidentId %>`You can also enter a full incident ID manually, such as for testing purposes (example: 9921bdc3-fe06-4adb-b8ce-aa5da3e41086).
2. In **Note**, enter a note for the audit log about this incident update.
3. In **Threat Assessment**,  select an option to indicate your updated threat assessment.

### Threat assessment options

The following Threat Assessment options inform others in your organization whether the threat is valid, and what action (if any) the organization should take to remediate the threat.

Threat presents a valid risk:

* Taking action to mitigate the threat.
* Risk is acceptable. No action required.

Threat does not present a valid risk:

* Compensating control in place. No action required.
* The threat is not valid.
* Other assessment.

You can also mark the incident as **Not concluded yet.**

### Insert a YAQL expression in an input field

Any field that supports one or more [Yet Another Query Language](https://yaql.readthedocs.io/en/latest/) (YAQL) expressions has a **SELECT VARIABLE** drop-down list above the field. A YAQL expression can  reference a value in the playbook context, such as a field in the incident payload, or the published result of a previous task.

To insert a YAQL expression, place your cursor in the field where you want to insert the reference, click **SELECT VARIABLE**, and then select the variable. A YAQL expression that references the selected value appears in the field.

## Configure the task output (optional)

This task generates the following results when it completes. You can publish a current task result or other values by adding them as output. Published output  is available for reference in later playbook tasks. For instructions, see [Configure task output (optional)](../add-task.md#Configuretaskoutputoptional).

* **feedback** (*string*)—Feedback message
   * *Suggested rewrite:* Note about the update  (example: The detected activity is expected in the environment affected.)
* **feedback_datetime** (*string*)—Feedback datetime
   * *Suggested rewrite:* ISO date and time in UTC of the update (example: 2021-08-14T09:57:35.535995+00:00)
* **feedback_reason** (*string*)—Reason for feedback
   * *Suggested rewrite:* Code for the updated threat assessment (example: threat_not_valid)
* **feedback_user** (*string*)—Feedback user name
   * *Suggested rewrite:* Name and email address of the user who updated the incident (example: CustomerFirstName CustomerLastName <username@xyz.com>)

## Technical reference

[Ideally this paragraph would state why the following information is useful, what to do with it...]

### Action Name

Update Incident

### Action Type

incident_add_feedback

### Permissions

[Include this section if needed. Example: Azure permissions.]

### Limitations

[Include this section if needed. Example: This action only works in AWS regions supported by Alert Logic.]
