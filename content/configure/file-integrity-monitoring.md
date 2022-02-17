# File Integrity Monitoring 

Alert Logic offers File Integrity Monitoring (FIM), which allows you to monitor changes to files and directories of assets associated with your Alert Logic deployments in the Alert Logic console. You can configure monitoring or exclusions for specific file paths or entire directories  in your Windows and Linux systems.

The File Integrity Monitoring Dashboard is only offered to Managed Detection and Response Professional customers. To learn more about Alert Logic subscriptions, see [Get Started with Alert Logic   Subscriptions and Add-ons](../get-started/subscriptions-addons.md).

FIM allows you to be aware of file changes and related details in your deployment. The following are examples of what you can monitor:

* When a file was created and last modified
* Unauthorized access to specific files
* Security permission changes, such as newly added permissions, deleted permissions and changes to existing permissions
* Registry changes, such as changed registry values, removed registry keys and sub keys
* Changes in system binaries and configuration files, and new processes

After you set up FIM, you can schedule a weekly or monthly search of changes to your FIM setups, and be notified when the search is complete. Scheduled searches  can help you keep records of changes to your systems for compliance requirements. For more information about how to schedule a search and access its notifications, see [File Integrity Monitoring Search Notification](notifications/fim-search.md).

The FIM features also help you demonstrate compliance with PCI Requirement  10.5.5 and PCI Requirement 11.5. Alert Logic provides guidance on how to use and access FIM features to demonstrate compliance in the  [PCI Requirement 10.5.5](../analyze/reports/compliance/PCI-requirement-10.5.5.md)  and [PCI Requirement 11.5](../analyze/reports/compliance/PCI-requirement-11.5.md).

You can  view the File Integrity Monitoring dashboard for a summary of your file monitoring activity. For more information see, [File Integrity Monitoring Dashboard ](../analyze/dashboard/file-integrity-monitoring.md).

To access the File Integrity Monitoring page, click the menu icon (![](../Resources/Images/dashboard/menu-icon.png)) from the Dashboards page. Click **Configure**, and then click the deployment for which you want to configure file monitoring. On the left navigation panel, click **File Integrity Monitoring**.

The File Integrity Monitoring page is composed of two subsections: Monitoring and Exclusions. On the **Monitoring** page, you can setup files and directories for monitoring from the default file types listed on the page. In the **Exclusions** page, you can exclude files and directories  from monitoring, which will override a previously configured file monitoring setup.

## Monitoring page

On the **Monitoring** page, you can configure monitoring for default files and directories. You must scope assets that you want monitored for that file or directory path. You do not need to edit or remove the default file paths. After you have applied the asset scoping to the file path, you must enable each file individually to start monitoring.

### Default directories and files

Alert Logic can monitor all default directories and files listed below for GNU/Linux files, Windows files, and Windows Registry. Click the **All File Types** drop-down menu to select a file type for the default directories and files you want to view.

    GNU/Linux Files    * /bin
* /boot
* /etc
* /sbin
* /usr/bin
* /usr/local/bin
* /usr/local/sbin
* /usr/sbin
* /usr/my_custom_filepath
* /usr/share/keyrings
* /var/spool/cron

    Windows Files    * C:\autoexec.bat
* C:\boot.ini
* C:\config.sys
* C:\Program Files\Microsoft Security Client\msseces.exe
* C:\Program Files\My Custom App\customapp.exe
* C:\Windows\explorer.exe
* C:\Windows\regedit.exe
* C:\Windows\system.ini
* C:\Windows\System32
* C:\Windows\win.ini

    Windows Registry    * <windows_registry>HKEY_LOCAL_MACHINE\Software\Classes\batfile</windows_registry>
* <windows_registry>HKEY_LOCAL_MACHINE\Software\Classes\cmdfile</windows_registry>
* <windows_registry>HKEY_LOCAL_MACHINE\Software\Classes\comfile</windows_registry>
* <windows_registry>HKEY_LOCAL_MACHINE\Software\Classes\exefile</windows_registry>
* <windows_registry>HKEY_LOCAL_MACHINE\Software\Classes\piffile</windows_registry>
* <windows_registry>HKEY_LOCAL_MACHINE\Software\Classes\AllFilesystemObjects</windows_registry>
* <windows_registry>HKEY_LOCAL_MACHINE\Software\Classes\Directory</windows_registry>
* <windows_registry>HKEY_LOCAL_MACHINE\Software\Classes\Folder</windows_registry>
* <windows_registry>HKEY_LOCAL_MACHINE\Software\Classes\Protocols</windows_registry>
* <windows_registry>HKEY_LOCAL_MACHINE\Software\Policies</windows_registry>
* <windows_registry>HKEY_LOCAL_MACHINE\Software\Policies\Custom</windows_registry>
* <windows_registry>HKEY_LOCAL_MACHINE\Security</windows_registry>
* <windows_registry>HKEY_LOCAL_MACHINE\Software\Microsoft\Internet Explorer</windows_registry>
* <windows_registry>HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services</windows_registry>
* <windows_registry>HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\Session Manager\KnownDLLs</windows_registry>
* <windows_registry>HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\SecurePipeServers\winreg</windows_registry>
* <windows_registry>HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Run</windows_registry>
* <windows_registry>HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\RunOnce</windows_registry>
* <windows_registry>HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\RunOnceEx</windows_registry>
* <windows_registry>HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\URL</windows_registry>
* <windows_registry>HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Policies</windows_registry>
* <windows_registry>HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT\CurrentVersion\Windows</windows_registry>
* <windows_registry>HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT\CurrentVersion\Winlogon</windows_registry>
* <windows_registry>HKEY_LOCAL_MACHINE\Software\Microsoft\Active Setup\Installed Components</windows_registry>

### Add a  FIM setup

There are two different ways to add a FIM setup. You can click the add icon (![](../Resources/Images/Icons/cdAddPlus.png)), or find the default file or directory from the list for which you want to monitor. After you have filled out all required fields and scoped your assets, you must turn on **Monitor**.

**To add a FIM setup from the add icon**:

1. Click the add icon (![](../Resources/Images/Icons/cdAddPlus.png))
2. In the **Select File Type** drop-down list, select a file type.
3. In the  **Base Directory Path** field, enter the file path that you want to monitor.
4. In the **File Name or Pattern** field, enter the pattern of the files that you want to monitor.
5. Select **Monitor** to enable monitoring for this file or directory.
6. (Optional) In the **Description** field, you can enter more detail for this setup.
7. In the **Asset Scoping** section, click **Search assets** bar to enter the names of the asset you want to monitor, and then select assets to add from the populated options.				
Monitoring is automatically applied to all assets in your deployment. Scoping individual assets for monitoring in this file path will override monitoring for all assets in this deployment.
8. Click **SAVE**.
9. Ensure **Monitor** is turned on for the file you just scoped.

**To add a FIM setup from the list**:

1. Click the **All File Types** drop-down list, and then select a file type to filter the list to its default files and directories.
2. Find the file path you want to scope assets for monitoring.
3. Click **View**, and then click the **Edit**.
4. Ensure **Monitor** is selected to enable monitoring for this file or directory.
5. (Optional) In the **Description** field, you can enter more detail for this setup.
6. In the **Asset Scoping** section, click the **Search assets** bar to enter the names of the asset you want to monitor, and then select assets to add from the populated options.                
Monitoring is automatically applied to all assets in your deployment. Scoping individual assets for monitoring in this file path will override existing monitoring rules for all assets in this deployment.
7. Click **SAVE**.
8. Ensure **Monitor** is turned on for the file you just scoped.

### Duplicate an existing FIM setup

You can use the duplicate feature if you want to copy an existing FIM setup within the same base directory path. You can change the file name or pattern and the asset scoping, but the base directory path must be the same.

The file name or pattern that you want to create a setup for must be under the same base path from the FIM setup that you want to duplicate.

**To duplicate an existing FIM setup:**

1. Click **View**, and then click the duplicate icon (![](../Resources/Images/Icons/duplicate.png)) for the file path or directory you want to copy.
2. Make the necessary changes to the **File Naming or Pattern** field.
3. Ensure **Monitor** is selected to enable monitoring for this file or directory.
4. Make the necessary changes to the description and asset scoping.
5. Click **SAVE**.
6. Ensure **Monitor** is turned on for the file you just scoped.

### Edit an existing FIM setup

To edit an existing FIM setup:

1. Click **View**, and then click the edit icon (![](../Resources/Images/pencil icon.png)) for the file path you want to edit.
2. Ensure **Monitor** is selected to enable monitoring for this file or directory.
3. Make any necessary changes.                 
Monitoring is automatically applied to all assets in your deployment unless you have further scoped individual assets for monitoring.
4. Click **SAVE**.
5. Ensure **Monitor** is turned on for the file you just scoped.

### Bulk edit multiple file paths

You can bulk edit multiple file paths at once to scope assets, or replace assets in scope with other assets.

**To bulk edit multiple file paths**:

1. Click the **All File Types** drop-down list, and then select a file type to filter the list to its default files and directories.
2. Select the check box to bulk select all the files in that file type.
3. At the bottom of the page, click the scope icon (![](../Resources/Images/pencil icon.png)).
4. Under **Selected File Paths**, you can remove file paths that you do not want to edit. You can use the search bar to find assets you want to remove, and then click the remove icon (![](../Resources/Images/Icons/remove.png)).
5. In the **Asset Scoping** section, select **Apply additional assets to the selected file paths** to add more assets to monitor, or select **Replace existing assets with a new asset scope** to remove your existing assets in scope and replace with other assets.					
Monitoring is automatically applied to all assets in your deployment unless you have further scoped individual assets for monitoring.
6. Click the **Search assets** bar to enter the names of the asset you want to monitor, and then select assets to add from the populated options.
7. Click **SAVE**.
8. Ensure **Monitor** is turned on.

## Exclusions page

On the **Exclusions** page, you can add entire directories or specific file paths you want to exclude from monitoring. Your file path or directories exclusions will be listed on this page.

The exclusions you configure override files that are currently being monitored. This allows you to exclude specific files or  sub-directories from an entire directory that you previously configured for monitoring.

To access the  Exclusions page, you can click **NEXT** from the **Monitoring** page, or click **Exclusions** on the left navigation panel.

**To add an exclusion**:

1. Click the add icon (![](../Resources/Images/Icons/cdAddPlus.png))
2. In the **Select File Type** drop-down list, select a file type.
3. In the  **Base Directory Path** field, enter the file path that you want to monitor.
4. In the **File Name or Pattern** field, enter the pattern of the files that you want to monitor.
5. (Optional) In the **Description** field, you can enter more detail for this setup.
6. In the **Asset Exclusions** section, click the **Search assets** bar to enter the names of the asset you want to exclude, and then select assets to exclude from the populated options.                
Monitoring is automatically applied to all assets in your deployment unless you have further scoped individual assets for monitoring. Excluding assets from this file path will override existing exclusion rules for all assets in this deployment.
7. Click **SAVE**.

### Duplicate an existing File Integrity Exclusion setup

You can use the duplicate feature if you want to copy an existing File Integrity Exclusion setup within the same base directory path. You can change the file name or pattern and the asset exclusions, but the base directory path must be the same.

The file name or pattern that you want to create a setup for must be under the same base path from the File Integrity Exclusion setup that you want to duplicate.

**To duplicate an existing File Integrity Exclusion setup:**

1. Click **View**, and then click the duplicate icon (![](../Resources/Images/Icons/duplicate.png)) for the file path or directory you want to copy.
2. Make the necessary changes to the **File Naming or Pattern** field.
3. Ensure **Monitor** is selected to enable monitoring for this file or directory.
4. Make the necessary changes to the description and asset exclusion.
5. Click **SAVE**.
6. Ensure **Monitor** is turned on for the file you just scoped.

### Edit an existing File Integrity Exclusion setup

To edit an existing File Integrity Exclusion setup:

1. Click **View**, and then click the edit icon (![](../Resources/Images/pencil icon.png)) for the file path you want to edit.
2. Make any necessary changes.                 
Monitoring is automatically applied to all assets in your deployment unless you have further scoped individual assets for monitoring. Excluding assets to this file path will override existing exclusion rules for all assets in this deployment.
3. Click **SAVE**.
4. Ensure **Monitor** is turned on for the file you just scoped.

### Bulk edit multiple file paths

You can bulk edit multiple file paths at once to scope assets, or replace assets in scope with other assets.

**To bulk edit multiple file paths**:

1. Click the **All File Types** drop-down list, and then select a file type to filter the list to its default files and directories.
2. Select the check box to bulk select all the files in that file type.
3. At the bottom of the page, click the scope icon (![](../Resources/Images/pencil icon.png)).
4. Under **Selected File Paths**, you can remove file paths that you do not want to edit. You can use the search bar to find assets you want to remove, and then click the remove icon (![](../Resources/Images/Icons/remove.png)).
5. In the **Asset Scoping** section, select **Apply additional assets to the selected file paths** to add more assets to monitor, or select **Replace existing assets with a new asset scope** to remove your existing assets in scope and replace with other assets.					
Monitoring is automatically applied to all assets in your deployment unless you have further scoped individual assets for monitoring.
6. Click the **Search assets** bar to enter the names of the asset you want to monitor, and then select assets to add from the populated options.
7. Click **SAVE**.
8. Ensure **Monitor** is turned on.
