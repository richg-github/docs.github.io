# Alert Logic Scanning Technical Description

## Host discovery

Host discovery determines if a computer or IP address is active. Host discovery scans detect legitimate hosts and determines empty address ranges to avoid unnecessary traffic. The ASV scan solution is for the PCI requirement to perform host discovery which makes a reasonable attempt to identify live systems that include live systems that do not respond to ICMP echo (“ping”) requests. To learn more about this requirement, see the [PCI ASV Program Guide](https://www.pcisecuritystandards.org/documents/ASV_Program_Guide_v2.pdf),

Alert Logic defines  the following as reasonable attempts to connect with the target:

* **ICMP echo (ping)—first attempt**: A ping sweep sends an ICMP message to each address.
* **ICMP echo (ping)—second attempt**: If there is no answer  received on the first attempt, a second ICMP ping is made.
* **ICMP timestamp**: ICMP timestamp requests are made.
* **Test top 22 TCP ports**: (21, 22, 23, 25, 53, 80, 110, 111, 135, 139, 143, 443, 445, 993, 995, 1723, 3306, 3389, 5900, 8080, 8400, 49154) Alert Logic sends a TCP ping to commonly used ports. TCP pings use a deviation of the TCP standard three-way handshake to determine if a computer responds. This method sends an unsolicited TCP Acknowledge (TCP ACK) to the specified port. If an active computer listens on this port, it sends back a reset to the unsolicited request. Another method involves sending a TCP Synchronize (TCP SYN) message (similar to the TCP ACK) to the commonly used ports and looking for a response.
* **Test top 12 UDP ports**: (53, 69, 111, 123, 137, 138, 161, 177, 445, 500, 1900, 4500) The most common UDP ports are tested for response.
* **"Port Closed" responses**: An active host sends a response to indicate a port is closed.

In isolated cases, these methods may not detect all hosts. Alert Logic recommends that you enable ICMP echo (ping) or ICMP timestamp as a signal to the Alert Logic scanner.
## Port scan

The port scan segment of the scanning process is split into two parts: the TCP port scan and the UDP port scan. Alert Logic uses full connect scans on both types of ports.

### TCP port scan

1. The scanner makes a connection to the target server through each port in the scan policy.
2. The scanner executes a full RFC compliant TCP/IP handshake.
3. Each port gives one of the following responses:
   * **Port open**: These ports are examined further in the next step of the scan process.
   * **Port closed**: These ports are ignored for the remainder of the scan.
   * **No answer or dropped packet**: These ports are blocked by a network firewall or host based firewall.

### UDP port scan

1. The scanner attempts to make a connection to the target server through each port in the scan policy.
2. The scanner waits the maximum amount of time for each port.
3. The scanner labels each port as open or filtered.                
UDP ports do not always send responses even if they are open, which is why sometimes the scanner labels open ports as filtered.

UDP ports take longer to scan than TCP ports. If you want to scan more than the list of common ports, you must enter a custom port list.

### Lite discovery scan

The standard discovery scan has no adverse impacts in most environments. For networks Data Center deployments with certain firewall or proxy configurations, Alert Logic recommends a lite option that scans fewer UDP ports.

## Service detection

After the port scan finds open ports, the service detection segment of the scan identifies which services are running on the port. The scanner searches all open ports for known services, in case services are running on non-standard ports. The following are the procedures that detect services running on all open ports:

1. The scanner sends traffic to ports that use various protocols and records those  responses:
   * TCP ports: The scanner sends specific queries to the port until it receives a recognizable response.
   * UDP ports: UDP ports without connection errors are inferred to be open, which means the UDP service detection is slow and unreliable. Many systems filter out ICMP error messages, or only send a certain number of error messages per second.
3. The scanner analyzes each response received and determines which type of service sent the response.

## Version detection

The version detection segment of the scan attempts to identify the following items for the port:

* Version numbers for each service on the port
* Applications running on the service
* Third-party plug-ins
* Security patches

The version detection segment  of the scan is done in two steps. The scanner runs the [Nmap service and version detection](https://nmap.org/book/man-port-scanning-techniques.html), and then runs proprietary Alert Logic service and version detection. Results from the two steps are then combined into a comprehensive list of software, versions, and patches.

## Vulnerability evaluation

In the vulnerability evaluation phase, Alert Logic compares the software, version, and patch list to its vulnerability database. The database includes over 70,000 vulnerable versions and their associated vulnerabilities. The scanner matches the software list with the vulnerability database and provides clients with a list of vulnerabilities that may be present in their environments.

## Assessment scope

The following is a sample list of services, devices, and operating systems that Alert Logic tests:

### Operating systems

* Linux
* Microsoft® Windows®

### Web servers

* Apache
* Microsoft® IIS

### Web application servers

* Apache Jakarta Tomcat
* JBOSS

### Common web script

* Commonly found scripts (typically, common gateway interface CGI scripts) written in various languages
* Ecommerce-related scripts, such as shopping carts and CRM scripts
* ASP
* PHP

### Database servers

* Microsoft SQL Server™
* MySQL®
* Oracle®
* PostreSQL

### Mail servers

* Microsoft® Exchange
* SendMail™

### Firewalls

* Cisco PIX®
* NetScreen

### Routers

* Cisco

### Common services

* Domain name system (DNS)
* File transfer protocol (FTP)
* Simple mail transfer protocol (SMTP)

### Router check

The router check tests the router for known vulnerabilities and configuration issues in the firmware.

### Firewall check

The firewall checks are to check for up-to-date patches on known vulnerabilities, and open ports that indicate inadequate configuration.

### Operating system check

Vendors release patches to address new exploits and flaws. The operating system checkverifies that the operating system has the latest patches installed.

### Database check

New exploits are found regularly for database products. The database check detects exploits and open access to databases.

### Web server check

The web server check tests for all known vulnerabilities, exploits, and configuration issues on web servers. The web server check  discovers new exploits routinely in web server products. The web server check detects and reports known exploits. The web server check also checks for other best practices, such as ensuring that directory browsing is not possible on the server.

## Complex passwords

Alert Logic supports complex passwords, but some special characters give command line interfaces difficulty, as they have special meanings. Keep your password special characters limited to numbers (0-9), periods (.), colons (:), semi-colons (;), quotes (',',","), percentages (%), and spaces ( ).

## Scanning depth

Alert Logic scanning enables safe and accurate assessments without affecting network operations. If the system finds an open SNMP service, it polls as much information as possible (true operating system, real hostname, patch level), but does not attempt to exploit holes to demonstrate what an attacker can do.

## Backporting

Backporting involves applying a software patch to an older version of the software than the version it was designed to modify. Backporting is specific to some UNIX/Linux and open source vendors. To learn more, see [Red Hat about backporting security fixes](https://access.redhat.com/security/updates/backporting).

If you use zero privileged level of network scanning, then Alert Logic scanning provides the option to [ignore a vulnerability](../analyze/manage-scans-results.md#ignoreVulnerability), which documents the presence of your vendor-supplied patch and suppresses further reporting of this issue on those IP addresses. You can export the list of ignored vulnerabilities as a report to give to other auditors the documented fixes for supposed network vulnerabilities. Network scanners report based on the found version, and auditors expect all vulnerabilities to be enumerated and exceptions to be documented.

The best way to handle backported patches is to do credentialed scans. The preferred method for handling credentialed scans is for Alert Logic to use the OVAL algorithm and data feeds directly from RedHat and other Linux vendors. When you run scans with credentials, the system automatically enumerates the list of installed patches and auto-suppresses vulnerabilities that backported patches addressed. Alert Logic scanning can do this internally and externally from the internet, but it requires standard user access to a Secure Shell (SSH) service on that computer.

When a network vulnerability scanner assesses a computer, it bases some of its findings on found versions of software. If these versions are known to be vulnerable to certain issues, they are enumerated as vulnerable to their respective CVEs. If your vendor backports security fixes and does not update the software version number, you may not be vulnerable despite what the Alert Logic vulnerability report states.

## Scanning system details

### SSL certificate host name discrepancy

This vulnerability appears in a report when the listed name in the SSL certificate configuration does not match the name used to access the host. This is an automatic failure for external PCI assessment scans due to the inability to verify the legitimacy of the host.

This vulnerability commonly appears when an administrator reuses an SSL certificate from one web application for another. For example, an SSL certificate created for www.mydomain.com cannot be used for mypage.mydomain.com.

#### Mitigation

Use the mitigation methods listed below to address this vulnerability:

* External sites
   * Purchase a new SSL certificate created specifically for your web application.
   * Use a wildcard SSL certificate for any page on the domain.
* Internal methods
   * Update the reverse DNS record of the IP address to the same subject of the SSL certificate.  The scan automatically detects the reverse DNS name and if it matches the SSL certificate subject, the issue is not flagged.
   * Update the SSL Certificate subject line to match the host name of the device.
* Other methods
   * If the scanner is unable to resolve a host name for the host, it is typically related to the configured DNS servers not having a record of the host.
   * If the certificate is not valid because it is a generic or default self-signed certificate, you can choose to filter the vulnerability at the IP or job level. If the certificate provides a host name (or lack thereof) that does not match the host name discovered during scanning, this is a valid finding. Filtering this vulnerability is at the discretion of the client only.

#### False positives

**False positive in external or internal scan**

If the scan result is a false positive, you can make the exposure inactive to remove the results from reports.

**False positive in PCI scan**

In many cases, the SSL certificate host name discrepancy appears because the host is scanned via an IP address instead of a fully qualified domain names (FQDN). PCI-DSS requires customers to supply FQDNs in addition to providing all external-facing IP addresses and all other unique entryways into applications for the entire in-scope infrastructure.

If you deploy load balancers, the scan may only see part of the configuration behind the load balancer. In these cases, the following applies:

* Localized load balancers: You must supply documentation showing that the infrastructure behind the load balancer(s) is synchronized in terms of configuration.
* External load balancing services: Implement a configuration to ensure that all IP addresses and ranges provided are successfully scanned.

If you believe that a PCI assessment failure was in error, first verify that the FQDN resolves to the host using an outside source such as [www.sslshopper.com](http://www.sslshopper.com/) or [www.digicert.com/help](http://www.digicert.com/help/). These sources may also identify other certificate problems.

**PCI scan disputes**

If the FQDN resolves to the host, you may submit a [PCI Scan Disputes](../configure/pci-scan-dispute.md). Provide the FQDN in the dispute comment so that Alert Logic can validate the certificate. Enter only one FQDN per host. A single dispute comment containing a blanket statement for all hosts found in the scan is not acceptable. In the case of a load balancer, provide all expected IP resolutions of the FQDN and confirm that hosts behind the load balancer are in sync.

In general, using the FQDN in the scan configuration prevents this vulnerability from appearing.

### Brute force user name and password guessing

Alert Logic scans performs some user name and password guessing, but it does not perform an all-out brute force attempt against accounts. Many devices come with default administrative account names, and the system checks for standard user name/password combinations such as:

* 3Com hubs/switches default logon—manager:manager
* Windows Network—administrator:administrator or administrator:blank
* MS-SQL—sa:blank

Alert Logic scans does not perform straight brute force attempts against logins, as there is too great a risk of locking out accounts caused by a denial-of-service situation.

### Denial-of-service attacks and buffer overflows

Alert Logic does not run any test that can cause significant or fatal damage to a system or application. Alert Logic can test some buffer overflow and denial-of-service (DoS) vulnerabilities without harming your server or service. Strict quality assurance measures ensure tests are safe before release. It is impossible to test for all configuration possibilities and it is difficult to completely rule out any disruptions.

For vulnerabilities that require a non-active testing method, the Alert Logic scanning system deploys a passive scan operation that uses versioning, configuration testing, and inference to determine the likelihood of the existence of a vulnerability. Vulnerabilities that cannot be completely verified are stated as warnings, with associated detail to evaluate mitigation strategies for that issue.

#### Denial-of-service situations

Alert Logic identifies two scenarios in which active testing can cause a DoS situation on a network.

* **Consumption of firewall connections/exhaustion of firewall resources**
If an internal  appliance is placed behind a firewall and instructed to scan computers on the other side of the firewall, the appliance can exhaust the available outbound connections/resources of the firewall. This happened on Cisco PIX firewalls where port address translation (PAT) was used to PAT private, internal addresses to the outside interface. During the port scanning phase of the scan, a large number of connections are initiated to identify all open ports on a target device.
To avoid this scenario, place the appliance on a segment of the network where it does not have to go through the firewall to reach the target. Then provide a static IP translation for the IP address of the testing unit. This reduces the number of connections the firewall must "remember" during testing.
* **Debug level logging/religious logging**
An appliance performing a high level of logging can cause a DoS situation. This happened in both internal and external testing. This scenario is a classic security vulnerability. If a firewall logs every connection attempt to a remote system, it can generate gigabytes of log file traffic, which  causes a strain on network infrastructure and exhausts file system resources of the remote logging console. A strained network infrastructure and exhausted file system resources are known problems with debug-level logging (i.e., logging everything). When a port scan is performed, the number of connections to a device can range from 1,500/3,000 ports connection attempts up to 65,535/131,070 ports connection attempts. To prevent a DoS situation, use a lower level of logging.

### Scans and network performance

The Alert Logic scan engine includes the following features designed to protect network performance:

* Designed and tested active scan tools that are sensitive to network operations
* Passive asset profiling that do not require an active test
* Scan job configuration options (see [Adjust Scan Settings](../analyze/manage-scans-and-results/adjust-settings.md))
* Schedule configuration options (see [Manage Scan Schedules](../analyze/manage-scans-and-results/schedules.md))
* Bandwidth limits on scan jobs (see [Adjust Scan Settings](../analyze/manage-scans-and-results/adjust-settings.md))
* Custom configuration for more light or heavy port scanning (see [Manage Scan Schedules](../analyze/manage-scans-and-results/schedules.md))
* Option to exclude IP addresses for devices that may not respond well to scanning (see [Exclude assets and ports from scans](../analyze/manage-scans-and-results/schedules.md#Excludeassetsfromscans))
* Flexible scheduling to ensure scan activity occurs only during approved times (see [Manage Scan Schedules](../analyze/manage-scans-and-results/schedules.md))

### Load-balancing devices

If your environment has a web farm behind a load-balancing device, not all devices are assesed, because the load-balancing device creates the algorithm that determines load distribution. Alert Logic can find issues in your code base, but load-balancing device makes decisions that can miss computer-specific issues.

To ensure that Alert Logic scans each device, place an appliance where it reaches the individual computers in the web farm.

### Operating systems

Alert Logic scanning generally tests for any operating system that supports a TCP/IP stack, but results vary among operating systems. DOS and Windows 3.1 WFWG support TCP/IP, but few known vulnerabilities exist for these systems.

Alert Logic does not rely on operating system guessing as a part of vulnerability assessments. For instance, a network that uses an F5 BIG-IP load balancer on its perimeter can skew the results of a test that relied on operating system guessing. While the website being hosted can reside on a Microsoft IIS server, the BIG-IP fingerprints as a BSD UNIX operating system. In this case, a more comprehensive test prevents inaccurate and possibly dangerous results.

### Operating system and host name reporting

Operating system guessing and host name determination in Alert Logic scanning is based off of a weighted system. The report shows the item with the highest weight (confidence factor).

Examples of the host name weighted system are as follows:

| Method | Weight  |
|---|---|
| DNS forward lookup | 1 |
| FTP/SMTP/Telnet/IMAP/POP3 Banners | 4 |
| SSL Certificate Subject Names | 5 |
| MS RPC | 5 |
| SNMP | 6 |
| MSSQL | 8 |
| NetBIOS – nbtstat | 12 |
| Authenticated SSH | 13 |
| Authenticated NetBIOS | 15 |

Examples of the host weighted system are as follows:

| Operating system guessing method | Weight  |
|---|---|
| IP Fingerprinting (nmap) | 2 |
| HTTP Server Headers | 5 |
| FTP/SMTP/Telnet/IMAP/POP3 Banners | 6 |
| NetBIOS – nbtstat | 8 |
| Authenticated – SNMP | 10 |
| Authenticated – SSH | 11 |
| Authenticated – NetBIOS | 15 |

### Web application testing

Alert Logic scanning looks for sample/default web pages left from an installation and commonly named files and folders that draw attention from malicious users. Some additional tools check web applications for rudimentary validation errors.

Note that Alert Logic does not perform complete web application tests or source code audits, though many of the http checks overlap with custom application testing.

#### PCI scanning for web applications

Comprehensive web application scanning is a standard part of Alert Logic PCI scans. Web application scanning enhancements offer hierarchically deep, page-level scanning of common attack vectors including the OWASP Top Ten, SQL injection, and cross-site scripting. The scanning system indexes web servers and builds a list of hierarchical URL links in the website. Web application checks are performed separately for each URL to provide site-wide coverage.

Web application scanning of customer websites is a part of PCI scans only and is not included in external or internal scans. However, scanning for vulnerabilities on standard web applications (such as Wordpress or Joomla) is part of all Alert Logic scans.

#### Other web application scanning features

* SQL injection: Check if SQL parameter injection is allowed on the query parameters
* Cross−site scripting: Check if cross-site scripting (XSS) is allowed on the query parameters
* HTTP PUT allowed: Check if the PUT option is enabled at server directories
* Directory index-able: Check if the server directories can be browsed
* Obsolete files exist: Check if obsolete files exist
* CGI scanning: Test for common check web pages

#### Spider capabilities

A spider crawls websites and gathers as many URL links as possible. These links provide the list of URLs the scanner targets for testing. Spider functions include:

* Crawling HTTP and HTTPS websites based on given URL
* Cookie support

The spider has the following limitations:

* SSL websites with invalid certificate cannot be crawled
* Some "malformed" URLs in HTML pages cannot be recognized
* Javascript generated URLs cannot be found using this spider

### Wireless networks

Wireless environments are transparent to the Alert Logic scanning system. Wireless devices have IP addresses and run applications just like other network systems. In that sense, wireless devices are assessed for security by Alert Logic. However, Alert Logic scanning is based on the Network layer (specifically IP only) and above; lower levels such as Data Link (PPP, SLIP, Ethernet, 802.11b, ATM, Frame-relay) and physical (Fiber, Cat-5, Cat-3, phone line, serial cable) are not within the scope of a network-based assessment.

## Vulnerability and exposure library

### Vulnerability sources

Alert Logic uses a variety of vulnerability suppliers: public, commercial, third-party, and vendor driven.

* Security Focus (bugtraq, pentest, incidents, vulndev)
* Cert
* Vulnwatch
* OSVDB
* CVE
* NVD
* I-Cat
* Other vendors

### Severity ratings

Alert Logic severity ratings come from the method used by the National Institute of Standards and Technology National Vulnerability Database and are based on the CVSS Base Score.

Alert Logic assigns each vulnerability one of the following severities based on the CVSS score:

| Severity | CVSS base score |
|---|---|
| Info | 0.0 |
| Low | 0.1 - 3.9 |
| Medium | 4.0 - 6.9 |
| High | 7.0 - 10.0 |

### CVE numbers

The Common Vulnerabilities and Exposures (CVE®) enumeration system was developed by the MITRE Corporation. The [CVE website](http://cve.mitre.org/) provides more information.

Use the CVE number to find vulnerability text that other vendors and researchers have made available or correlate vulnerability assessments with IDS data.

### Types of vulnerabilities

#### Dangerous default settings

Dangerous default settings come in various forms such as the following:

* Leaving sample pages/scripts on an IIS installation
* Not changing the manager password from "manager" on a 3Com hub/switch
* Leaving public/private as SNMP community names on a SNMP enabled device
* Failing to set the sa password on a MS-SQL server

#### Software features and best practices

Attackers can take advantage of usability features for a system or application and use them to access your network, for example:

* ICMP timestamp/netmask requests
* Microsoft netBIOS protocol
* Expand/Verify commands of Sendmail
* Ident services displaying the owner of running processes

#### Misconfigurations

Alert Logic designed the scanning system to separate true misconfigurations from default out-of-the-box settings. Common misconfigurations that are identified and reported include the following:

* SMTP relay
* Unrestricted netbios file sharing
* DNS zone transfers
* FTP world writeable directories
* Default administration accounts without passwords
* Open FrontPage websites
* NFS world exportable directories

#### Vendor flaws

Vendor flaws are the largest category. It includes buffer overflows, string format issues, directory transversals, and cross-site scripting. This category includes any vulnerability that requires a patch or an upgrade to fix.
