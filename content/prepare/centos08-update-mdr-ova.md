# CentOS Version 8 Update for MDR Customers using OVA 

CentOS announced the end of life for their version 6 operating system. This means CentOS will no longer provide security patches, vulnerabilities, or bug fixes for version 6. As a result, Alert Logic is helping customers update all Alert Logic appliances running on operating system CentOS version 6 to the current and supported version 8.

As Alert Logic transitions all customers to CentOS 8, Alert Logic will continue maintain necessary security updates for CentOS version 6 to ensure all customers remain secure.

## How to update for MDR customers using OVA image

1. You must install a new appliance for every appliance you are currently running with the new OVA image. See [Install and Configure the Virtual Appliance.](virtual-appliance.md)
2. Check the health of your agents and appliances on the Health page in the Alert Logic console. See [Health](../analyze/health.md).
3. Terminate the old appliance.

## How to update other products

If you are not running an OVA image for your MDR deployments, refer to the links below for specific instructions depending on your subscription and services:

* MDR** customers with **AWS** deployments**: See [CentOS Version 8 Update for AWS MDR Customers](centos08-update-mdr-aws.md) for more details.
* Cloud Defender** or other legacy products customers with **AWS** deployments**: See [CentOS Version 8 Update for AWS Legacy Customers](centos08-update-legacy-aws.md) for more details.
* Cloud Defender**  or other legacy products customer using an OVA image**: See [CentOS Version 8 Update for  Legacy Customers using OVA](centos08-update-legacy-ova.md) for more details.
* Alert Logic Managed Web Application Firewall (WAF)** subscription**: Alert Logic has already contacted you, or will contact you soon, to coordinate a time to update your appliance.
* Threat Manager** subscription**: Alert Logic will contact you soon on the process and details for this transition.

OVA ESXi 6.5 is the lowest supported version, and you will not be able to update to CentOS 8 if you are using an older version.
