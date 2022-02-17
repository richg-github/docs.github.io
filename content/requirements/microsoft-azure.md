# Requirements for Managed Detection and Response for Microsoft Azure

## Virtual IDS and Scanner appliance requirements

The following  provides requirement information to install an Alert Logic IDS virtual and scanner appliance in an Azure environment.

### Virtual IDS appliance 

Use the following information to determine your virtual machine size requirements.

#### Throughput calculation

Use the following calculation to get the  virtual appliance throughput requirements. The result of this calculation provides the information you need to determine the correct instance type size to select during the installation procedure.

To calculate throughput requirements:

1. Identify each virtual server that Alert Logic will protect.
2. For the first virtual server to protect:
   1. Log in to the [ Azure portal](https://portal.azure.com/).
   2. Select **Virtual Machines** from the left navigation panel.
   3. Click the virtual server name in the list.
   4. Click **Monitor**.

1. Identify the **Total** utilization for **Network In** and **Network Out**.
2. Add these numbers together. The result is the networking utilization for the first virtual server.
3. Complete these steps for each virtual server that you want Alert Logic to protect.
4. After you calculate the total networking utilization for each virtual server, add these numbers together. The result is the estimated throughput requirement for your virtual appliance. Select your instance type size based on this calculation.

#### Instance type sizes

The following table shows the select compute instance types that Alert Logic runs  in Azure.

| Appliance type | Instance type | Peak supported throughput |
|---|---|---|
| Scanner Only (Essentials) | F2s_v2 | N/A |
| IDS and Scanner | F4s_v2 | 500 Mbps |
| IDS and Scanner | F8s_v2 | 1 Gbps |
| IDS and Scanner | F16s_v2 | 2 Gbps |

### Microsoft Azure endpoints

All virtual machines you create in Azure use a private network channel to automatically communicate with other virtual machines in the same cloud service or virtual network. However, to allow inbound network traffic from Alert Logic, you must add endpoints and Access Control List (ACL) entries to your virtual machine.

For more information, see [Microsoft's documentation about endpoints](http://azure.microsoft.com/en-us/documentation/articles/virtual-machines-set-up-endpoints/).

Alert Logic supports HTTP and HTTPS traffic on alternate ports. For simplicity, these instructions assume the default ports 80 and 443 for HTTP and HTTPS traffic.

Create the following endpoints and ACL entries for Alert Logic in Azure.

| Endpoint | ACL entry | Protocol  | Description |
|---|---|---|---|
| 22 | 204.110.219.96/27 | SSH | Secure shell (Alert Logic primary data center) |
| 22 | 204.110.218.96/27 | SSH | Secure shell (Alert Logic DR data center) |
| 4849 | 204.110.219.96/27 | HTTPS | Appliance management (Alert Logic primary data center) |
| 4849 | 204.110.218.96/27 | HTTPS | Appliance management (Alert Logic DR data center) |
| 443 | 0.0.0.0/0 | HTTPS | HTTPS traffic |
| 80 | 0.0.0.0/0 | HTTP | HTTP traffic |

###  Azure  virtual networks

Alert Logic appliances and Azure web servers must be located in the same virtual network. Since each virtual network is run as an overlay, only virtual machines and services that are part of the same network can access each other. Services outside the virtual network have no way to identify or connect to services hosted within virtual networks, unless specific ACL entries are added for external Internet sources.

### Geo-redundant replication

Enable **Geo-redundant replication** when you set up your Azure environment. With this option enabled, Azure replicates your data to a secondary location within the same region. When you create, update, or delete data in your storage account, the transaction is fully replicated to the secondary location. In the event of a major disaster that affects the primary storage account location, Azure first attempts to restore the primary location. If restoration is not possible, Azure updates the storage account DNS name to point to the secondary location.

### Traffic encryption (Alert Logic Managed Web Application Firewall (WAF))

Alert Logic supports Secure Sockets Layer (SSL) end-to-end encryption (required for HIPAA compliance). If SSL encryption is required all the way to the backend server, configure the appliance to re-encrypt traffic before forwarding it to the server.  You can do this by selecting SSL both for inbound and outbound traffic when configuring the website in the Alert Logic console.

### HTTPS support (WAF)

To support multiple HTTPS websites on one instance, the [Server Name Indication (SNI)](http://en.wikipedia.org/wiki/Server_Name_Indication) option must be used, or you must use a wild-card certificate that covers all websites. Some older unsupported browsers such as Internet Explorer on Windows XP do not support SNI.
