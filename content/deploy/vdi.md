# Virtual Desktop Infrastructure Environments

You can install Extended Endpoint Protection on virtual machines that are part of a virtual desktop infrastructure (VDI) environment.

The two most common VDI setups are:

* VMware Horizon View
* Citrix XenDesktop

Extended Endpoint Protection is only available for the following VDI workstations:

* Windows 7
* Windows 8.1
* Windows 10
* macOS High Sierra
* macOS Mojave
* macOS Catalina

## Deploy Extended Endpoint Protection with VDI

When you install Extended Endpoint Protection on an endpoint, the agent contacts Alert Logic, and Alert Logic assigns the endpoint a unique identifier.  On the **Endpoints** page in the Alert Logic console, you can designate an endpoint as the master image.

### Install on the master

1. Use [these instructions](endpoint-installer.md) to install Extended Endpoint Protection on the master image.
2. Browse to the **Endpoints** page under the **Endpoint Protection** tab in the Alert Logic console.
3. Click the name of the endpoint you want to designate as the master image.
4. Select  the **VDI Master Image** check box to indicate that the endpoint is your master image.

### Create clones

You may take a snapshot at any point after the installation completes. When clones are created from this snapshot, they will each uniquely register into Extended Endpoint Protection when they first boot.

Clones keep their incident and endpoint histories after refreshing or recomposing.

After you create a clone, you can refresh it to its original state or reset it without losing its current identity in the Alert Logic console.
