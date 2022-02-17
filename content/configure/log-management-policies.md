# Log Management Policies

Alert Logic allows you to create four types of Log Management policies in the Alert Logic console. These policies dictate how Alert Logic collects log messages, and allows you to reuse this common configuration for several log sources of the same type.

* **Flat File policy**: Allows you to collect flat file messages. This is a common log message format for web servers and other server software. For more information about Flat File policies, see [Log Management Flat File Policy](log-management-flat-file-policy.md).
* **Syslog policy**: Allows you to collect syslog messages, which are a way for network devices to send event messages to a logging server—usually known as a syslog server. For more information about Syslog policies, see [Log Management Syslog Policies](log-management-syslog-policies.md).
* **Windows event log policy**: Allows you to collect event log files that track significant events on a Windows server, such as user logins or program errors. For more information about Windows event log policies, see [Log Management Windows Event Log Policies](log-management-windows-event-policies.md).
* **S3 policy**: Sets guidelines for collecting Amazon Simple Storage Service (S3) access logs, which provide details about a single access request, such as the requester, bucket name, request time, request action, response status, and error code. For more information about S3 policies, see [Log Management S3 Policies](log-management-s3-policies.md).

When a universal agent is installed, Alert Logic automatically assigns either a Windows event log or syslog source to each host in your environment. These sources are associated with the default Windows event log policy or the default syslog policy. You can edit the default policies so that the collection settings apply to all newly created event log or syslog sources. Similarly, any new syslog remote collector is associated with the default syslog remote collector policy, which can be edited independently of other default policies.

To access the Log Management policies page, click the menu icon (![](../Resources/Images/dashboard/menu-icon.png)) to see the navigation menu. Click ![](../Resources/Images/dashboard/configure-icon.png)**Configure**, and then click **Log Management**. In the left navigation panel, click **Policies**.

You can check the operational status of  Log Management in the Service Status page in the Alert Logic console. Alert Logic recommends that you subscribe to the Service Status page and all your Alert Logic components, including Log Management. For more information about the Service Status page and how to subscribe, see [Service Status](../analyze/service-status.md).
