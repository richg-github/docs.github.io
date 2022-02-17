## Frequently Asked Questions

For frequently asked questions, click on the link to go to the corresponding section to see questions for specific features:

<!--<MadCap:menuProxy mc-linked-toc="$topicHeadings" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />-->
To go to the previous section, see [Network Deployment](ch_network.md). To go to the next section, see [Alert Logic Managed Web Application Firewall (WAF) Release Notes](../../../release-notes/inline-waf.md).

## Deployment

|  | Network deployment Where in the network is WAF deployed? |
|  | Alert Logic Managed Web Application Firewall (WAF) is installed in the network between the network firewall and the web server. It is a filtering reverse proxy that terminates all client requests validates them and, if benign, re-issues the requests to the protected web servers on behalf of the clients. This means that the client (from the Internet) sees WAF as the web server that serves requests to the protected web site and the protected web server only communicates directly with Web Security Manager. |

## Client issues

|  | Client IP address appears not to be available to backend webserver Our web application is using the client IP for geo location and site statistics. After putting WAF in front of the website the web application only sees the IP address of WAF. Is there any way we can forward the client IP address to the backend web server? |
|  | Yes. As WAF is a reverse-proxy it terminates requests from clients and makes the request to the backend webserver on behalf of the client. That makes the source IP (of the client) disappear from the underlying IP packets. However, the original source IP address is forwarded to the backend server in a HTTP header. The header is called "X-Forwarded-For". Your application (or webserver) can be configured to use the information in the header instead if you are running an IIS server and you want it to log the client IP try Googling for "IIS X-Forwarded-For ISAPI filter". |

## SSL Certificates

|  | Wildcard SSL certificates Do you support the use of wildcard SSL certs? |
|  | Yes, you can use a wildcard SSL cert, but you will have to apply it for all proxies or make one proxy with a number of aliases (in proxy manage->settings->servers (like entering *.alertlogic.com in the alias list to match a *.alertlogic.com wildcard certificate). |
|  | SSL certificate update How do I update the SSL Certificate? |
|  | Updating SSL certificates can be done in several ways. The best approach is to have the CA generate a PEM certificate (it will do that when you select Apache as the destination server). When updating certificates, simply copy and paste the content (including ---BEGIN CERTIFICATE--- and ---END CERTIFICATE--- lines) of your renewed certificate into the correct Public key field for the WAF proxy in question. Do the same for the private key (which you should have when you generated a CSR file). Copy and paste that?? in the Private key field and press save. Make sure to type in the pass phrase in the Passphrase field if your private key is encrypted. WAF will then replace the copy of your Public and Private key with the new copies. |

## Troubleshooting

|  | Database locked error messages in System Error log We are getting a lot of database locked errors in the system error log and WAF is very slow. |
|  | Make sure Hyperthreading is disabled on platform on which WAF is installed. Start by checking the number of CPU's reported in System : Information. If the CPU count is doubled Hyperthreading is probably enabled. Disabling it will fix the problem. |

## Clustering

|  | Clustering not working in VMware ESX We have configured a cluster IP address in WAF running on VMware ESX but the IP address is unreachable. |
|  | Make sure `promiscuous mode` and `MAC address changes` are allowed on the VMware virtual switch (vswitch) or the port group in the VMware ESX network configuration. |

## Accessing Web Security Manager management interfaces

|  | How do I login to the console? |
|  | username: operator password: changeme When logging in to the console as the `operator` user the shell will be the Web Security Manager command-line interface (CLI). The Web Security Manager CLI is used for initial network configuration and basic network administrative tasks. All actions that can be made in the CLI also available in the web based  management interface. All licenses, including trials, have access to the Web Security Manager CLI. Remember to change the default password using command 'set password'. Note: This is not the management GUI. |
|  | How do I access the underlying OS - not the CLI? |
|  | OS access is only available in non-trial Web Security Manager installations. When a non-trial license key is applied the root password is set to the license key. Remember to change it. In the console CLI issue the command 'enable' and provide the root password. To use SSH, enable SSH access to management interfaces in System : Configuration. Connect to port 22 using an SSH terminal program like Putty. To change root password issue the command 'passwd' when logged in to the OS. |
|  | I cannot access the management GUI on HTTPS port 4849 |
|  | If you are accessing Web Security Manager through a network firewall it may be blocking HTTPS on this port. Change the management port by accessing the GUI from a node within the same network segment as the Web Security Manager node. In the GUI go to in System > Interfaces and change the listen port in the management role. |

## Learning

|  | Learner not learning from test requests Learning is enabled for the website but Web Security Manager is not learning anything. We have run a vulnerability scanner on the proxied website. The scanning included a complete site crawl but nothing was learned. |
|  | The Learner learns from input, that is: from un-trusted sources. In order to avoid an attacker polluting the policy by hitting the website with something automated, thresholds have to be reached for the policy to be generated. On top of that - if you have performed any blocked requests which have classified as known attack types (DoS, SQL Injection, XSS, etc.) then the Learner will not learn anything from your IP-address. The address has been banned and marked as hostile. To disable IP banning select "Learn from hostile sources (IPs)" in **Services**->**Websites**->**Learning**->**Learning settings**. Also the learner will look at factors like spread in time, sources and number of hits. In **Services**->**Websites**->**Learning**->**Learning settings** click "help" in the upper right corner to get the relevant section of the manual. To configure the Learner to learn from anything, right away, configure it with very low thresholds in Services > Websites > Settings->Learner. For example: Consecutive sample status updates: 1 - Learning thresholds all set to 1. Generate traffic to the site using for instance Microsoft Web Application Stress Tool which is freely available on the MS web site. Do *not* use the generated policy for production unless the test cases used are representative of real life requests. It will almost always result in false positives when the website proxy meets "real life". We recommend deleting all learned data and letting Web Security Manager learn from real life requests when it is deployed into the production environment. |

To save configuration changes or edits you make to any features and options, you must click **Save** on the lower-right of the section or page where you are making changes. Click **apply changes** on the upper-left corner of the page, and then click **OK**. Your changes will not be stored if you do not properly save your changes.

## Filtering

|  | Requests are blocked but not logged I have installed Web Security Manager in a test environment and created a website proxy for our test website, but my requests are not getting through. I get a “404 Not Found” message from Web Security Manager but the denied requests do not appear in the deny log of the website proxy. |
|  | The most common reason for blocked requests not showing in the website deny log is that they are logged in the Web Security Manager Generic website proxy (ID 0 in the overview). This is because the request is targeting an unknown host or is malformed in some other way. For example, when you bind inbound traffic to an interface with IP address 192.168.10.10 and you configure Web Security Manager to proxy requests for www.mydomain.com and then try to access the website by entering the IP address (192.168.10.10) in the browser address field, the request will be rejected because the browser sends a request for the virtual host 192.168.10.10 not the virtual host www.mydomain.com you just configured. If you want Web Security Manager to respond to the IP address (which is practical for test purposes but definitely not recommended for production), add the IP address to the virtual host aliases list in **Services**->**Websites**->**ADC**->**Load balancing**+**Virtual host aliases**. |
|  | NTLM authentication We have a MS IIS based site using NTLM authentication. When requests are proxied through Web Security Manager it does not work. How can we make it work? |
|  | Enable "Add HTTP/1.1 VIA header information" in **Services**->**Websites**->**ADC**->**Load balancing**. This should do it. Microsoft IIS is configured not to allow NTLM authentication if a request is coming from a proxy server (as with Web Security Manager). If it sees a NTLM request coming thru a proxy server, IIS will subvert to other authentication methods, such as Basic of Digest. If "Add HTTP/1.1 VIA header information" is enabled Web Security Manager will insert a Via: header in forwarded requests which will inform the back-end server that the request is proxied. |
|  | Redirecting from HTTP to HTTPS When our visitors request a resource in a specific path (like /secret/someapp.php), how do we redirect them to the same path on a corresponding HTTPS site. |
|  | Enter a redirect rule in **Services**->**Websites**->**ADC**->**Virtual host**. For example: To redirect visitors requesting http://www.mydomain.com/secret/someapp.php to https://www.mydomain.com/secret/someapp.php enter the following redirect rule: Match Type: "prefix" Match: /secret/ Redirect externally to: http://www.mydomain.com/secret/ This will redirect any request for resources in /secret/ to the HTTPS site. Note that the protocol and server address is required in the redirect to field. It can be any address including https://www.myotherdomain.com/secret/deep/in/the/directory/tree/ in which case a request for http://www.mydomain.com/secret/someapp.php will be redirected to https://www.myotherdomain.com/secret/deep/in/the/directory/tree/someapp.php. More advanced redirects are available using regular expressions see *redirect* in the manual or click *help* in the upper menu when you are on the server page. |
