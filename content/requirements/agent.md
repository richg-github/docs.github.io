# Requirements for the Alert Logic Agent

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

    To learn how to install the Alert Logic agent for Windows or Linux, see [Install the Alert Logic Agent for Windows](../prepare/alert-logic-agent-windows.md) or [Install the Alert Logic Agent for Linux](../prepare/alert-logic-agent-linux.md). To learn how to install the agent in a virtual container environment, see [Install the Alert Logic Agent Container](../prepare/alert-logic-agent-container.md).
