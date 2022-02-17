# Install the  Remote Collector for Linux

A remote collector collects, compresses, and encrypts log data from the configured remote machines to send directly to Alert Logic. For more information on the system requirements for a remote collector, see [Requirements for the Alert Logic Remote Collector](../requirements/remote-collector.md).

A remote collector can only collect syslog data.

A remote collector is useful because:

* A remote collector can be installed on a Windows machine or a Linux machine.
* A remote collector can be upgraded remotely.
* A remote collector does not require a virtual VMware instance, unlike a virtual appliance.
* Hosts without an agent can send syslog data to Alert Logic via a remote collector.
* Log status is reported directly to Alert Logic.

Data Center deployments only

For Data Center deployments, you must locate and copy your **Unique Registration Key**, which you need to install the remote collector.

Alert Logic uses the Unique Registration Key to specify where the remote collector is located.

To access your Unique Registration Key:

1. In the Alert Logic console, open the relevant Data Center deployment.
2. Under **Configuration Overview**, click **Installation Instructions**.
3. Copy your Unique Registration Key.

You can install the Alert Logic universal agent and syslog remote collector on the same host. This will allow the syslog remote collector to collect forwarded logs, while the universal agent collects local logs and network traffic for Network IDS and audit purposes. This setup ensures that the syslog remote collector host is protected the same way as all your other assets in a deployment.

After you install the syslog remote collector, you must adjust any active network policies (such as SELinux, iptables, and security groups) to allow incoming connections on the port specified in the default syslog remote collector policy. Alert Logic recommends restricting these policies to allow connections only from specific hosts or private networks. For details on configuring SELinux, see [Install the agent](alert-logic-agent-linux.md#installAgent).

## Download a remote collector 

To download the agent, select the link of the desired agent installers:

| Agent Installer | Processor  | Link |
|---|---|---|
| Debian | 32-bit | [Latest syslog remote collector for Linux (32-bit Debian format)](https://scc.alertlogic.net/software/al-log-syslog_LATEST_i386.deb) |
| Debian | 64-bit | [Latest syslog remote collector for Linux (64-bit Debian format)](https://scc.alertlogic.net/software/al-log-syslog_LATEST_amd64.deb) |
| Debian | 64-bit ARM | [Latest syslog remote collector for Linux (64-bit ARM Debian format)](https://scc.alertlogic.net/software/al-log-syslog_LATEST_arm64.deb) |
| RPM | 32-bit | [Latest syslog remote collector for Linux (32-bit RPM format)](https://scc.alertlogic.net/software/al-log-syslog-LATEST-1.i386.rpm) |
| RPM | 64-bit | [Latest syslog remote collector for Linux (64-bit RPM format)](https://scc.alertlogic.net/software/al-log-syslog-LATEST-1.x86_64.rpm) |
| RPM | 64-bit ARM | [Latest syslog remote collector for Linux (64-bit ARM RPM format)](https://scc.alertlogic.net/software/al-log-syslog-LATEST-1.aarch64.rpm) |

## Install the remote collector 

### Install for RPM-based distributions

To install a remote collector:

1. Download the RPM package to the target machine.
2. For Amazon Web Services (AWS) and Microsoft Azure deployments, run the following commands and replace <kbd>&amp;lt;version&amp;gt;</kbd> with the desired version.
   * <kbd>rpm -U al-log-syslog-&amp;lt;version&amp;gt;*.rpm</kbd>
   * <kbd>/etc/init.d/al-log-syslog provision</kbd>
   * <kbd>/etc/init.d/al-log-syslog start</kbd>
4. For Data Center deployments, run the following commands and replace <kbd>&amp;lt;version&amp;gt; </kbd>and <kbd>&amp;lt;UNIQUEREGISTRATIONKEY&amp;gt;</kbd> with the desired version and your Unique Registration Key, respectively.
   * <kbd>rpm -U al-log-syslog-&amp;lt;version&amp;gt;*.rpm</kbd>
   * <kbd>/etc/init.d/al-log-syslog provision --key &amp;lt;UNIQUEREGISTRATIONKEY&amp;gt;</kbd>
   * <kbd>/etc/init.d/al-log-syslog start</kbd>
6. Direct all syslogs to the remote collector on inbound port 1515.
7. If you use an rsyslog daemon, add the following line to rsyslog.conf:
<kbd>*.* @@yourIPaddress:1515;RSYSLOG_FileFormat</kbd>

This configuration will direct your local syslog to the remote collector on TCP port 1515.
8. If you use a syslog-ng daemon, add the following lines to syslog-ng.conf
   * <kbd>destination </kbd>
   * <kbd>d_alertlogic {tcp("yourIPaddress" port(1515));};</kbd>
   * <kbd>log { source(s_src); yourIPaddress(d_alertlogic); };</kbd>
   
   This configuration will direct your local syslog to the remote collector on TCP port 1515.

### Install for Debian-based distributions

To install a remote collector:

1. Download the Debian package to the target machine.
2. For AWS and Azure deployments, run the following commands and replace <kbd>&amp;lt;version&amp;gt;</kbd> with the desired version.
   * <kbd>/etc/init.d/al-log-syslog start</kbd>
   * <kbd>/etc/init.d/al-log-syslog provision</kbd>
   * <kbd>dpkg -i al-log-syslog-&amp;lt;version&amp;gt;*.deb</kbd>
6. For Data Center deployments, run the following commands and replace <kbd>&amp;lt;version&amp;gt; </kbd>and <kbd>&amp;lt;UNIQUEREGISTRATIONKEY&amp;gt;</kbd> with the desired version and your Unique Registration Key, respectively.
   * <kbd>/etc/init.d/al-log-syslog start</kbd>
   * <kbd>/etc/init.d/al-log-syslog provision --key &amp;lt;UNIQUEREGISTRATIONKEY&amp;gt;</kbd>
   * <kbd>dpkg -i al-log-syslog-&amp;lt;version&amp;gt;*.deb</kbd>
10. If you use an rsyslog daemon,  add the following line to rsyslog.conf to configure your syslog device to forward logs to port 1515: <kbd>*.* @@yourIPaddress:1515;RSYSLOG_FileFormat</kbd>
11. If you use a syslog-ng daemon, add the following lines to syslog-ng.conf:
   * <kbd>destination d_alertlogic {tcp("yourIPaddress" port(1515));};</kbd>
   * <kbd>log { source(s_src); yourIPaddress(d_alertlogic); };</kbd>
   
   This configuration will direct your local syslog to the remote collector on TCP port 1515.
