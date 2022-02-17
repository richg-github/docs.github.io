# United Kingdom and European Union Firewall Rules

Before installing Alert Logic products, you need to adjust your firewall rules so that data can be securely transferred to and from Alert Logic, along with allowing product updates to occur.

## Communication with Alert Logic Network IDSappliances

### Appliance inbound

Depending on your environment and default firewall rules, additional rules may be required to allow the Alert Logic EU data center to communicate with the Alert Logic appliances.

| Source | Destination | Protocol | Port | Product Function | Description |
|---|---|---|---|---|---|
| Agent(s) CIDR- network subnet range for the agent(s) | Appliance | TCP | 443 | Network IDS | Agent updates, agent routing, log collection |
| Agent(s) CIDR- network subnet range for the agent(s) | Appliance | TCP | 7777 | Network IDS | Agent data transport (between agent and appliance on local network) |
| Accessible CIDR Range/IP Address | Appliance | TCP | 80 | Network IDS | For virtual appliance claim only. Remove the rule after you claim the appliance. |
| 185.54.124.0/24 | Appliance | TCP | 5666 | Network IDS | Appliance monitoring (Debian only) |
| 185.54.124.0/24 | Appliance | TCP | 22 |  | **DO NOT** open port 22 unless an Alert Logic support personnel requests it for troubleshooting or provisioning. |

### Appliance outbound

Depending on your environment and default outbound firewall rules, additional rules may be required to allow the Alert Logic appliances to communicate with the Alert Logic EU data center.

| Source | Destination | Protocol | Port | Product Function | Description |
|---|---|---|---|---|---|
| Appliance | 8.8.8.8 | TCP/UDP | 53 | Network IDS | DNS (default DNS servers, alternative DNS servers can be used) |
| Appliance | 8.8.4.4 | TCP/UDP | 53 | Network IDS | DNS (default DNS servers, alternative DNS servers can be used) |
| Appliance | 0.0.0.0/0 | TCP | 80 | Network IDS | Appliance updates |
| Appliance | 185.54.124.0/24 | UDP | 123 | Network IDS | NTP, time sync |
| Appliance | 185.54.124.0/24 | TCP | 443 | Network IDS | Updates, data transport, and appliance management |
| Appliance | 185.54.124.0/24 | TCP | 4138 | Network IDS | Event transport |
| Appliance | 185.54.124.0/24 | UDP/TCP | All | Network IDS | Debian only |

You may see outbound TCP 443 or TCP 22 connections to public cloud infrastructure. Alert Logic attempts to contact the nearest regional cloud resource, and if that fails, it connects to the standard IP ranges for your assigned data center. The system attempts to use the closest resource first in future connection attempts. Cloud resources are dynamically assigned, and IP addresses are not static.

## Agent or remote collector outbound rules

You must add the following rules to allow agents or remote collectors to communicate with the  EU data center.

| Source | Destination | Protocol | Port | Description |
|---|---|---|---|---|
| Source host | Appliance | TCP | 7777 | Data transport |
| Protected host | 185.54.124.0/24 | TCP | 443 | Agent updates (direct) |
| Protected host | Appliance | TCP | 443 | Agent updates (single point egress) |

You may see outbound TCP 443 or TCP 22 connections to public cloud infrastructure. Alert Logic attempts to contact the nearest regional cloud resource, and if that fails, it connects to the standard IP ranges for your assigned data center. The system attempts to use the closest resource first in future connection attempts. Cloud resources are dynamically assigned, and IP addresses are not static.

## Scanning 

The following outbound firewall rules are required for AWS scanning instances.

| Type | Protocol | Port Range  | Destination | Description |
|---|---|---|---|---|
| HTTP | TCP | 80 | 0.0.0.0/0 | Appliance updates |
| All traffic | All | All | VPC network addresses | Access to scan targets |
| DNS (UDP) | UDP | 53 | 0.0.0.0/0 | DNS |
| DNS (TCP) | TCP | 53 | 0.0.0.0/0 | DNS |
| HTTPS | TCP | 443 | 0.0.0.0/0 | Appliance updates and data transport |

## Alert Logic Managed Web Application Firewall (WAF)

Depending on your environment and default firewall rules, additional rules may be required for the WAF add-on.

### WAF inbound

| Source | Destination | Protocol | Port | Product Function | Description |
|---|---|---|---|---|---|
| 185.54.124.0/24 | Appliance | TCP | 2222 | WAF | Secure shell (AWS Auto Scaling  only) |
| 185.54.124.0/24 | Appliance | TCP | 4849 | WAF | Appliance user interface |
| 185.54.124.0/24 | Appliance | TCP | 22 |  | **DO NOT** open port 22 unless an Alert Logic support personnel requests it for troubleshooting or provisioning. |

### WAF outbound

| Source | Destination | Protocol | Port | Product Function | Description |
|---|---|---|---|---|---|
| Appliance | DNS servers | TCP/UDP | 53 | WAF | DNS |
| Appliance | 0.0.0.0/0 | TCP | 443 | WAF | S3 access (optional for non-AWS customers) |

You may see outbound TCP 443 or TCP 22 connections to public cloud infrastructure. Alert Logic attempts to contact the nearest regional cloud resource, and if that fails, it connects to the standard IP ranges for your assigned data center. The system attempts to use the closest resource first in future connection attempts. Cloud resources are dynamically assigned, and IP addresses are not static.

## Platform-specific information

### AWS marketplace customers

If you select a default security group in the AWS marketplace, AWS automatically configures firewall rules. The default rules are acceptable, but you can change them to the recommended rules.

Outbound firewall rules for AWS pertain only to VPC customers. By default, the outbound rules open any port to any destination.

The CloudFormation template or Terraform template Alert Logic provided to you sets up the firewall rules when it creates your instances.

### Google Cloud Platform customers

The Terraform template that Alert Logic provided to you sets up the firewall rules when it creates your instances in Google Cloud Platform (GCP).

### Azure customers

The Terraform template Alert Logic provided to you sets up the firewall rules when it creates your instances.
