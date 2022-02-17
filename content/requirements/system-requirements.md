# System Requirements

## Operating system and browser support

The Alert Logic console supports the current version and the previous major version of the following operating systems:

* Mac
* Linux
* Windows

The Alert Logic console supports the current version and the previous major version of the following browsers:

* Chrome
* Safari
* Firefox
* Microsoft Edge
* Opera
* Internet Explorer

Alert Logic  cannot guarantee that other browsers and versions will work with its products.

## Requirements for the Alert Logic agent

The following table describes the basic requirements to install the agent:

Processors supported by the agent:

* Intel
* ARM

Operating systems supported by the agent:

* **For Windows users:**
   * Windows Server 2003, SP1
   * Windows Server 2008
   * Windows Server 2012
   * Windows Server 2016
   * Windows Server 2019
   * Windows Server 20H2
   * Windows Vista
   * Windows 7
   * Windows 8
   * Windows XP SP1
   * Windows 10
* **For Linux users:**
   * Debian (.deb)
      * 5.x (lenny)
      * 6.x (squeeze)
      * 7.x (wheezy)
      * 8.x (jessie)
      * 9.x (stretch)
      * 10.x (buster)
   * Ubuntu (.deb)
      * 10.x
      * 12.x
      * 14.x
      * 16.x
      * 18.x
      * 20.x
   * CentOS (.rpm)
      * 5.x
      * 6.x
      * 7.x
      * 8.0
   * Red Hat Enterprise Linux (.rpm)
      * 5.x
      * 6.x
      * 7.x
      * 8.x
   * SUSE
      * 12.1
      * 12.0
      * 11.4
      * 11.3
   * Amazon Linux
   * Amazon Linux 2

The following table describes other basic requirements to install the agent:

| Components | System requirements |
|---|---|

| Memory | 96 MB of available memory |
| Disk space for agent | 30 MB of available disk space |
| Disk space for local cache | 500 MB of available disk space |
| Packet access | WinPcap 4.1.2 |
| CPU Utilization | 1-10% depending on log volume |
| RAM | 15 MB minimum |
| Disk space | 30 MB minimum |
| Log collection support | Windows, Flat File |
| Supported environments | Agent-only deployments with virtual and physical appliances, VPC, and Public Clouds |
| Encryption | TLS Standard (SSL): 2048-bit key encryption, 256-bit AES bulk encryption |
| Log collection frequency | At minimum, every five minutes logs are collected and sent to Alert Logic Cloud |
| Host permissions | LocalSystem account has all the necessary permissions by default |

The agent requires DNS access to communicate with the Alert Logic server.

## Requirements for Alert Logic Threat Manager appliances

### Virtual appliance

Bandwidth volume directly impacts the ability of the appliance to inspect traffic. High-traffic environments may require a virtual machine with additional processor and memory resources.

The following table describes the basic system requirements to install a  virtual IDS appliance:

| Virtual CPU cores | Components | System Requirements |
|---|---|---|
| 4 cores | RAM | 16 GB |
| Disk space | 40 GB minimum |
| Supported virtual environment | VMware and Hyper-V |
| Encryption | TLS Standard (SSL): 2048-bit key encryption, 256-bit AES bulk encryption |
| Peak supported throughput | 500 Mbps |
| 8 cores | RAM | 32 GB |
| Disk space | 40 GB minimum |
| Supported virtual environment | VMware and Hyper-V |
| Encryption | TLS Standard (SSL): 2048-bit key encryption, 256-bit AES bulk encryption |
| Peak supported throughput | 1 Gbps |
| 16 cores | RAM | 64 GB |
| Disk space | 40 GB minimum |
| Supported virtual environment | VMware and Hyper-V |
| Encryption | TLS Standard (SSL): 2048-bit key encryption, 256-bit AES bulk encryption |
| Peak supported throughput | 2 Gbps (1 Gbps per fiber interface) |

### Physical appliance

The following table describes the basic specifications for the physical appliance:

| Components | System Specifications |
|---|---|
| CPU | 4 cores Intel Xeon |
| RAM | 164 GB |
| Disk space | 1 TB 500 GB |
| Chassis | 1U rack mounted |
| Power | 250W |
| Encryption | TLS Standard (SSL): 2048-bit key encryption, 256-bit AES bulk encryption |

## Requirements for Alert Logic Log Manager appliances

### Virtual appliance

The following describes the basic requirements to install a virtual appliance:

| Components | System Requirements |
|---|---|
| CPU | 2 cores |
| RAM | 2 GB |
| Disk space | 1 GB–50 GB |
| Supported virtual environment | VMware only |
| Log collection support | Syslog via agent or agent-less, Windows and flat-file  via agent only |
| Encryption | TLS Standard (SSL): 2048-bit key encryption, 256-bit AES bulk encryption |
| Note | Not designed to run in a public cloud environment. Use agent-only deployments instead. |

### System requirements for the remote collector

The following describes the basic requirements to install a remote collector:

| Components | System Requirements |
|---|---|
| CPU | 2 cores |
| RAM | 2 GB |
| Disk space | 10 GB minimum |
| Supported Operating Systems | Windows and Linux |
| Log collection support | Syslog only via port 1515 |
| Encryption | TLS Standard (SSL): 2048-bit key encryption, 256-bit AES bulk encryption |
| Log collection frequency | Every five minutes (minimum)- logs collected and sent to Alert Logic Cloud |
| Host permissions | LocalSystem account has all the requisite permissions by default |

### Physical appliance

The following table describes the basic specifications for the physical appliance:

| Components | System Specifications |
|---|---|
| CPU | 4 cores Intel Xeon |
| RAM | 164 GB |
| Disk space | 1 TB 500 GB |
| Chassis | 1U rack mounted |
| Power | 250W |
| Encryption | TLS Standard (SSL): 2048-bit key encryption, 256-bit AES bulk encryption |

### Multi-tenant appliance

The following table describes the basic requirements to install a multi-tenant appliance:

| Components | System Requirements |
|---|---|
| Customer Support | Physical appliance that can support up to 50 discrete virtual appliances |
| CPU | Intel Xeon |
| RAM | 4 GB DDR3 |
| Disk space | 500 GB |
| Chassis | 1U rack mounted |
| Power | 250W |
| Log collection support | Both agent-based and agent-less Syslog, Agent-only Windows and flat-file  log collection |

### Virtual instance without the agent

The following table describes basic requirements to install a virtual instance without the agent:

| Components | System Requirements |
|---|---|
| Virtual CPUs | 2 |
| Storage | 20 GB |
| Memory | 2 GB |
| Virtual Network Interface(s) | **Virtual network interface(s)** One interface with DHCP or manual IP addressing for management If access to customer assets are restricted from management interface, an additional interface, internal to the customer environment with static access, is required for scanning. VMWare OVF Tool (for more information see [VMware OVF Tool](http://www.vmware.com/resources/techresources/1013)) |

## Requirements for Alert Logic Web Security Manager Premier appliances

### VMware virtual appliance

The following table describes the basic system requirements to install a VMware virtual appliance:

| Components | System Requirements |
|---|---|
| CPU | 2 CPUs 64 bit |
| RAM | 4 GB |
| Disk space | 250 GB |
| Virtual network interface(s) | An interface with an external IP address for management
 An interface with access to the web servers to be protected |
| Encryption / Decryption for SSL traffic | AES-NI CPU instruction set for encryption/decryption of SSL traffic on VMs and host OS is recommended |
| Clustering | For clustering to work, make sure promiscuous mode, forged transmits, and MAC address changes are allowed on the VMware virtual switch (vSwitch) or the port group in the VMware ESX network configuration |

### Physical appliance

The following table describes the basic system requirements to install a physical appliance:

| Components | System Requirements |
|---|---|
| Equipment | 100–250 Mbit |
| CPU | Intel Xeon E3 4 cores |
| RAM | 8 GB |
| Disk space | 500GB |
| Chassis | 1U rack mounted |
| Power | 250W |
| Log collection support | N/A |
| Encryption | TLS Standard (SSL): 1024–2048bit key encryption, 256bit AES bulk encryption |

### Processing Capacity

The following table describes the bandwidth limits for the Alert Logic Managed Web Application Firewall (WAF) physical appliances:

| Appliance type | Throughput | Number of virtual hosts | Number of SSL certificates | Number of proxies |
|---|---|---|---|---|
| Tier 1 - R410, R220, R230 | 0-250 Mbps | 1000 | 100 | 200 |
| Tier 2 - R630 | 250-1000 Mbps | 1000 | 100 | 200 |

## Requirements for Alert Logic Web Security Manager appliances

### Virtual appliance

The following table describes the basic system requirements to install a Web Security Manager virtual appliance:

| Components | System Requirements |
|---|---|
| CPU | 4 virtual CPUs |
| RAM | 16 GB |
| Disk space | 30 GB minimum |
| Supported virtual environment | VMware only |
| Log collection support | N/A |
| Encryption | TLS Standard (SSL): 1024–2048bit key encryption, 256bit AES bulk encryption |

This is the recommended basic configuration for the Web Security Manager product when deployed on a virtual appliance. Bandwidth volume directly impacts the ability of the appliance to inspect traffic. Therefore, high traffic environments may require a virtual machine with additional processor and memory resources.

### Physical appliance

The following table describes the basic specifications for the physical appliance:

| Components | System Specifications |
|---|---|
| CPU | 4 cores Intel Xeon |
| RAM | 164 GB |
| Disk space | 1 TB 500 GB |
| Chassis | 1U rack mounted |
| Power | 250W |
| Encryption | TLS Standard (SSL): 2048-bit key encryption, 256-bit AES bulk encryption |
