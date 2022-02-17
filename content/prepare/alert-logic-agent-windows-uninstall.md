# Uninstall the Alert Logic Agent for Windows

You can uninstall the Alert Logic agent for Windows by using Control Panel or a command prompt.

## Uninstall the agent by using Control Panel

To uninstall the agent  by using Control Panel:

1. Open the Services App:
   1. To open the Run dialog box, press the Windows logo key, and then press **R**.
   2. Type "services.msc" in the **Open** field.
   3. Press **Enter**.
3. Stop the Alert Logic  agent service:
   1. Right-click **AL Agent**.
   2. Click **Stop**.
5. Delete the agent folder:
   1. In Windows Explorer, browse to C:\Program Files\CommonFiles.
   2. Delete the **Alertlogic** folder.
7. Uninstall the Alert Logic agent:
   1. In Control Panel, click **Uninstall a program**.
   2. Right-click **AL Agent**, and then click **Yes** to confirm uninstall.
9. Verify that the registry entry is deleted:
   1. In the Run dialog box, type "cmd" in the **Open** field.
   2. Hold down **Ctrl** + **Shift**, and then press **Enter**.
   3. Run the following command in the administrative command prompt: 
   <kbd>reg delete %SOFTWARE%\AlertLogic\agent\host_uuid</kbd>
11. For instructions to reinstall the Windows agent, see [Install the Alert Logic Agent for Windows](alert-logic-agent-windows.md).

## Uninstall the agent by using the command prompt

To uninstall the agent by using the command prompt:

1. Open the administrative command prompt:
   1. To open the Run dialog box, press the Windows logo key , and then press **R**.
   2. Type "cmd" in the **Open** field.
   3. Hold down**Ctrl** + **Shift**, and then press **Enter**.
3. Run the following commands to stop the Alert Logic agent: 
<kbd>sc stop al_agent</kbd>
4. Run the following commands to remove the .pem files: 
<kbd>del %ProgramFiles%\CommonFiles\Alertlogic\host_crt.pem</kbd>
<kbd>del %ProgramFiles%\CommonFiles\Alertlogic\host_key.pem</kbd>
5. Run the following command to uninstall the agent: 
<kbd>wmic /node:%COMPUTERNAME% product where name="AL Agent" call uninstall /nointeractive</kbd>
6. For instructions to reinstall the Windows agent, see [Install the Alert Logic Agent for Windows](alert-logic-agent-windows.md).
