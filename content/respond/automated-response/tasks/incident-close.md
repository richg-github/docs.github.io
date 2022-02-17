# Configure a Close Incident Task (Draft)

In your automated response playbook, you can configure a Close Incident  task to close an Alert Logic [incident](../../../analyze/incidents.md).

In your automated response playbook, you can configure a Close Incident  task to add the final threat assessment to an Alert Logic [incident](../../../analyze/incidents.md), add a note for your organization about the reason for closing the incident, and then close it.

The source of the incident  can be any of the following:

* Incident that meets the conditions of a trigger for the playbook. For more information, see [link to topic about playbook triggers].
* Incident that a user selects to run the playbook on manually. For more information, see [link to topic about running a playbook on an incident].
* Sample incident payload used to test the playbook. For more information, see [link to topic about playbook testing].

Complete the following steps to successfully configure the Close Incident task:

1. [Add the task to your playbook](#Addthetasktoyourplaybook)
2. [Configure the task input](#Configurethetaskinput)
3. [Configure the task output (optional)](#Configurethetaskoutputoptional)

## Add the task to your playbook

If you have not added the  task to your playbook, complete the instructions in [Add a task in the workflow diagram](../add-task.md#Addataskintheworkflowdiagram) and [Add task details (optional)](../add-task.md#Addtaskdetailsoptional).

## Configure the task input

Complete these instructions to provide the input values for your Close Incident task.

**To configure the task input:**

1. On the task **Input** tab, leave the YAQL expression in **Incident ID** to reference the incident that you want the playbook to close:
`<% ctx().payload.incidentId %>`        You can also enter a full incident ID manually, such as for testing purposes (example: 9921bdc3-fe06-4adb-b8ce-aa5da3e41086).
2. In **Note**, enter a note for the audit log about the final threat assessment.
3. In **Threat Assessment**,  select an option to indicate your final threat assessment.

### Threat assessment options

The following Threat Assessment options inform others in your organization whether the threat is valid, and what action (if any) the organization should take to remediate the threat.

Threat presents a valid risk:

* Taking action to mitigate the threat.
* Risk is acceptable. No action required.

Threat does not present a valid risk:

* Compensating control in place. No action required.
* The threat is not valid.
* Other assessment.

### Insert a YAQL expression in an input field

Any field that supports one or more [Yet Another Query Language](https://yaql.readthedocs.io/en/latest/) (YAQL) expressions has a **SELECT VARIABLE** drop-down list above the field. A YAQL expression can  reference a value in the playbook context, such as a field in the incident payload, or the published result of a previous task.

To insert a YAQL expression, place your cursor in the field where you want to insert the reference, click **SELECT VARIABLE**, and then select the variable. A YAQL expression that references the selected value appears in the field.

## Configure the task output (optional)

This task generates the following results when it completes. You can publish a current task result or other values by adding them as output. Published output  is available for reference in later playbook tasks. For instructions, see [Configure task output (optional)](../add-task.md#Configuretaskoutputoptional).

* **new** (*object*)—New incident details
   * *Suggested rewrite:* Details added to the incident when closed
* **new.notes** (*string*)—Notes about completion
   * *Suggested rewrite:* Note about the final threat assessment  (example: The detected activity is expected in the affected environment.)
* **new.reason_code** (*string*)—Reason for completion
   * *Suggested rewrite:* Final threat assessment code (example: threat_not_valid)
* **new.status** (*string*)—Incident status
   * *Suggested rewrite:* Incident status after closure (value: completed)
* **new.status_change_time** (*string*)—Status change time
   * *Suggested rewrite:* ISO date and time in UTC of the closure (example: 2021-08-10T11:22:27.799796+00:00)
* **old** (*object*)—Old incident details
   * *Suggested rewrite:* Incident details before closure
* **old.status** (*string*)—Incident status
   * *Suggested rewrite:* Incident status before closure (value: open)
* **old.status_change_time** (*string*)—Status change time
   * *Suggested rewrite:* ISO date and time in UTC of the previous incident status change (example: 2021-07-10T11:42:21.734796+00:00)

## Technical reference

[Ideally this paragraph would state why the following information is useful, what to do with it...]

### Action Name

Close Incident

### Action Type

incident_close

### Permissions

[Include this section if needed. Example: Azure permissions.]

### Limitations

[Include this section if needed. Example: This action only works in AWS regions supported by Alert Logic.]
