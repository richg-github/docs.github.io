# Install and Configure the  Virtual Appliance

The main use for an Alert Logic virtual appliance is for network IDS analysis and scanning in VMWare deployments.

If you have experience with VMWare management tools and virtual machine installation, you can install a virtual appliance into your environment to collect network traffic and data.

The instructions below are not a complete guide to configure vSphere or virtual data centers. VMWare offers [more information regarding vSphere](http://www.vmware.com/support/).

Data Center deployments only

For Data Center deployments, you must locate and copy your **Unique Registration Key**, which you need to install the appliance.

Alert Logic uses the Unique Registration Key to specify where the appliance is located.

To access your Unique Registration Key:

1. In the Alert Logic console, open the relevant Data Center deployment.
2. Under **Configuration Overview**, click **Installation Instructions**.
3. Copy your Unique Registration Key.

## Download the virtual appliance

Before you download the virtual appliance, review the [virtual appliance](../requirements/appliance-requirements.md) requirements.

| Link | MD5 | Type |
|---|---|---|
| [Latest Virtual Appliance link](https://scc.alertlogic.net/software/threat-virtual-appliance_LATEST.ova) | 146916bbb6c32d0d0f8daacb3cd77ba1 | VMWare image |
| [Latest Virtual Appliance link](https://scc.alertlogic.net/software/threat-virtual-appliance_LATEST.zip) | fe890ca50d7467bebd95bf54a1b35353 | Hyper-V |

| Link | Version | MD5 | Type |
|---|---|---|---|
| [Latest Virtual Appliance link](https://scc.alertlogic.net/software/threat-virtual-appliance_LATEST.ova) | 2.0 | 0dd254c201b71bdb7c251c61b1ad84ec | VMWare image |
|  | 1.9 | b5734be9bed1822283703fa86ee33a2f | VMWare image |
| [Latest Virtual Appliance link](https://scc.alertlogic.net/software/threat-virtual-appliance_LATEST.zip) |  | fe890ca50d7467bebd95bf54a1b35353 | Hyper-V |

## Install the virtual appliance

The appliance is configured with a 40 GB virtual drive.

**To install a virtual appliance with vSphere:**

1. Save the virtual appliance image to your target machine.
2. Import the file into vSphere.
3. Power on the virtual machine.
4. Configure your IP address. To manually assign an address, log into a serial console with the following credentials: setup/7739521
5. In your browser, type: **http://<YourVirtualApplianceIPAddress>**.
6. For Data Center deployments only, in **Unique Registration ID**, paste your unique registration key.
7. Click **Start Claim Process**. A screen appears informing you that your appliance is provisioning. For status details, click **Go To Detailed Status**.
