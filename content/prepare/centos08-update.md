# CentOS Version 8 Update

CentOS has announced the end of life for their version 6 and 8 operating systems. This means CentOS will no longer provide security patches, vulnerabilities, or bug fixes for these operating systems. As a result, Alert Logic is helping customers update all Alert Logic appliances running on out-of-date operating systems.

Updating to the currently supported operating system requires two steps:

* Step 1 needs to be completed by you, the customer. Update your appliance to CentOS version 8 using the documentation below.
* Step 2 will be completed by Alert Logic and will happen with zero downtime. Once your operating system(s) are running on CentOS 8, we will update your appliance to Alma Linux, which is supported through 2029.

As we transition all customers to Alma Linux, Alert Logic will continue to maintain necessary security updates for virtual CentOS versions 6 and 8 through September 30, 2022, to ensure all customers remain secure.

Physical appliances running CentOS will continue to be supported until Alert Logic begins updating those appliances.

## Prerequisite 

You must be running VMWare ESXi 6.5 or higher before updating the Alert Logic appliance to CentOS 8.

## How to update

The update process varies for each customer, depending on your subscription and service you are using:

* MDR ** customers with **AWS** deployments**: See [CentOS Version 8 Update for AWS MDR Customers](centos08-update-mdr-aws.md) for more details.
* MDR ** customers using an OVA image**: See [CentOS Version 8 Update for MDR Customers using OVA ](centos08-update-mdr-ova.md) for more details.
* MDR** customers with ** Azure **deployments**: See [CentOS Version 8 Update for AWS MDR Customers](centos08-update-mdr-aws.md) for more details
* Cloud Defender** or other legacy products customers with **AWS** deployments**: See [CentOS Version 8 Update for AWS Legacy Customers](centos08-update-legacy-aws.md) for more details.
* Cloud Defender**  or other legacy products customer using an OVA image**: See [CentOS Version 8 Update for  Legacy Customers using OVA](centos08-update-legacy-ova.md) for more details.
* Alert Logic Managed Web Application Firewall (WAF)** subscription**: Alert Logic has already contacted you, or will contact you soon, to coordinate a time to update your appliance.
* Threat Manager** subscription**: Alert Logic will contact you soon on the process and details for this transition.
