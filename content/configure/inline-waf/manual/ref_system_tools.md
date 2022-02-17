# Tools

The System Tools page includes the following sections. Click on the link to go to the corresponding section to learn more:

<!--<MadCap:menuProxy mc-linked-toc="$topicHeadings" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />-->
To go to the documentation for the previous section of System, see [Logs](ref_system_logs.md). To go to  the documentation for next subsection in the System section, see [Maintenance](ref_system_maintenance.md).

To access the Maintenance page in the **WAF** management interface, on the left panel, under System, click **Maintenance**.

To save configuration changes or edits you make to any features and options, you must click **Save** on the lower-right of the section or page where you are making changes. Click **apply changes** on the upper-left corner of the page, and then click **OK**. Your changes will not be stored if you do not properly save your changes.

Tools for operation, maintenance and support.

### Network tools

#### TCP connect test

Used for network connectivity debugging.

<colgroup></colgroup>| **              TCP connect test            ** Input field | Attempts to establish a connection to the remote on the port specified. If the connection is successfully established, the remote host is considered reachable.<dl><dt>                Valid input              </dt><dd>A valid IP address:port string</dd><dt>                Input example              </dt><dd>`192.168.0.200:80`</dd><dt>                Default value              </dt><dd>`None`</dd></dl> |

#### Network debug

The network debug tool runs tcpdump with the selected options. Tcpdump intercepts packages sent to or from the selected interface and writes packet information to a debug log file which can be viewed in the System : Logs section.

The most common use of this tool is to debug connection issues with either clients or backend web servers.

<colgroup></colgroup>| **              Interface            ** | The interface to intercept traffic to/from. |
| **              Packet count             ** | The number of packets to capture. When the selected number of packets are captured the tool will stop. |
| **              Source/destination IP             ** Input field | Limit packet capturing to a specified source / target IP. To debug problems with a backend server enter that servers IP address. To debug client problems enter the IP address of the client. This value is optional.<dl><dt>                Valid input              </dt><dd>A valid IP address</dd><dt>                Input example              </dt><dd>`10.10.10.88`</dd><dt>                Default value              </dt><dd>`None`</dd></dl> |
| **              Port            ** Input field | Limit packet capturing to a specific port number. This value is optional.<dl><dt>                Valid input              </dt><dd>A valid port number in the range 1-65534</dd><dt>                Input example              </dt><dd>`443`</dd><dt>                Default value              </dt><dd>`None`</dd></dl> |
| **              Verbose            ** Checkbox | Print less protocol information so output lines are shorter. |

#### HTTP backend mass health check 

<colgroup></colgroup>| **              Run            ** |  |
| **View previous results** |  |
| **              Cancel running check             ** |  |

### Reboot and Shutdown

This section allow the system administrator to restart and shutdown Alert Logic Managed Web Application Firewall (WAF).

<colgroup></colgroup>| **              Reboot            ** | Restarts WAF. Click on the button **Reboot** to initiate a restart. Reboot takes approximately 2 minutes depending on the hardware configuration. |
| **              Shutdown            ** | Shutdown Web Security Manager. Click on the button **Shutdown** to initiate a clean shutdown of Web Security Manager™. |

### Technical information for support

This section allow the system administrator to view detail information about the current Web Security Manager system status. This information is typically intended for support cases.

<colgroup></colgroup>| **              System Details            ** | Detailed system information including hardware, network settings and running processes. To get the information, click on the **Download** button. You will be prompted to save the file locally on your computer. |
| **Website configuration** |  |

### License information

Shows current license information including validity and product type.

<colgroup></colgroup>| **              Product name            ** | Name of the product license. |
| **              Major version            ** | Major product version - e.g. 2. |
| **              Serial number            ** | Shows the current applied serial number. This information is important when contacting Alert Logic for technical support. |
| **              Apply new key            ** Input field | Apply new license key. Allows the system administrator to apply a new license key.<dl><dt>                Valid input              </dt><dd>A valid license key</dd><dt>                Default value              </dt><dd>`None`</dd></dl> Type in or paste the new license key and click the **Apply** button for changes to take effect. |
