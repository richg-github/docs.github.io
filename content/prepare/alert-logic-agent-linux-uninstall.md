# Uninstall the Alert Logic Agent for Linux

You can uninstall the Alert Logic agent for Linux. If you have previously installed an older Linux version of an Alert Logic agent, you must uninstall that version before you install the current agent image.

## Uninstall an agent RPM package

To uninstall the agent RPM package:

1. Run the following command to locate the agent RPM package: 
<kbd>rpm -qa | grep agent</kbd>
2. Run the following command to uninstall the agent RPM package: 
<kbd>rpm -ev &amp;lt;packageNameFromStep1&amp;gt;</kbd>
3. Run the following command to delete the Alert Logic directory:
<kbd>rm -rf /var/alertlogic</kbd>
4. For instructions to reinstall the agent  RPM package, see [Install the Alert Logic Agent for Linux](alert-logic-agent-linux.md).

## Uninstall an agent Debian package

To uninstall the agent Debian package:

1. Run the following command to locate the agent Debian package: 
<kbd>dpkg -l | grep agent</kbd>
2. Run the following command to uninstall the agent Debian package: 
<kbd>dpkg -r &amp;lt;PackageNamefromStep1&amp;gt;</kbd>
3. Run the following command to delete the Alert Logic directory: 
<kbd>rm -rf /var/alertlogic</kbd>
4. For instructions to reinstall the agent  Debian package, see [Install the Alert Logic Agent for Linux](alert-logic-agent-linux.md).
