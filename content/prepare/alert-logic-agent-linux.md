# Install the Alert Logic Agent for Linux

Alert Logic provides an agent that gathers data that Alert Logic must collect for analysis, such as log messages and network traffic, as well as metadata and host identification information. You must download the agent, and then deploy it to each host you want to monitor, or collect log messages. Alert Logic provides agents for Windows and Linux hosts. For more information, see [Requirements for the Alert Logic Agent](../requirements/agent.md#reqsAgent).

    If you have Amazon Web Services (AWS) Systems Manager managed instances, you can use [AWS Systems Manager Distributor](https://docs.aws.amazon.com/systems-manager/latest/userguide/distributor.html)     to install the  Alert Logic agent on the instances instead of installing the agent on each host manually. For more information, see [Automate Alert Logic Agent Installation with AWS Systems Manager Distributor](agent-install-automated-aws.md).           
If you have an active IAM or RBAC role (for AWS or Azure, respectively), and configured agents to automatically update, the agent you install automatically assigns itself to the local appliance and you need not enter the Unique Registration Key.

## Download the agent

Linux users can select either Debian-based agent installers or RPM-based installers. Both installers are available in a 32-bit or 64-bit format. To download the Alert Logic agent for Linux, click the agent installer link for the agent you want to install:

| Agent Installer | Processor  | Link |
|---|---|---|
| Debian | 32-bit | [Latest Linux Agent Installer (32-bit Debian format)](https://scc.alertlogic.net/software/al-agent_LATEST_i386.deb) |
| Debian | 64-bit | [Latest Linux Agent Installer (64-bit Debian format)](https://scc.alertlogic.net/software/al-agent_LATEST_amd64.deb) |
| Debian | 64-bit ARM | [Latest Linux Agent Installer (64-bit ARM Debian format)](https://scc.alertlogic.net/software/al-agent_LATEST_arm64.deb) |
| RPM | 32-bit | [Latest Linux Agent Installer (32-bit RPM format)](https://scc.alertlogic.net/software/al-agent-LATEST-1.i386.rpm) |
| RPM | 64-bit | [Latest Linux Agent Installer (64-bit RPM format)](https://scc.alertlogic.net/software/al-agent-LATEST-1.x86_64.rpm) |
| RPM | 64-bit ARM | [Latest Linux Agent Installer (64-bit ARM RPM format)](https://scc.alertlogic.net/software/al-agent-LATEST-1.aarch64.rpm) |

## Install the agent

Alert Logic gives you the option to install the agent with image capture. Alert Logic recommends image capture only when you want to install the agent for the purpose of creating a system image to be used by more than one host in the future. The process of installing for image capture installs the agent but does not assign the host an identity. After you download the agent installer, follow the appropriate procedure below.

    If you have previously installed an older Linux version of an Alert Logic agent, you must uninstall that version before you install the current agent image. For more information, see [Uninstall the Alert Logic Agent for Linux](alert-logic-agent-linux-uninstall.md).    ### **Install the agent **

To install the agent:

1. Copy package to the target machine.
2. If you run SELinux, you must first run the following command: 
<kbd>semanage port -a -t syslogd_port_t -p tcp 1514</kbd>
If the <kbd>semanage</kbd> command is not present in your system, you can install the policycoreutils-python package to obtain the <kbd>semanage</kbd> command. Alert Logic recommends that you consult with your system administrator to verify.
3. Run one of the following commands, based on your distribution:
   * **RPM**: <kbd>rpm -U al-agent-&amp;lt;version&amp;gt;*.rpm</kbd>
   * **Debian**: <kbd>dpkg -i al-agent-&amp;lt;version&amp;gt;*.deb </kbd>
   * **Debian**: dpkg -i al-agent-<version>*.deb
5. (Optional) If you have set up a NAT, virtual appliance, or physical appliance and you want to specify it as a single point of egress for agents to use, run the following command: 
<kbd>/etc/init.d/al-agent configure --host </kbd><kbd>&amp;lt;LOGMANAGERAPPLIANCEIP&amp;gt;</kbd><kbd>&amp;lt;ALAPPLIANCEIP&amp;gt;</kbd>
6. (Optional) If you have set up a proxy, and you want to specify the proxy  as a single point of egress for agents to use, then run the following command: <kbd>/etc/init.d/al-agent configure --proxy &amp;lt;PROXYIP/PROXYHOST&amp;gt;</kbd>
A TCP or HTTP proxy may be used in this configuration.
7. (Optional) For customers who use single point of egress to pass all Internet connectivity of the agent through the Alert Logic appliance, run the following command:
<kbd>/etc/init.d/al-agent configure --host &amp;lt;HOSTIP/APPLIANCEIP&amp;gt;</kbd>
8. For Data Center deployments only, run the following command: <kbd>/etc/init.d/al-agent provision --key &amp;lt;UNIQUEREGISTRATIONKEY&amp;gt;</kbd>
      If you have Data Center deployments, Alert Logic uses the Unique Registration Key to specify where the agent is located. 
To access your Unique Registration Key:   1. In the Alert Logic console, open the relevant data center deployment.
   2. Under **Configuration Overview**, click **Installation Instructions**.
   3. Copy your Unique Registration Key.
12. For image capture on physical machines only, run the following command: <kbd>/etc/init.d/al-agent start</kbd>
13. Do one of the following:
   * If you use an rsyslog daemon 
   add the following line to rsyslog.conf:
   <kbd>*.* @@127.0.0.1:1514;RSYSLOG_FileFormat</kbd>
   This configuration directs your local syslog to the agent on TCP port 1514.
   * If you use a syslog-ng daemon 
   add the following lines to syslog-ng.conf:
   This configuration directs your local syslog to the agent on TCP port 1514.
      * <kbd>destination d_alertlogic {tcp("localhost" port(1514));};</kbd>
      * <kbd>log { source(s_sys); destination(d_alertlogic); };</kbd>
15. Restart the syslog daemon.
16. Verify that the agent has registered with the Alert Logic console.

Agent registration can take several minutes.

### Install the agent with image capture 

**To install the agent with image capture:**

1. Copy the package to the target machine.
2. If you run SELinux, you must first run the following command: 
<kbd>semanage port -a -t syslogd_port_t -p tcp 1514</kbd>
If the <kbd>semanage</kbd> command is not present in your system, you can install the policycoreutils-python package to obtain the <kbd>semanage</kbd> command. Alert Logic recommends that you consult with your system administrator to verify.
3. Run one of the following commands, based on your distribution:
   * **RPM**: <kbd>rpm -U al-agent-&amp;lt;version&amp;gt;*.rpm</kbd>
   * **Debian**: <kbd>dpkg -i al-agent-&amp;lt;version&amp;gt;*.deb</kbd>
5. For Data Center deployments only, run the following command: <kbd>/etc/init.d/al-agent configure --key &amp;lt;UNIQUEREGISTRATIONKEY&amp;gt;</kbd>
      If you have Data Center deployments, Alert Logic uses the Unique Registration Key to specify where the agent is located. 
To access your Unique Registration Key:   1. In the Alert Logic console, open the relevant data center deployment.
   2. Under **Configuration Overview**, click **Installation Instructions**.
   3. Copy your Unique Registration Key.
9. Do one of the following:
   * If you use an rsyslog daemon 
   add the following line to rsyslog.conf:
   <kbd>*.* @@127.0.0.1:1514;RSYSLOG_FileFormat</kbd>
   
   This configuration directs your local syslog to the agent on TCP port 1514.
   * If you use a syslog-ng daemon 
   add the following lines to syslog-ng.conf:
   <kbd>destination d_alertlogic {tcp("localhost" port(1514));};</kbd>
   <kbd>log { source(s_sys); destination(d_alertlogic); };</kbd>
   
   This configuration directs your local syslog to the agent on TCP port 1514.
11. Restart the syslog daemon.
12. Shut down the target machine and save your operating system image.                
Do not start the agent or reboot the image before capturing the image of your virtual machine.
If you start the agent or reboot the image before capturing the image on your virtual machine, the agent reaches out to the Alert Logic backend to be claimed.  Once claimed, the agent host identity is fixed and will be copied to any new instances spun up with this image.  To validate that claiming has not occurred (and ensure that you avoid this problem), go to the Alert Logic console and ensure the agent is not present before cloning the image.
13. (Optional) Start an instance of the saved image and verify that the agent has registered with the Alert Logic console.
If you need to edit your OS image at any point, you must ensure when saving that the Alert Logic agent is *not* registered. You can accomplish this by stopping the agent with:
<kbd>/etc/init.d/al-agent stop</kbd>
Then, if it is present, remove the files:
<kbd>/var/alertlogic/etc/host_crt.pem</kbd>
<kbd>/var/alertlogic/etc/host_key.pem</kbd>
 prior to shutting down and saving the resulting image.

Agent registration can take several minutes.
