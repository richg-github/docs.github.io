# Configure a Reopen Incident Task (Draft)

In your automated response playbook, you can configure a Reopen Incident  task to reopen an Alert Logic [incident](../../../analyze/incidents.md) and add a note for your organization about the reason for reopening it.

The source of the incident  can be any of the following:

* Incident that meets the conditions of a trigger for the playbook. For more information, see [link to topic about playbook triggers].
* Incident that a user selects to run the playbook on manually. For more information, see [link to topic about running a playbook on an incident].
* Sample incident payload used to test the playbook. For more information, see [link to topic about playbook testing].

Complete the following steps to successfully configure the Reopen Incident task:

1. [Add the task to your playbook](#Addthetasktoyourplaybook)
2. [Configure the task input](#Configurethetaskinput)
3. [Configure the task output (optional)](#Configurethetaskoutputoptional)

## Add the task to your playbook

If you have not added the  task to your playbook, complete the instructions in [Add a task in the workflow diagram](../add-task.md#Addataskintheworkflowdiagram) and [Add task details (optional)](../add-task.md#Addtaskdetailsoptional).

## Configure the task input

Complete these instructions to provide the input values for your Reopen Incident task.

**To configure the task input:**

1. On the task **Input** tab, leave the YAQL expression in **Incident ID** to reference the incident that you want the playbook to reopen:
`<% ctx().payload.incidentId %>`You can also enter a full incident ID manually, such as for testing purposes (example: 9921bdc3-fe06-4adb-b8ce-aa5da3e41086).
2. In **Note**, enter a note for the audit log about why to reopen the incident.

### Insert a YAQL expression in an input field

Any field that supports one or more [Yet Another Query Language](https://yaql.readthedocs.io/en/latest/) (YAQL) expressions has a **SELECT VARIABLE** drop-down list above the field. A YAQL expression can  reference a value in the playbook context, such as a field in the incident payload, or the published result of a previous task.

To insert a YAQL expression, place your cursor in the field where you want to insert the reference, click **SELECT VARIABLE**, and then select the variable. A YAQL expression that references the selected value appears in the field.

## Configure the task output (optional)

This task generates the following results when it completes. You can publish a current task result or other values by adding them as output. Published output  is available for reference in later playbook tasks. For instructions, see [Configure task output (optional)](../add-task.md#Configuretaskoutputoptional).

* **new** (*object*)—New incident details
   * *Suggested rewrite:* Details added to the incident when reopened
* **new.notes** (*string*)—Notes about reopening
   * *Suggested rewrite:* Note about reopening the incident (example: The detected activity is not expected in the affected environment.)
* **new.reason_code** (*string*)—Reason for reopening
   * *Suggested rewrite:* Threat assessment code for a reopened incident (value: other)
* **new.status** (*string*)—Incident status
   * *Suggested rewrite:* Incident status for a reopened incident (value: open)
* **new.status_change_time** (*string*)—Status change time
   * *Suggested rewrite:* ISO date and time in UTC of the reopening (example: 2021-08-10T11:22:27.799796+00:00)
* **old** (*object*)—Old incident details
   * *Suggested rewrite:* Incident details before reopening
* **old.status** (*string*)—Incident status
   * *Suggested rewrite:* Incident status before reopening (value: completed)
* **old.status_change_time** (*string*)—Status change time
   * *Suggested rewrite:* ISO date and time in UTC of the previous incident status change (example: 2021-07-10T11:42:21.734796+00:00)

## Technical reference

[Ideally this paragraph would state why the following information is useful, what to do with it...]

### Action Name

Reopen Incident

### Action Type

incident_reopen

### Permissions

[Include this section if needed. Example: Azure permissions.]

### Limitations

[Include this section if needed. Example: This action only works in AWS regions supported by Alert Logic.]
