# Information

The System Information page includes the following sections. Click on the link to go to the corresponding section to learn more:

<!--<MadCap:menuProxy mc-linked-toc="$topicHeadings" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />-->
To go to the documentation for the previous section of System, see [Configuration](ref_system_configuration.md). To go to  the documentation for next subsection in the System section, see [Interfaces](ref_system_interfaces.md).

To access the Information page in the **WAF** management interface, on the left panel, under System, click **Information**.

To save configuration changes or edits you make to any features and options, you must click **Save** on the lower-right of the section or page where you are making changes. Click **apply changes** on the upper-left corner of the page, and then click **OK**. Your changes will not be stored if you do not properly save your changes.

### System

Displays basic system hardware information.

<colgroup></colgroup>| **              CPU            ** | Number of CPUs detected, CPU speed in gigahertz (GHz) and CPU model. |
| **              BIOS            ** | Information read from server BIOS. |
| **              Memory            ** | Available server (hardware) memory. |
| **              Uptime            ** | Time since the system was last started. |
| **              Localtime            ** | The system time. |

<dl><dt>        CPU model:      </dt><dd>Displays the CPU model.</dd><dt>        CPU speed      </dt><dd>Displays the CPU speed in gigahertz (GHz).</dd><dt>        CPU(s)      </dt><dd>Displays the number of CPU(s) detected.</dd><dt>        Architecture      </dt><dd>Displays the architecture running. Eg. i386/32-bit or amd64/64-bit depending on the Web Security Manager version installed.</dd></dl>### Web Security Manager

basic information about the Web Security Manager platform.

<colgroup></colgroup>| **              Version            ** | Major and minor version information, e.g. `Web Security Manager-2.2.0-i386`. |
| **              Architecture            ** | Architecture running. Eg. `i386/32-bit` or `amd64/64-bit` depending on the Web Security Manager version installed. |

### Devices

Detected devices like network interfaces and disk controllers.

<colgroup></colgroup>| **              Device            ** | The device system id. |
| **              Description            ** | Device manufacturer and name. |

### Disks

System disks available.

<colgroup></colgroup>| **              Disk            ** | The disk id, e.g. `sd0`. |
| **              ID            ** | Disk identification information |
| **              Type            ** | The disk type, e.g. `SCSI`. |
| **              Info            ** | Disk information like size, cylinders, etc. |

### Currently logged in users

The currently logged in users table displays who is logged in to the system management interface.

<colgroup></colgroup>| **              Username            ** | The account username. |
| **              Remote IP address            ** | The remote IP address of the session. |
| **              Last activity            ** | The time when activity was recorded last. |
