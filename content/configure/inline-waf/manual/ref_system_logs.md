# Logs

The System Logs page includes the following sections. Click on the link to go to the corresponding section to learn more:

<!--<MadCap:menuProxy mc-linked-toc="$topicHeadings" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />-->
To go to the documentation for the previous section of System, see [Interfaces](ref_system_interfaces.md). To go to  the documentation for next subsection in the System section, see [Maintenance](ref_system_maintenance.md).

To access the Maintenance page in the **WAF** management interface, on the left panel, under System, click **Maintenance**.

To save configuration changes or edits you make to any features and options, you must click **Save** on the lower-right of the section or page where you are making changes. Click **apply changes** on the upper-left corner of the page, and then click **OK**. Your changes will not be stored if you do not properly save your changes.

This section displays various log for major system components. Horisontal menu shows the following log options:

The log views auto update regularly.

<colgroup></colgroup>| **              Attack            ** | Attack notifications sent to local Syslog server. |
| **              Audit            ** | Audit log tracking administrative actions. |
| **              Proxy            ** | Warnings and errors encountered in the proxy core components |
| **              Learner            ** | Messages, warnings and errors from the Learner sub system. |
| **              Backup            ** | Warnings and errors encountered during automated configuration backup operations |
| **              WebGUI            ** | Warnings and errors encountered in the management interface. |
| **              Daemon            ** | admd: Administrative daemon warning and error messages. syncd: Warnings and errors encountered during ACL (access control list) synchronization. Only relevant if clustering or fail-over is configured. alertd: Alert daemon warning and error messages. janitor: Messages, warnings and errors from the Log sub system. statsd: Messages, warnings and errors from the statistics sub system. getupdate: Warnings and errors related to automated patch/version download. |
| **              Syslog            ** | Various system log messages. |
| **              Error            ** | All messages sent to Syslog with informational level `error` and above. |
| **Debug** |  |
