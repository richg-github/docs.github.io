# Updates

The System Updates page includes the following sections. Click on the link to go to the corresponding section to learn more:

<!--<MadCap:menuProxy mc-linked-toc="$topicHeadings" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />-->
To go to the documentation for the previous section of System, see [Maintenance](ref_system_maintenance.md). To go to  the documentation for next subsection in the System section, see [Users](ref_system_users.md).

To access the Updates page in the **WAF** management interface, on the left panel, under System, click **Updates**.

To save configuration changes or edits you make to any features and options, you must click **Save** on the lower-right of the section or page where you are making changes. Click **apply changes** on the upper-left corner of the page, and then click **OK**. Your changes will not be stored if you do not properly save your changes.

Alert Logic Managed Web Application Firewall (WAF)checks for available updates every hour and automatically downloads available updates. When updates are available for installation a notification email is sent to the `system contact`.

### Signatures        

#### Current signature version

<colgroup></colgroup>| **              ID            ** | Unique update identifier. |
| **              Info            ** | Brief update description. |
| **              Size            ** | Size of the update. |
| **              Date            ** | Update creation date. |
| **              Install            ** Check box | Select update for installation. |

##### Installing updates

To install available updates, check the **Install** box right to the particular update on the list, and then click the **Install**.

All updates are required and updates can only be installed in sequential order.

#### Installed updates

Displays already installed Web Security Manager updates.

<colgroup></colgroup>| **              ID            ** | Unique update identifier. |
| **              Info            ** | Brief update description. |
| **              Date            ** | Update creation date. |

### Software updates        

#### Updates available for installation

Displays available WAF updates that are ready for installation.

<colgroup></colgroup>| **              ID            ** | Unique update identifier. |
| **              Update name            ** | Update name information. |
| **              Info            ** | Brief update description. |
| **              Size            ** | Size of the update. |
| **              Date            ** | Update creation date. |
| **              Install            ** Check box | Select update for installation. |

##### Installing updates

To install available updates, check the **Install** box right to the particular update on the list and click the **Install** button.

All updates are required and updates can only be installed in sequential order.

#### Installed updates

Displays already installed WAF updates.

<colgroup></colgroup>| **              ID            ** | Unique update identifier. |
| **              Update name            ** | Update name information. |
| **              Info            ** | Brief update description. |
| **              Date            ** | Update creation date. |

### Configuring for updates

In order for the automated update system to work, you need to specify an admin contact email address and configure a DNS-server in:

**        System      **->**Configuration**

When updates are ready a notification is sent to the admin contact email address.

WAF needs to be able to initiate the following outbound connections:

<dl><dt>        updates.alertlogic.com port 80 tcp      </dt><dd>Querying of available updates.</dd><dt>        updates.alertlogic.com port 8080 tcp      </dt><dd>Download of available packages.</dd></dl>
Make sure that these connections are allowed in the network firewall.
