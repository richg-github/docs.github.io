# Uninstall Alert Logic Extended Endpoint Protection

You can uninstall Extended Endpoint Protection like most Windows software programs, or you can disable it to temporarily stop the service.

## Retrieve logs

If you plan to contact Support about behavior of Extended Endpoint Protection on a particular machine, Alert Logic recommends that you save the logs from the endpoint. You can collect the logs and then uninstall Extended Endpoint Protection.

Use the Extended Endpoint Protection log collector (.bat) to retrieve the logs: [Download document from the Alert Logic public GitHub](https://github.com/alertlogic/al-endpoint-downloads/blob/master/logcollector.bat)

Retrieving the logs is necessary only if you plan to contact Alert Logic Support.

## Uninstall Extended Endpoint Protection

If you discontinue Extended Endpoint Protection you must remove your agents, or they will attempt to contact Alert Logic, and those connection attempts will fail.

To uninstall Extended Endpoint Protection from your Windows 7 machine:

1. Click the Windows **Start** button, and then select **Control Panel**.
2. Click **Programs**, and then **Programs and Features**.
3. Find Extended Endpoint Protection in the list and select it.
4. At the top of the window, click **Uninstall**.

To uninstall Extended Endpoint Protection from your Windows 10 machine:

1. Click the Windows **Start** button, and then click the settings icon.
2. Click **Apps**.
3. Find Extended Endpoint Protection in the list and select it.
4. Click **Uninstall**.

To uninstall Extended Endpoint Protection from your Mac machine:

1. Open a terminal.
2. Type in the following case-sensitive command: <kbd>sudo sh ./Library/Alertlogic/uninstall</kbd>
3. Enter your pasword. The terminal should confirm that the uninstall was successful.

Though the Alert Logic agent is no longer installed on the endpoint, the endpoint is still available for reporting in the Alert Logic console under **Archived Devices**.

You can also uninstall the agent in bulk using a system management tool.

## Disable Extended Endpoint Protection without uninstalling

To disable Extended Endpoint Protection on an endpoint:

A local administrator can use the Windows Task Manager to stop the Extended Endpoint Protection service.

You can also disable it from the command line by entering:

<kbd>sc config alep_#.#.# start= disabled</kbd>

where #.#.# is the version number, e.g. 2.9.0

To force uninstall Extended Endpoint Protection:

If you need to force uninstall the Extended Endpoint Protection from an endpoint, use this uninstall script (.cmd): [Download document from the Alert Logic public GitHub](https://github.com/alertlogic/al-endpoint-downloads/blob/master/uninstall.cmd).

## Discontinue Extended Endpoint Protection

If you want to discontinue using the Extended Endpoint Protection functionality, you must contact Alert Logic to deactivate your Alert Logic MDR Essentials subscription. In addition, you must remove Extended Endpoint Protection agents from your environment. If you discontinue Extended Endpoint Protection and do not remove agents, they will attempt to contact Alert Logic, and those connection attempts will fail.
