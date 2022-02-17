# Log Management Best Practices

Compliance requirements drive the need for log management. Regulations and standards require log collection, retention, and access for routine log analysis. You also need complete visibility into the assets you manage in cloud platforms. Routine log analysis can help you with the following security tasks:

* Identify security incidents
* Prevent policy violations
* Monitor and detect fraudulent activities
* Establish performance baselines
* Perform auditing and forensic analysis
* Support internal investigations
* Identify operational trends and long-term problems

Most compliance mandates require that you regularly review collected logs. You must also be able to search those logs, and you must store them in their original format for a specified amount of time.

Hosted and cloud deployments increase the amount of data you manage and the complexity of data management. As the types of data formats and data sources increases, so will the types of log data sources and the volume of data. In addition, your network infrastructure is in a constant state of change, because you constantly add systems, applications, users, and devices.

These challenges require that you implement log management practices that focus on the following:

* Collect the right logs
* Review and analyze log data on a regular basis
* Make log data usable

## Collect the right logs

You should know which logs to collect to achieve your security and compliance goals. Some logs, like operating system logs and application logs, can contain security-related information and information about events. Think about the potential value of each possible log source. Then consider collecting logs that are required for compliance or auditing, as well as logs that help you troubleshoot issues. The following log types provide the best information:

* Anti-malware software logs
* Authentication server logs
* Cloud provider logs
* Firewall logs
* Intrusion prevention systems logs
* Network access control server logs
* Network device logs
* Operating system logs
* Remote access logs
* Vulnerability management software logs
* Web proxy logs

For more details, see [Log Management—Which Logs to Collect](log-management-log-collection.md).

## Ensure logs contain the right information

Your specific security and compliance needs should dictate the information you log and analyze. When you collect logs, be sure they contain the following information:

* User ID
* Date and time for log ons and log offs
* Systems, data, applications, files, and networks accessed
* Failed attempts to access systems, data, applications, files, and networks
* Changes to system configurations and use of system utilities
* Alarms and other security events
* Activity from firewall or antivirus software

## Review and analyze logs 

Log data will not help you achieve your goals if you do not examine it regularly. For compliance purposes, log review and management is a requirement. Many compliance mandates require that you review logs regularly. Each log message contains useful information, like host IP addresses or user names. Each log source includes information that is important for tasks like debugging or troubleshooting.

Linking different log sources for review can be difficult, because those log sources may not contain common values. You could create PERL scripts to search and list only those log messages that match the query. However, the complexity and variety of log sources still limits the ability to meet this challenge.

For more details about log review and analysis, see [Log Management Challenges](log-management-challenges.md).

## Archive logs

You must ensure logs comply with retention and security policies defined in compliance requirements. Because logs can contain sensitive data, you must control access to stored logs and be sure no one can alter it.

Storage of log data from distributed sources across your organization creates a storage management challenge. Purchasing and deploying the required storage consumes valuable space and power (both for operations and cooling). The log data must be managed, backed up, and included in disaster-recovery planning.

For more details about log archival, see [Log Management Challenges](log-management-challenges.md).

## Automated log management

Automated log management solutions provide the following tools to address log management challenges and make the data you collect usable:

* Log collection across various platforms
* Log parsing
* Reports
* Data analysis
* User notifications
* Review of log data for compliance mandates and security best practices.

Your organization must weigh the cost of log management tools and services against the internal staff time required for log management, the cost of non-compliance, data loss, and security incidents.

## Summary

Compliance initiatives often drive the need for log management. Compliance with governing regulations and standards require log collection, retention, and access for forensic analysis. However, log management also provides security- and availability-related benefits.

Log management allows your organization to meet compliance requirements, and it provides benefits for network security and availability. These benefits include improved detection of security incidents, policy violations, fraudulent activities, and operational problems. Logs are also allow you to establish performance baselines, perform auditing and forensic analysis, support internal investigations, and identify operational trends and long-term problems.
