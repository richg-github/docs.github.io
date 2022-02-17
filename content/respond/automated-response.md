# Get Started with Automated Response (Beta)

    This document is intended for early-access customers, and it is updated as Automated Response features are enhanced.     
Gain full security value from the Managed Detection and Response (MDR) platform by setting up automated responses to threats that Alert Logic detects. The Automated Response feature in the Alert Logic console helps you create workflows between Alert Logic and your applications to respond to common security threats automatically.   When you automate routine security tasks and responses to common threats, response times decrease. Your security team can  focus on new or more complex threats that require human analysis and intervention.

Automated Response requires an Alert Logic MDR Professional subscription.

Old draft: Automated Response is a security orchestration, automation, and response (SOAR) feature in the Alert Logic console. Automated Response helps you create workflows between Alert Logic and your applications to respond to security threats automatically. Your organization gains efficiency by integrating incident response into your business processes and tools.  When you automate routine security tasks, response times decrease and your security team can  focus on new cyberattacks and more complex threats that require human analysis and intervention.

Implement a response to take  actions that Alert Logic recommends using features in the Alert Logic console and devices or services that you already have.

Automated Response is a security orchestration, automation, and response (SOAR) feature in the Alert Logic console.

## Simple responses versus playbooks

Automated response includes two main features: Simple Responses and Playbooks.

Simple Responses is a core capability in MDR.  A simple response is an automated action that Alert Logic recommends that you take in response to a common security threat. Simple responses allow you to achieve a security outcome with an interaction between Alert Logic and a third-party device or service that you already have. The "simple" in simple responses refers to the guided interface that makes it easier to enable even complex response actions. The Alert Logic console steps you through the setup with a workflow that captures common practices and actions that Alert Logic recommends. No knowledge of programming or automation is required for setup. Available simple responses cover key use cases for the MDR platform:

* Isolating a host
* Disabling a user
* Blocking external attacker addresses

The Playbooks feature is available for organizations that want to go beyond Alert Logic recommendations made available in the core simple responses.  A playbook is a series of automated workflow actions between Alert Logic and your systems that you define. A playbook can also integrate the Alert Logic console with your devices  to achieve a security outcome. However, creating a playbook requires your team to define the logic instead of taking advantage of Alert Logic expertise and a guided interface. A knowledge of programming and workflow automation is helpful for creating playbooks but is not required. Several playbook templates are available to help you get started.

Alert Logic recommends that you start by implementing the simple responses that apply to your environment and devices. Then consider creating a playbook if  your organization has security needs that require different or more complex automation workflows.

## Access Automated Response

The Automated Response page is available under ![](../Resources/Images/dashboard/respond-icon.png)**Respond** in the Alert Logic console.

## Automated Response page

On the Automated Response page, you can access additional pages for creating, managing, and viewing automated response features.

### Simple Responses

On the Simple Responses page, you can add a simple response to take  actions that Alert Logic recommends, using features in the Alert Logic console and devices or services that you already have. After you choose the security outcome you want to achieve with your device, a guided interface steps you through the process, from connecting your device through choosing a recommended response.

### Playbooks

A playbook is a series of automated workflow actions between Alert Logic and your systems that you define. On the Playbooks page, you can add a playbook and configure it to run automatically in response to triggers, with or without an approval step. You can also run a playbook on a specific incident. Alert Logic provides templates you can use as a starting point to create playbooks for common scenarios.

For more information, see:

* [Add a Task to a Playbook (Beta)](automated-response/add-task.md)
* [Playbook Task Configuration Guide (Beta)](automated-response/task-configuration-guide.md)

### Exclusions

If you want your simple response to exclude specific users, IP addresses, or hosts, you can define them in exclusion lists. Then, when you set up your simple response, you can choose one or more of the lists to exclude the items from your automation. The Exclusions page lists all the exclusion lists created in your account and the accounts that you manage.

### Triggers

Playbooks can run automatically when defined criteria, called triggers, are met. A few examples of playbook triggers include threat level, MITRE classification, and targeted asset group. You can also configure a trigger to run a playbook at a scheduled time. More than one playbook can use the same trigger. The Triggers page lists all playbook triggers created in your account and the accounts that you manage.

For more information, see [link to triggers doc].

### History

The History page lists the run history for all your simple responses, playbooks, tasks, and actions. The records include information such as each time the item ran, the start and end time, and the run status (succeeded, failed, or pending).  The history provides an audit trail of all actions taken. You can open the item to view details, which can help you troubleshoot your automation during its initial creation and testing.

These records include information about the events that triggered the rules, and then the actions that were carried out.

You can review history information for each of your playbooks.. Open a specific record to see the events A complete audit trail lists

StackStorm maintains records of past action executions. These records include information about what events triggered what rules, and then what actions were executed. Common uses for this information includes root cause analysis reporting, operational control, and collaboration. We must change the name from Executions to "History and Audit".

Execution UX must show every action executed, it’s current status, etc. In the incident was the response action executed? need to provide audit/trail/history/verification

List of incidents and to see if it was responded to...dashboard. Open an incident time/date/actions/successful or not.....if you want to see details, go to executions UI

### Inquiries

The Inquiries page lists all playbooks and simple responses that require approval and their approval status. This page is where you can view and manage approval requests that are pending. You can see which playbooks are waiting for a human response to an inquiry sent to an email address, pushed to a business application via a connector, or pushed to the Alert Logic Mobile App. Administrators can take action directly from the page to respond to pending requests. For more information, see [Playbook Inquiries](automated-response/inquiries.md).

## What you can do with Automated Response

Automated Response can automate common security tasks and optimize your security analyst workflows with standard, predefined actions. A few examples of routine security tasks you can automate  include:

* Automatically block an IP address on Amazon Web Services (AWS) WAF (web application firewall)
* Open a security incident in ServiceNow and request approval to respond through the Alert Logic Mobile App
* Send an AWS policy change incident to a Microsoft Teams channel  and close the incident automatically if DevOps confirms they initiated the change, not a potential malicious user

For more ideas, explore Automated Response templates.

## Integration with your applications

Automated Response provides end-to-end workflow integration with your processes and tools to gain efficiency and reduce threat response time. Built-in Automated Response features support the following third-party applications and services:

Simple responses:

* Amazon Web Services (AWS)
* Microsoft Azure Active Directory
* Microsoft Teams
* PagerDuty
* ServiceNow
* Slack
* Zendesk

you can integrate Automated Response with any system for which you have a [connection target](../configure/connectors-beta/connection-targets/connection-target.md) configured in the Alert Logic console.To explore the list of built-in templates, see .

For the list of playbook tasks, see .

## Knowledge prerequisites

Separate must haves with nice to haves and consider simple versus expert mode

Intended audience for simple mode: Security Analysts

Built-in templates

Building a playbook from scratch

roles (job titles) with certain knowledge expectations, roles in Alert Logic, partners...

Helpful

YAML - Playbook action metadata is defined as YAML, the workflow definition is described in YAML

JSON - Input and output schema: output of an action (https://docs.stackstorm.com/actions.html)

## Technical prerequisites

Separate must haves with nice to haves and consider simple versus expert mode

Technical prerequisites

Set up connection targets for integrations with third-party applications and services

Set up the Mobile App for approvals

admin role?

knowledge prerequisites:

Input

For more information, see Design the architecture.

**********

1. Add a task to the playbook (21)
2. Add a task condition
3. Join to ?

Join parallel tasks

For an action like send_approval_email, if you have parallel tasks/branches of execution such as Approved for Block/Not Approved for Block, at some point you might want to wait for these parallel tasks to finish before proceeding. You can only join things that are in executing in parallel

Library of playbooks

methods for succeeded and failed: Chadwick Moss request

biweekly demo 1/15 - Malcolm's part: Analytics technology AE and NGX. As they are configuring a playbook, facilitate awareness, visibility, or knowledge gaps when they're in the AR experience. help them make informed decisions about automated response configurations. They can information to help them

**To enter details about the playbook:**

1. In the Alert Logic console, click the navigation menu icon (![](../Resources/Images/dashboard/menu-icon.png)), click ![](../Resources/Images/dashboard/respond-icon.png)**Respond**, and then click **Automated Response**.
2. On the Playbooks tab, click the add icon (![](../Resources/Images/Icons/cdAddPlus.png)), and then click **Incident**.
3. Type a descriptive name that easily identifies the playbook in a list—for example, "???."
4. Type a detailed description for your playbook to help you identify the playbook later.
5. (Optional) Click the **Parameters** tab to view parameters available for use in your playbook tasks and optionally add your own input parameters:
   1. Click the **ADD PARAMETER** icon.
   2. Enter your parameter name using only alphanumeric and underscore characters.
   3. Type a brief description to help you identify your parameter and its purpose.
   4. Select the JSON parameter type.
   5. Choose whether the parameter is required, immutable (value cannot be changed), or secret (needs to be encrypted).
7. (Optional) Click the **Output** tab to view parameters available for use in your playbook tasks and optionally add your own input parameters:
8. Click **SAVE AND CONTINUE**.

Playbook model notes (mtg with Pavel T. 1/20/21)

Need a primer of what the playbooks are, constructs that are there.

We can use our own words, need to clearly explain what it is and how to use it. Start defining with examples. If you want to do this, do this.

Definitions that must be clear, plus tell how to do it with examples. If you want to do this, this is how, that, this is how. conditions, retries, with items (an ability to execute in a loop over time), suggests referring to StackStorm doc for structure,

Have to explain how to trigger, what triggers.

Structure it as blocks: context, variables of the context, examples of how these building blocks go.

Tasks

Use the with items section to process a list of items in a task [ex. <% ctx(messages) %>. The task will iterate through each item and request an action execution for each item. By default, all the items will be processed at the same time. When concurrency is specified, the number of items up to the concurrency value will be processed and the remaining items will be queued. When the action execution for an item is completed, the next item in the list will be processed.

The task result is a list of the action execution results in the same order as the items. All action executions must complete successfully for the task to reach a succeeded state. If one or more action executions fail, then the task will result in a failed state.

When there’s a request to cancel or pause the workflow, the task will be in a canceling or pausing state respectively until all action executions in the process of being executed are completed. Once these action executions are completed, the task will go to canceled or paused state respectively. If concurrency for the task is specified and there are remaining items, no new action executions will be requested. When a paused workflow resumes, the task will continue to process any remaining items.

Technical details:

Playbooks based on StackStorm technology, specifically Orquesta workflow [but we don't want to talk about this in the doc]

https://docs.stackstorm.com/workflows.html Orquesta is a new workflow engine, designed specifically for StackStorm, released in 2019. With Orquesta, you can define simple sequential workflows or complex workflows with forks, joins, and sophisticated data transformation and queries.

https://docs.stackstorm.com/orquesta/overview.html:

A workflow definition is a structured YAML file that describes the intent of the workflow. A workflow is made up of one or more tasks. A task defines what action to execute, with what input. When a task completes, it can transition into other tasks based upon criteria. Tasks can also publish output for the next tasks. When there are no more tasks to execute, the workflow is complete.

Orquesta includes a native language spec for the workflow definition. The language spec is decomposed into various models and described with JSON schema. A workflow composer that understands the models converts the workflow definition into a directed graph. The nodes represent the tasks and edges are the task transition. The criteria for task transition is an attribute of the edge. The graph is the underpinning for conducting the workflow execution. The workflow definition is just syntactic sugar.

When there is no more tasks identified to run next, the workflow is complete. On workflow completion, regardless of status, the workflow result contains the list of error(s) if any and the output as defined in the workflow defintion. If the workflow failed, the workflow conductor will do its best to render the output from the latest version of the runtime context at completion of the workflow execution.

https://docs.stackstorm.com/actions.html "A YAML metadata file ... describes the action, and its inputs."

"Action metadata is used to describe the action and is defined as YAML. These attributes can be present in the metadata file:

name - Name of the action.

runner_type - The type of runner to execute the action.

enabled - Action cannot be invoked when disabled.

entry_point - Location of the action launch script relative to the /opt/stackstorm/packs/${pack_name}/actions/ directory.

parameters - A dictionary of parameters and optional metadata describing type and default. The metadata is structured data following the JSON Schema specification draft 4. The common parameter types allowed are string, boolean, number (whole numbers and decimal numbers - e.g. 1.0, 1, 3.3333, etc.), object, integer (whole numbers only - 1, 1000, etc.) and array. If metadata is provided, input args are validated on action execution. Otherwise, validation is skipped.

tags - An array with tags for this actions for the purpose of providing supplemental information
