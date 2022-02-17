# Playbook Task Configuration Guide (Beta)

Playbook tasks support common security activities such as blocking attackers and disabling user accounts in an Amazon Web Services (AWS) environment.

The following table lists all playbook tasks with an available configuration guide. For instructions on how to configure the input for a specific task, click a link in the Task column.  For information about adding a task to your playbook and configuration steps that are common to all tasks, see [Add a Task to a Playbook (Beta)](add-task.md).

| Vendor | Task | Description |
|---|---|---|
| Alert Logic | Block IPs withAlert Logic WAF | Request the Alert Logic WAF appliance to block a list of IP addresses. |
| Alert Logic | [Close Incident](tasks/incident-close.md) | Close an incident and provide the threat assessment. |
| Alert Logic | [Reopen Incident](tasks/incident-reopen.md) | Reopen a closed incident. |
| Alert Logic | Run Alert Logic MDR Action | Run an Alert Logic MDR action for an [Alert Logic service](https://alertlogic-sdk-python.readthedocs.io/en/latest/). |
| Alert Logic | [Send Approval Request to User](tasks/send-approval-user.md) | Request approval from a user via an email or a push notification to the Alert Logic Mobile App. |
| Alert Logic | [Send Approval Request via Connection Target](tasks/send-approval-channel.md) | Send an approval request to an application via a connection target. |
| Alert Logic | [Send Incident via Connector](tasks/connector-send-incident.md) | Send incident details or create a service ticket via a webhook or email connector. |
| Alert Logic | [Update Incident](tasks/incident-update.md) | Update an incident with threat assessment feedback. |
| AWS | AWS WAF Block IP Address - CloudFront | Block an IP address in an Amazon CloudFront web distribution integrated with the  AWS WAF  (web application firewall) service. |
| AWS | AWS WAF Block IP Address - Regional | Block an IP address in a regional AWS WAF (web application firewall). |
| AWS | AWS WAF Unblock IP Address - CloudFront | Unblock an IP address in an Amazon CloudFront web distribution integrated with the  AWS WAF (web application firewall) service. |
| AWS | AWS WAF Unblock IP Address - Regional | Unblock an IP address in a regional AWS WAF (web application firewall). |
| AWS | [Disable AWS User](tasks/aws-disable-user.md) | Disable an AWS user and its access keys. |
| AWS | [Send Message to Amazon SNS Topic](tasks/amazon-sns-publish.md) | Trigger an action in AWS by sending a message. |
| AWS | Run AWS Action | Run any action supported by [ SDK for Python (Boto3) (AWS documentation)](https://docs.aws.amazon.com/pythonsdk/?id=docs_gateway) for an AWS service. |
| AWS | Send Event to Amazon EventBridge | Send events to Amazon EventBridge for a serverless infrastructure such as AWS Lambda. |
| AWS | [Update AWS WAF IP Set](tasks/aws-waf-update-ip-set.md) | Update an AWS WAF (web application firewall) IP set that controls access to a protected Amazon CloudFront distribution or regional application. |
| Microsoft | [Disable Azure AD User](tasks/azure-disable-user.md) | Disable a user in Microsoft Azure Active Directory (AD). |
| Microsoft | [Enable Azure AD User](tasks/azure-enable-user.md) | Enable a user in Azure AD. |
| Microsoft | [Send Incident to Microsoft Teams](tasks/teams-send-incident.md) | Send incident details to Microsoft Teams via a connector. |
| General Operation | Do Nothing | Do nothing, such as while waiting for a parallel task to complete or when transitioning from one condition to another. |
| General Operation | Format as CSV | Format a list of JSON objects as a list of CSV strings. |
| General Operation | Parse CSV | Convert a list of CSV strings to a JSON object in which the first string contains the property names and the following strings contain the values. |
| General Operation | Pause Playbook | Pause running of the playbook. |
| General Operation | Print Message | Print a message to the playbook for troubleshooting purposes. |
| General Operation | Run Remote Command | Run a remote command securely with the SSH protocol. |
| General Operation | Send HTTP Request | Invoke  REST API to carry out HTTP requests. This action supports specifying HTTP verbs, an authorization header, custom headers, and payload. |
| PagerDuty | [Send Incident to PagerDuty](tasks/pagerduty-send-incident.md) | Send incident details to PagerDuty via a connector. |
| ServiceNow | [Create ServiceNow Incident](tasks/servicenow-create-incident.md) | Create an incident in ServiceNow via a connector. |
| ServiceNow | Create ServiceNow Record | Create a record in a ServiceNow table. |
| ServiceNow | Delete ServiceNow Record | Delete a record from a ServiceNow table. |
| ServiceNow | Get ServiceNow Records | Get records from a ServiceNow table. |
| ServiceNow | Update ServiceNow Record | Update an existing record in a ServiceNow table. |
| ServiceNow | Upload Data to ServiceNow | Upload data to a ServiceNow table as an attachment. |
| Slack | [Send Incident to Slack](tasks/slack-send-incident.md) | Send incident details to Slack via a connector. |
| Slack | [Send Message to Slack](tasks/post-message.md) | Send a message to a Slack channel via a connection target. |
| Zendesk | Create Zendesk Ticket | Create a ticket on Zendesk. |
| Zendesk | Search Zendesk Tickets | Search tickets on Zendesk. |
| Zendesk | Update Zendesk Ticket | Update a ticket on Zendesk. |
| Zendesk | Update Zendesk Ticket Status | Update the status of a Zendesk ticket. |
