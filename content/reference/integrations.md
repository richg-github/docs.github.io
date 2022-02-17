# Alert Logic Integrations

Alert Logic Managed Detection and Response is a suite of threat management services and capabilities. Alert Logic offers three levels of security: Essentials, Professional, and Enterprise. The tiers provide the different levels of coverage from a tightly integrated toolset, cybersecurity threats, expanding compliance risks, and resource constraints across operating systems and applications you run on various platforms.

You configure custom checks as inputs to Alert Logic, and extend the capabilities of Alert LogicAWS environments with AWS Inspector and AWS Config Rules. The integration and APIs also can be used with Alert Logic Cloud Insight.

## Prerequisites

To use Alert Logic integrations, you must:

* Register for an Alert Logic account
* Set up at least one [deployment](../get-started/deployments.md)

## Integrations

### Amazon Guard Duty

Amazon GuardDuty analyzes and processes VPC Flow Logs and AWS CloudTrail event logs, and uses security logic and AWS usage statistics techniques. GuardDuty then identifies unexpected, unauthorized, and malicious activity, like escalations of privileges, uses of exposed credentials, or communication with malicious IPs, URLs, or domains.

After you enable GuardDuty in AWS, you must install the Alert Logic collector for GuardDuty in each region you want to monitor, so you can view GuardDuty findings in the Alert Logic console.

[Installation Details](https://github.com/alertlogic/cwe-collector/blob/master/cfn/README-GD.md) | [Source Code](https://github.com/alertlogic/cwe-collector/)

### Amazon Inspector

Amazon Inspector is an AWS service that produces a detailed report, complete with prioritized steps, for vulnerability remediation. The Alert Logic integration, performed through a specific Lambda check added to the Alert Logic custom Lambda checks, incorporates Amazon Inspector data into your remediations, which provides a single, holistic view of your security posture.

[Installation Details](https://github.com/alertlogic/ci_lambda_checks/blob/master/README.md) | [Source Code](https://github.com/alertlogic/ci_lambda_checks)

### AWS Config Rules

AWS Config Rules comprise an extended rule system for AWS Config. The Alert Logic integration, performed through a specific Lambda check added to the Alert Logic custom Lambda checks, incorporates AWS Config Rules data into your  remediations to provide a single, holistic view of your security posture.

[Installation Details](https://github.com/alertlogic/ci_lambda_checks/blob/master/README.md) | [Source Code](https://github.com/alertlogic/ci_lambda_checks)

### Cloud Insight Custom Checks

Alert Logic Custom Checks enable you to work within the Alert Logic environment to create custom rules and behaviors around changes to your  deployments. Those configurations then incorporate the results into your  remediations to provide a single, holistic view of your security posture.

[Installation Details](https://github.com/alertlogic/ci_lambda_checks/blob/master/README.md) | [Source Code](https://github.com/alertlogic/ci_lambda_checks)

### Alert Logic Add-on for Atlassian JIRA

The Alert Logic Add-on for JIRA integrates Alert Logic remediations as JIRA issues, which allows you to configure, manage, and assign issues to JIRA teams. JIRA team members can use the add-on to review and then dispose assigned remediations.

Installation Details | Source Code

## Advanced APIs

### API Documentation

Alert Logic API documentation helps you use  APIs to automate some tasks, such as creating a query for deployments in your account, viewing topological layouts of specified deployments, and creating a query for a list of remediations (groups of exposures). Alert Logic continually expands the API documentation.

[API Documentation](https://console.account.alertlogic.com/users/api/index.html)

### Node.js Developer Environment

Alert Logic built the Alert Logic console entirely against its rich RESTful APIs. The console template places the technology Alert Logic uses to write its interface into your hands.

[Installation Details](https://github.com/alertlogic/al_ui_template/blob/master/README.md) | [Source Code](https://github.com/alertlogic/al_ui_template)
