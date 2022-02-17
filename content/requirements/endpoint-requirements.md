# Requirements for Alert Logic Extended Endpoint Protection

## System requirements

### Operating systems

Extended Endpoint Protection supports the following operating systems:

* Workstations
   * Windows 7
   * Windows 8.1
   * Windows 10
   * macOS 10.13 - 11.x
* Servers
   * Windows Server 2008 R2
   * Windows Server 2012
   * Windows Server 2016
   * Windows Server 2019

### Hardware

Extended Endpoint Protection supports the following processors:

* 64-bit operating systems running on 64-bit processors
* Windows 7 32-bit operating systems
* Intel processors
* AMD processors

### OS language support

The application supports the following OS-level language settings:

* US English
* UK English
* German
* Spanish

### Memory and disk usage

At steady state, Extended Endpoint Protection uses the following resources:

| 64-bit operating systems | 32-bit operating systems |
|---|---|
| 198MB of memory | 102MB of memory |
| 306MB of disk space | 306MB of disk space |

### Hypervisor compatibility

Extended Endpoint Protectionis supported on guest virtual machines (VMs) powered by most commercial hypervisor providers, such as VMware, AWS, and Azure.

VirtualBox VMs are not currently supported.

## Communication with Alert Logic

All endpoints must have the ability to communicate outbound over TCP connections to the following domains via the defined ports.

### US customers

| Protocol | Port | Destination |
|---|---|---|
| TCP | 443 | https://api.endpoints.alertlogic.com |
| TCP | 443 | https://events.endpoints.alertlogic.com |
| TCP | 443 | https://upgrader.endpoints.alertlogic.com |
| TCP | 443 | https://software.endpoints.alertlogic.com |
| TCP | 443 | https://analysis.endpoints.alertlogic.com |
| TCP | 443 | https://8yv5pue4aa.execute-api.us-east-1.amazonaws.com |
| TCP | 443, 8883, 8443 | a1geuebeh39j2x.iot.us-east-1.amazonaws.com |
| TCP | 443, 8883, 8443 | a1geuebeh39j2x-ats.iot.us-east-1.amazonaws.com |

### UK/EU customers

| Protocol | Port | Destination |
|---|---|---|
| TCP | 443 | https://api.endpoints.alertlogic.co.uk |
| TCP | 443 | https://events.endpoints.alertlogic.com |
| TCP | 443 | https://upgrader.endpoints.alertlogic.com |
| TCP | 443 | https://software.endpoints.alertlogic.com |
| TCP | 443 | https://analysis.endpoints.alertlogic.com |
| TCP | 443 | https://8yv5pue4aa.execute-api.us-east-1.amazonaws.com |
| TCP | 443, 8883, 8443 | a1geuebeh39j2x.iot.eu-west-1.amazonaws.com |
| TCP | 443, 8883, 8443 | a1geuebeh39j2x-ats.iot.eu-west-1.amazonaws.com |

IP addresses used by these services may change regularly. If your firewall does not handle dynamic IP address resolution, then all outbound traffic must be allowed to any destination address in the table above.

## Configuration requirements

### Route traffic through a central proxy server

By default, Extended Endpoint Protection communicates directly to the cloud outside a browser. This means  Extended Endpoint Protection does not benefit from any configured browser-side proxy settings. To accommodate routing Extended Endpoint Protection traffic through a central proxy server, Extended Endpoint Protection looks for a registry value where you can assign the address of a target proxy server. You can manually write this value through Group Policy.

Network Proxy support is offered in two modes: Automatic and Manual configuration.

#### Automatic Configuration

Extended Endpoint Protection supports routing network traffic through unauthenticated central network proxies. The Extended Endpoint Protection agent detects if the local machine is configured to route through a local network proxy, and inherits those settings to direct its traffic appropriately.

#### Manual Configuration

If desired, you can manually configure a local machine to route the Extended Endpoint Protection agent traffic to a defined network proxy. Use manual configuration if the endpoint is not configured to use a proxy, but you still wish to send the agent network traffic through a central proxy server.

To route traffic through a target server:

To accommodate manually routing traffic through a central proxy server, Extended Endpoint Protection looks for a specific Windows registry value that you can assign to the address of a target proxy server. You can manually write this value through Group Policy.

1. Browse to the registry located at HKEY_LOCAL_MACHINE\SOFTWARE SOFTWARE\Alert Logic\Extended Endpoint Protection
2. Create a new String Value:
   * Name it "Proxy"
   * Set the string value as the URI of your proxy server and port. For example, <kbd>http://192.168.100.100:8888</kbd>

#### Additional proxy implementation notes and requirements:

* Only HTTP is supported as the protocol for the proxy server URI, and HTTPS is used between the endpoint and portal. Proxy connections are unauthenticated.
* If the endpoint is behind an HTTP proxy, then configure the HTTP proxy server to allow tunneling (HTTP CONNECT method) on port 8883. This is necessary to enable the endpoint agent to securely communicate with Amazon IoT.
* The proxy setting is global and applies to all users and all network connections  (WiFi, wired, VPN, etc.). If the end user moves the machine to a new network where the proxy is not accessible, the   connection will break.
* If you update or remove the proxy, you must change the registry setting, and then restart the  Extended Endpoint Protection service or reboot the computer.

### Add certificates to the system root store

Extended Endpoint Protection automatically trusts SSL deep inspection proxies with certificates stored on the local machine in the Trusted Root Certification Authorities certificate store. If the proxy certificate is not already stored, you must add it to support  connectivity through this proxy.

### Whitelist Alert Logic processes

All Alert Logic processes must be allowed to execute. While Extended Endpoint Protection tests for compatibility with operating systems, you may need to whitelist Extended Endpoint Protection with other antivirus and Endpoint Detection and Response (EDR) vendors. Norton by Symantec is known to require approval, but other vendors may also.
