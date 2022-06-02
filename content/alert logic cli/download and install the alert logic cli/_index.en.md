---
title: "Download and Install the Alert Logic CLI"
date: 2018-12-29T11:02:05+06:00
weight: 1
draft: false
---

This section describes how to download, install, and update the Alert Logic CLI, using the Python Package Installer (pip) or a Windows package. After installation, see CLI First Use and Validation to authenticate and connect to Alert Logic APIs.

### Prerequisites for Installation

Alert Logic built the CLI using the Alert Logic SDK for Python.

Installation requires one of the following:

* A compatible Python installation on Linux or macOS, minimum Python version 3.7, or
* A compatible version of Windows (Windows 10, Windows Server 2016, Windows Server 2019)

#### Install the Alert Logic CLI on Linux or macOS

You can install the Alert Logic CLI using pip, the Python Package Installer.

To install the Alert Logic CLI for the current user, run the following command:

```
pip3 install alcli --upgrade --user
```


Sample output:

```
1 $ pip3 install alcli --upgrade --user
2 Collecting alcli
3 Downloading alcli-1.0.28-py3-none-any.whl (14 kB)
4 Collecting alertlogic-sdk-python>=1.0.28
5 Downloading alertlogic_sdk_python-1.0.28-py3-none-any.whl (21 kB)
6 Requirement already satisfied, skipping upgrade: importlib-metadata==1.6.0 in ./Library/Python/3.7/lib/python/site-packages (from alcli) (1.6.0)
7 Requirement already satisfied, skipping upgrade: configparser==4.0.2 in ./Library/Python/3.7/lib/python/site-packages (from alcli) (4.0.2)
8 […]
9 Installing collected packages: alertlogic-sdk-python, alcli
10 Successfully installed alcli-1.0.28 alertlogic-sdk-python-1.0.28
```

To install the Alert Logic CLI and upgrade system packages, omit the --user option:

```
pip3 install --upgrade --force-reinstall alcli
```

#### Download and install the Alert Logic CLI on Windows

1. Download the Alert Logic CLI .exe or .msi file.
2. Run the downloaded file.
3. If you are prompted for User Access Control, click Yes to allow installation.
4. Click through the installation wizard using the default settings.

{{< notice "note" >}}
By default, the installer makes the alcli command accessible from any command prompt, by adding the installation directory to the system execution Path. Uncheck Add to PATH variable if you do not want this behavior.
{{< /notice >}}

5. Click Finish to exit the wizard.

#### Upgrade the Alert Logic CLI

Follow the above instructions to upgrade existing installations to the latest version.