# Authenticated Scanning

Alert Logic allows you to use credentials to perform host-level authenticated scanning. Using Windows or Secure Shell (SSH) credentials as part of your scans allows for more accurate vulnerability scans and lowers the number of false positive results.

## Windows authenticated scanning

Windows authenticated scanning is an authenticated network-based method for interrogating the target machine for missing security-related patches and updates.

To run Windows authenticated scanning, you must set up the following parameters:

* **Credentials**—Alert Logic scanning needs a local or domain administrator account to accurately assess the patch level of your computers.
* **Network access to RPC/WMI, NetBIOS, or SMB/CIFS ports**—Alert Logic scanning requires access to RPC/WMI (135/tcp, 49152-65535/tcp), NetBIOS (139/tcp, 137/udp, 138/udp), or SMB/CIFS (445/tcp adn445/udp). Network or personal firewalls blocking access to any of these protocols will prevent access to Windows patch scanning.
* **Enable Remote Registry services**—The Remote Registry service must be enabled and started. Verify this from the Administrative Control Panel under Services.

If the authentication failed, the scan report will list Exposure ID: 16205 - Local Checks Error.

**To set up a dedicated user for scanning:**

Use the following procedure to set up a dedicated user that Alert Logic can use for authenticated scanning.

1. Click **Start**, type <kbd>lusrmgr.msc</kbd>, and then press **Enter**.
2. Right-click the **Users** folder, and then click **New User**.
3. On the **New User** window:
   1. In **User Name**, type a new user name (for example, <kbd>Alert Logic Dedicated Scanning User</kbd>).
   2. In **Password**, type a password.
   3. In **Confirm Password**, type the password again.
   4. Click **Create**.
5. After the window refreshes, indicating successful user creation, click **Close**.
6. Click the **Groups** folder, right-click **Administrators**, and then click **Add to Group**.
7. On the **Administrators Properties** window, click **Add**.
8. On the **Select Users** window, in **Enter the object names to select**, type the newly created user (for example, <kbd>Alert Logic</kbd>), and then click **Check Names**.
9. After the window refreshes, reflecting any changes and user confirmation, click **OK**.
10. On the **Administrators Properties** window, confirm that the user appears under **Members**, and then click **OK**.
11. Close **lusrmgr**.

**To set up WMI:**

The Alert Logic scanner needs to connect to Windows Management Instrumentation (WMI) on the machine, in addition to remote registry, to pull version information from .dll and .exe files, as well as information stored within Windows Management services and settings. Unlike UNIX and Linux, which come with SSH secure remote access where the system can log on and interrogate things as a user, Alert Logic scanning requires the administrative privileges due to the limitations of methods available to remotely access Windows machines. Alert Logic scanning does not make registry changes and does not write to the machine. To learn more about registry keys, refer to the Microsoft documentation [here](https://msdn.microsoft.com/en-us/library/windows/desktop/ms724878%28v=vs.85%29.aspx).

The Open Vulnerability and Assessment Language (OVAL®) method is the preferred method of network-based patch scanning. The scanner uses the OVAL method for assessing Windows-based machines for a variety of Microsoft-specific and third-party application security patches.

WMI comes installed on all Microsoft operating systems. The following procedure describes how to enable remote access to WMI.

To enable remote WMI requests:

1. On the target server, go to **Administrative Tools**, **Computer Management**.
2. Expand **Services and Applications**.
3. Right-click **WMI Control**, and then select **Properties**.
4. Select the **Security** tab.
5. Click **Security**.
6. Add the scan user (if needed), and then be sure to select **Remote Enable** for the user/group that will be requesting WMI data.

### Further Investigation

If the above steps did not help, Alert Logic recommends installing the WMI Administrative Tools from Microsoft. This includes a WMI browser that will let you connect to a remote machine and browse through the WMI information. That will help to isolate any issues in a more direct and simple environment. When the WMI browser can access a remote machine, Alert Logic should have access as well.

## UNIX/Linux authenticated scanning		

All UNIX and Linux authenticated scanning (security patch scanning) is performed with SSH access using a standard user account.

**UNIX/Linux operating system types**

Alert Logic scanning supports the following operating systems for authenticated scanning:

* Amazon Linux AMI
* CentOS
* Debian
* Fedora
* RedHat
* SuSe
* Ubuntu

Commands used by the UNIX/Linux authenticated scan

* cat
* ls
* pwd
* awk
* sed
* ps
* cd
* echo
* grep
* tail
* head
* uname
* hostname
* exit
* dpkg (debian)
* dpkg-query (debian)
* rpm (linux)

If the authentication failed, the scan report will list Exposure ID: 16205 - Local Checks Error.

## Authenticated scanning in an Amazon Web Services (AWS) environment

For authenticated scans to work properly in your environment, you must set your AWS security groups to allow full access by the scanning appliance. Doing so allows an appliance to communicate with client instances, so the authenticated scan can detect all possible vulnerabilities and configuration issues. Alert Logic installs appliances alongside the instances inside each Amazon VPC.

By default, security groups are set up to allow full communication among group members. If you modify the default settings, authenticated scans may not reflect a full picture of your instance.

### Credential storage

| Type | Encryption type | Notes |
|---|---|---|
| Front end web traffic | TLS 1.2 and AES 256 bit encryption, via HTTPS | User credentials are encrypted using the public key from the  FusionVM server, and only the FusionVM server can decrypt the information. |
| FusionVM back end | RSA and Api call EncryptByAsymKey, 2048 bit key length | Encryption of user passwords and authentication credentials for scanned systems is handled by MS-SQL server. |
| Scanning appliances | RSA and DSA, 2048 bit key length | Encryption by OpenSSH in SSH connections between the Appliance and the FusionVM server. Scanning appliances do not have anything encrypted on the appliances except the password file for appliance login authentication. |
