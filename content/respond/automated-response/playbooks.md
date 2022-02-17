# Get Started with Playbooks

A playbook is a series of automated workflow actions between Alert Logic and your systems that you define. On the Playbooks page, you can add a playbook and configure it to run automatically in response to triggers, with or without an approval step. You can also run a playbook on a specific incident. Alert Logic provides templates you can use as a starting point to create playbooks for common scenarios.

The Playbooks page lists all the playbooks created in your account and the accounts that you manage.

## How playbooks work

A playbook is built from one or more tasks that you define. The Alert Logic console depicts the tasks in a workflow diagram. The diagram helps you visualize the sequencing of tasks, any conditions required for transitioning to the next task, and the relationships among tasks.

A task includes the name you give it, the action to carry out, and the action's input, which you enter on the task's Input tab.

When a task completes, it can transition to the next tasks based upon criteria. Tasks can publish output for the next tasks. The task's Output tab is where you define criteria for carrying out the next tasks and specify any output to publish to the next tasks.

Playbook workflows can be simple, with sequential actions that flow from one to the next. Or they can be more complex, with forks into parallel branches that then join together again (or not).

When no more tasks exists for the playbook to carry out, the workflow is complete.

You can run a playbook manually from an incident, or it can run automatically when the criteria defined in a trigger are met. You can also nest playbooks, meaning a playbook can contain other playbooks.

## Playbook process overview

1. [Plan Your Automated Response](plan.md)
2. [Create the playbook](#Createtheplaybook)
3. [Validate the playbook](#Validatetheplaybook)
4. [Test the playbook](#Testtheplaybook)
5. (Optional) [Specify criteria to run the playbook automatically](#Specifycriteriatoruntheplaybookautomatically)
6. (Optional) [Run the playbook on demand](#Runtheplaybookondemand)
7. View playbook run history.
See what time playbook started and ended
Granular details on the attack and the action taken
8. View inquiries.
apply to pending > take an action and respond?

## Create the playbook

## Validate the playbook

To ensure that your playbook has all required information, the next step is to validate it. Click the **VALIDATE** icon. A message indicates if validation is successful. If validation fails, one or more messages appear to indicate the missing information.

As you work, Alert Logic recommends that you save often as soon as you have a successful configuration. Click the **SAVE** icon to save your work and validate the playbook. The playbook does not save if the playbook is not valid.

![](../../Resources/Images/automated-response/playbook-validate.png)

## Test the playbook

After you validate the playbook, you can test it. This step runs the playbook with a sample incident payload. To test the playbook, click the **TEST** icon. You can then check that the playbook results are what you expected and edit your playbook as necessary.

## Specify criteria to run the playbook automatically

If you want the playbook to run automatically when certain incident criteria are met, you must specify the criteria on the Incident Notifications page. Criteria include threat levels and escalation status. For more information about setting up an incident notification, see [Incident Notifications](../../configure/notifications/incident.md). In the step where you choose recipients, click **Subscribe Playbook**, and then select your playbook.

## Run the playbook on demand

You can run a playbook to respond to a specific incident.

**To run the playbook on demand:**

1. In the Alert Logic console, click the navigation menu icon (![](../../Resources/Images/dashboard/menu-icon.png)), click ![](../../Resources/Images/dashboard/respond-icon.png)**Respond**, and then click **Incidents**.
2. Open the incident for which to run the playbook.
3. Click the **PLAYBOOK** icon.
![](../../Resources/Images/automated-response/playbook-run.png)
