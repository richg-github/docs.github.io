# Maintenance

The System Maintenance page includes the following sections. Click on the link to go to the corresponding section to learn more:

<!--<MadCap:menuProxy mc-linked-toc="$topicHeadings" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />-->
To go to the documentation for the previous section of System, see [System](ch_system.md). To go to  the documentation for next subsection in the System section, see [Configuration](ref_system_configuration.md).

To access the Clustering page in the **WAF** management interface, on the left panel, under System, click **Clustering**.

To save configuration changes or edits you make to any features and options, you must click **Save** on the lower-right of the section or page where you are making changes. Click **apply changes** on the upper-left corner of the page, and then click **OK**. Your changes will not be stored if you do not properly save your changes.

This section contains tools for backup, restore and for maintaining disk space.

### Backup and restore

A backup of Alert Logic Managed Web Application Firewall (WAF) contains the current system configuration including configuration, policy and learn data for all website proxies. When restoring from a backup WAF will create all interfaces (including cluster interfaces) as specified in the configuration. As interfaces are identified using their id in the system a full system restore can only be performed on a system with the same types of and at least the same number of interfaces as the system the backup was created on.

#### Best effort - restoring to different platforms

To restore to a hardware platform that is different from the platform the backup was created on enable **Best effort**. WAF will then:

* Create interfaces on the target platform in the same order as they appear in the restore file and will try to ignore errors. If the target platform has fewer interfaces than the platform the backup file was created on the excess interfaces will be skipped and the associated IP addresses (including virtual IPs and VRRP cluster interfaces bound to those interfaces will not be created.
* Bind the management role to all interfaces on the target platform in order to make it easy to access the management GUI on the target platform. It is recommended that management is not bound to interfaces which also has the inbound traffic role.

Note that this may result in errors for website proxies that are bound to specific IP addresses so after a best effort restore it is necessary to go through the process of configuring network interfaces and to go through all website proxies to make sure the configuration fits the new platform.

#### Local backup

When initiating a backup the backup file is stored in the local WAF file system and will appear in the list of backup files. From here it can be downloaded, deleted and selected for fast local restore.

To initiate a local backup click the **Backup button**.

#### Restore

<colgroup></colgroup>| **                Import - File upload              ** | Imports saved system configuration from a file. To import (restore) system configuration previously saved to a file, click on the **Browse** button, select the configuration file and click on the **Upload** button. Enable **Best effort** to skip interface creation and try to ignore errors. Note that this will *overwrite current configuration* including the learn database. |
| **                Import - FTP download              ** | Downloads and imports saved system configuration from FTP. To import (restore) system configuration from file located on an FTP server, enter the complete path to the configuration file located on the FTP server and click on the Download" button. FTP configuration configured under Auto-backup in **System**->**Configuration**. |
| **                Import - SCP download              ** | Downloads and imports saved system configuration from SCP. To import (restore) system configuration from file located on an SCP server, enter the complete path to the configuration file located on the SCP server and click on the Download" button. SCP configuration configured under Auto-backup in **System**->**Configuration**. |

### Website templates list

When a template is created form a website proxy it is saved in the local file system. From here it can be applied directly to a website proxy when it is created or later if desired.

The websites templates list displays the website templates available in the system and allows for download and delete of templates of type Custom.

Templates of type Factory contains the default settings available when creating a website proxy and cannot be deleted or downloaded.

### Databases

The databases list displays the databases in use in the system. The flush button will empty the database.

<colgroup></colgroup>| **                Deny log summary db - all websites              ** | Contains the data displayed in the **Dashboards**+**Deny log** section. |
| **                Learn database - all websites              ** | Contains learn data for all websites. Note that when flushing this database from this page **learn data for all websites will be deleted!**. To flush learn data for a specific website select that website, go to the learning data section and click the **Reset learn data** button. |
| **Traffic stats db - all websites** |  |
| **                Traffic stats db - all websites              ** | Contains the data displayed in the **Dashboards**+**Traffic** section and in the Statistics page for each website proxy. Note that when flushing this database from this page **traffic stats data for all websites will be deleted!**. To flush learn data for a specific website select that website, go to the traffic statistics section and click the **Clear stats** button. |
| **                Website 0 deny log              ** | Each database contains deny log data for a website. The number in the name corresponds to the ID displayed in the left column of the website proxies list in the websites overview page. |

### Access logs list

Displays all access logs currently stored in the system.

Note that access logs can potentially consume a lot of space so it is probably a good idea to download and delete some older access logs.
