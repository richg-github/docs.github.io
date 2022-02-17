# Interfaces

The System Interfaces page includes the following sections. Click on the link to go to the corresponding section to learn more:

<!--<MadCap:menuProxy mc-linked-toc="$topicHeadings" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />-->
To go to the documentation for the previous section of System, see [Information](ref_system_information.md). To go to  the documentation for next subsection in the System section, see [Logs](ref_system_logs.md).

To access the Interfaces page in the **WAF** management interface, on the left panel, under System, click **Interfaces**.

To save configuration changes or edits you make to any features and options, you must click **Save** on the lower-right of the section or page where you are making changes. Click **apply changes** on the upper-left corner of the page, and then click **OK**. Your changes will not be stored if you do not properly save your changes.

Each detected network interface is configured in this section.

Configuration parameters are repeated for each interface allowing system administrator to configure one interface at a time. Parameters like IP, network mask, IP aliases, fail-over, etc. Short description of each detected interface is displayed in the sections.

For example, AMD 79c970 PCI and Intel PRO-1000MT.

### IP configuration

IP configuration specific parameters.

<colgroup></colgroup>| **              IP address            ** Input field | System IP address configured for the interface.<dl><dt>                Valid input              </dt><dd>A valid IP address</dd><dt>                Input example              </dt><dd>`192.168.0.200`</dd><dt>                Default value              </dt><dd>`None`</dd></dl> |
| **              Netmask            ** Input field | Network mask of the interface subnet.<dl><dt>                Valid input              </dt><dd>A valid network mask</dd><dt>                Input example              </dt><dd>`255.255.255.0`</dd><dt>                Default value              </dt><dd>`None`</dd></dl> |
| **Gateway** Input field |  |
| **              Description            ** Input field | A description of the interface.<dl><dt>                Valid input              </dt><dd>Any string</dd><dt>                Input example              </dt><dd>`proxy interface`</dd><dt>                Default value              </dt><dd>`None`</dd></dl> |
| **              IP aliases            ** Input field | IP address aliases for the interface.<dl><dt>                Valid input              </dt><dd>IP address separated by new-line</dd><dt>                Input example              </dt><dd>`192.168.0.201, 192.168.0.202`</dd><dt>                Default value              </dt><dd>`None`</dd></dl><dl>IP aliases will not be backed up or load balanced in a Web Security Manager cluster. IP addresses which are served by a cluster are configured in [Clustering](ref_system_clustering.md#ref_system_clustering.md).</dl> |

### Role

Every configured network interface can be assigned different roles. Depending on the number of network interfaces present, roles should be assigned accordingly. It is recommended to assign a dedicated interface for each possible role.

Network interfaces can be assigned the following roles:

<colgroup></colgroup>| **              Inbound traffic            ** Check box | Enable or disable inbound traffic for the interface. If checked, the interface (and all IP addresses attached to it) will respond to inbound HTTP/HTTPS requests from clients. If the selected network interface is exposed to clients, this role should be assigned. Default: `<unchecked>` Alert Logic Managed Web Application Firewall (WAF) will not pass any traffic from clients to back-end servers before at least one network interface is assigned this role. |
| **              Synchronization            ** Check box | Enable or disable `Synchronization` for the interface. If checked, the Interface (only it's system IP address) is used for synchronization. Fail-over must be active (on the same or any other network interface) before synchronization is active. Default: `<unchecked>` |
| **              Management            ** Check box + input. | Enable or disable `Management` for the interface. If checked, the Interface (only it's system IP address) is used for web-based management. The **Management port** sets the port the management server answers.<dl><dt>                Valid input              </dt><dd>An TCP/IP port number</dd><dt>                Input example              </dt><dd>`8080`</dd><dt>                Default value              </dt><dd>`2000`</dd></dl> Management interface is available via HTTPS/SSL on the configured port. Default: `<checked>` |

### DHCP

WAF supports IP assignment through DHCP. This may be desired in cloud environments where it cannot be guaranteed that IPs are persisted across reboots or shutdowns.

When installing the WAF instance, if IPs are assigned through DHCP, WAF will detect it and set the DHCP flag for the interface in question to `on`.

When DHCP is enabled for an interface the IP address of the interface will not appear in IP listings for listen IPs for website proxies but will instead be included in the list option `All inbound/DHCP`. DHCP option can also be enabled for interfaces with the management role bound.

When the DHCP assigned IP changes the WAF automatically adjust the configuration for both website proxies and management daemons accordingly so, since WAF is a server, this option should only be used where there is a system outside of WAF that keeps track of mappings from public IPs to local DHCP assigned private IPs as is the case in cloud environments that rely on DHCP.

<colgroup></colgroup>| **              DHCP            ** Check box | Enable or disable DHCP for the interface. If checked, the interface will get its IP address via DHCP and adjust configuration of proxy and management services accordingly when the IP address changes. Default: If IP address received from DHCP during installation this option will be enabled, otherwise it will be disabled. |

### Media settings

This section allows system administrator to configure network interface media settings like speed and duplex. Normally, a network interface is set to `autoselect` meaning that the speed and duplex settings are automatically negotiated with the uplink switch.

<colgroup></colgroup>| **              Media            ** Drop down list | Media settings. Select the media settings from the drop down menu.<dl><dt>                Valid input              </dt><dd>Supported media settings for the interface is displayed in the drop down menu.</dd><dt>                Default value              </dt><dd>`Autoselect`</dd></dl> |
