# Alert Logic Requirements for Virtual and Physical Appliances

## Requirements for Alert Logic IDS virtual appliances

Bandwidth volume directly impacts the ability of the appliance to inspect traffic. High-traffic environments may require a virtual machine with additional processor and memory resources.

The following table describes the basic system requirements to install a  virtual IDS appliance:

| Virtual CPU cores | Components | System Requirements |
|---|---|---|
| 4 cores | RAM | 16 GB |
| Disk space | 40 GB minimum |
| Supported virtual environment | VMware and Hyper-V |
| Encryption | TLS Standard (SSL): 2048-bit key encryption, 256-bit AES bulk encryption |
| Peak supported throughput | 500 Mbps |
| 8 cores | RAM | 32 GB |
| Disk space | 40 GB minimum |
| Supported virtual environment | VMware and Hyper-V |
| Encryption | TLS Standard (SSL): 2048-bit key encryption, 256-bit AES bulk encryption |
| Peak supported throughput | 1 Gbps |
| 16 cores | RAM | 64 GB |
| Disk space | 40 GB minimum |
| Supported virtual environment | VMware and Hyper-V |
| Encryption | TLS Standard (SSL): 2048-bit key encryption, 256-bit AES bulk encryption |
| Peak supported throughput | 2 Gbps (1 Gbps per fiber interface) |

## Physical IDS appliance specifications

Bandwidth volume directly impacts the ability of the appliance to inspect traffic. High-traffic environments require physical appliances with additional power, processor, and memory resources.

Alert Logic provides three tiers of physical appliances to meet system requirements. The following table describes the components and specifications for each appliance:

| Appliances | Components | System Specifications |
|---|---|---|
| Tier 1 - R230XL | CPU | 4 cores |
| RAM | 16 GB |
| Disk Space | 1 TB |
| Chassis | 1U rack mounted |
| Power | 250W |
| Encryption | TLS Standard (SSL): 2048-bit key encryption, 256-bit AES bulk encryption |
| Peak throughput | 500 Mbps |
| Tier 2 - R640XL | CPU | 8 cores |
| RAM | 32 GB |
| Disk Space | 1 TB |
| Chassis | 1U rack mounted |
| Power | 750W |
| Encryption | TLS Standard (SSL): 2048-bit key encryption, 256-bit AES bulk encryption |
| Peak throughput | 1 Gbps |
| Tier 3 - R640XL | CPU | 24 cores |
| RAM | 64 GB |
| Disk Space | 1 TB |
| Chassis | 1U rack mounted |
| Power | 750W |
| Encryption | TLS Standard (SSL): 2048-bit key encryption, 256-bit AES bulk encryption |
| Peak throughput | 2 Gbps (1 Gbps per fiber interface) |

## Physical Log Manager appliance specifications

The following table describes the basic specifications for the physical appliance:

| Components | System Specifications |
|---|---|
| CPU | 4 cores Intel Xeon |
| RAM | 164 GB |
| Disk space | 1 TB 500 GB |
| Chassis | 1U rack mounted |
| Power | 250W |
| Encryption | TLS Standard (SSL): 2048-bit key encryption, 256-bit AES bulk encryption |

## Requirements for Alert Logic Managed Web Application Firewall (WAF) appliances

###  VMware WAF virtual appliance

If your CPU usage is above 80 percent for extended periods, Alert Logic recommends adding processor resources.

The following table describes the basic system requirements to install a VMware virtual appliance:

| Components | System Requirements |
|---|---|
| CPU | 2 CPUs 64 bit |
| RAM | 4 GB |
| Disk space | 250 GB |
| Virtual network interface(s) | An interface with an external IP address for management
An interface with access to the web servers to be protected |
| Encryption / Decryption for SSL traffic | AES-NI CPU instruction set for encryption/decryption of SSL traffic on VMs and host OS is recommended |
| Clustering | For clustering to work, ensure promiscuous mode, forged transmits, and MAC address changes are allowed on the VMware virtual switch (vSwitch) or the port group in the VMware ESX network configuration |

###  Physical WAF appliance capacity

Bandwidth volume directly impacts the ability of the appliance to manage traffic. High-traffic environments may require appliances with additional power, processor, and memory resources.

The following table describes the basic bandwidth limits for the WAF physical appliances:

| Appliances | Throughput | Number of Virtual Hosts | Number of SSL Certificates | Number of Proxies |
|---|---|---|---|---|
| Tier 1 - R410, R220, R230 Tier 1 - R230XL | 0-250 500 Mbps | 1000 | 100 | 200 |
| Tier 2 - R630 Tier 2 - R640XL | 250 500-1000 Mbps | 1000 | 100 | 200 |

###  Physical WAF appliance specifications

The following table describes the basic specifications for the physical appliance:

| Components | System Specifications |
|---|---|
| CPU | 4 cores Intel Xeon |
| RAM | 164 GB |
| Disk space | 1 TB 500 GB |
| Chassis | 1U rack mounted |
| Power | 250W |
| Encryption | TLS Standard (SSL): 2048-bit key encryption, 256-bit AES bulk encryption |

    To learn how in install a virtual or physical appliance, see [Install and Configure the  Virtual Appliance](../prepare/virtual-appliance.md) or[Install and Configure the  Physical Appliance](../prepare/alert-logic-physical-appliance.md).
