<h1>Download and Install the <MadCap:variable name="SDKVariables.CLI" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /></h1><p>This section describes how to download, install, and update the <MadCap:variable name="SDKVariables.CLI" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />, using the Python Package Installer (pip) or a Windows package. After installation, see <MadCap:xref href="first-use.htm" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd">CLI First Use and Validation</MadCap:xref> to authenticate and connect to <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> APIs.</p>

## Prerequisites for Installation

<p>
  <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> built the CLI using the <MadCap:variable name="SDKVariables.SDK" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> for Python.</p>

Installation requires one of the following:

* A compatible Python installation on Linux or macOS, minimum Python version 3.7, or
* A compatible version of Windows (Windows 10, Windows Server 2016, Windows Server 2019)

<h3>Install the <MadCap:variable name="SDKVariables.CLI" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> on Linux or macOS</h3><p>You can install the <MadCap:variable name="SDKVariables.CLI" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> using <a href="https://pip.pypa.io/en/stable/" title="pip - The Python Package Installer" alt="pip - The Python Package Installer">pip</a>, the Python Package Installer.</p>

<p> To install the <MadCap:variable name="SDKVariables.CLI" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> for the current user, run the following command:</p>

```

pip3 install alcli --upgrade --user
```

Sample output:

```

$ pip3 install alcli --upgrade --user
Collecting alcli
Downloading alcli-1.0.28-py3-none-any.whl (14 kB)
Collecting alertlogic-sdk-python>=1.0.28
Downloading alertlogic_sdk_python-1.0.28-py3-none-any.whl (21 kB)
Requirement already satisfied, skipping upgrade: importlib-metadata==1.6.0 in ./Library/Python/3.7/lib/python/site-packages (from alcli) (1.6.0)
Requirement already satisfied, skipping upgrade: configparser==4.0.2 in ./Library/Python/3.7/lib/python/site-packages (from alcli) (4.0.2)
[…]
Installing collected packages: alertlogic-sdk-python, alcli
Successfully installed alcli-1.0.28 alertlogic-sdk-python-1.0.28
```

<p>To install the <MadCap:variable name="SDKVariables.CLI" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> and <MadCap:annotation MadCap:createDate="2021-04-28T09:53:20.0908124-05:00" MadCap:creator="bob.baskin" MadCap:initials="BO" MadCap:comment="may revert" MadCap:editor="bob.baskin" MadCap:editDate="2021-04-28T09:53:24.6287724-05:00" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd">upgrade</MadCap:annotation> system packages, omit the --user option:</p>

```

pip3 install --upgrade --force-reinstall alcli
```

<h3>Download and install the <MadCap:variable name="SDKVariables.CLI" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> on Windows</h3><ol>
  <li>Download the <MadCap:variable name="SDKVariables.CLI" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /><a href="https://github.com/alertlogic/alcli/releases/latest/download/AlertlogicCLISetup.exe" title="Alert Logic CLI executionable installer" alt="Alert Logic CLI executionable installer">.exe</a> or <a href="https://github.com/alertlogic/alcli/releases/latest/download/AlertlogicCLISetup.msi" title="Alert Logic CLI Microsoft Windows installer" alt="Alert Logic CLI Microsoft Windows installer">.msi</a> file.</li>
  <li>Run the downloaded file.</li>
  <li>If you are prompted for User Access Control, click <b>Yes</b> to allow installation.</li>
  <li>Click through the installation wizard using the default settings. </li>
      By default, the installer makes the alcli command accessible from any command prompt, by adding the installation directory to the system execution Path. Uncheck 
      <li>Click <b>Finish</b> to exit the wizard.</li></ol><h2>Upgrade the <MadCap:variable name="SDKVariables.CLI" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /></h2>
Follow the above instructions to upgrade existing installations to the latest version.
