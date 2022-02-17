# Virtual Host

The ADC Virtual Host page includes the following sections. Click on the link to go to the corresponding section to learn more:

<!--<MadCap:menuProxy mc-linked-toc="$topicHeadings" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />-->
To go to the documentation for the previous section of the manual, see [Deny and Error Handling](ref_services_deny_and_error_handling.md). To go to  the documentation for next subsection in the ADC section, see [Load Balancing](ref_services_load_balancing.md).

**To access the Virtual Host page in the WAF management interface**:

1. On the left panel, under Services, click **Websites**.
2. On the Websites page, click the website you want to manage.
3. Under ADC, click **Virtual Host**.

To save configuration changes or edits you make to any features and options, you must click **Save** on the lower-right of the section or page where you are making changes. Click **apply changes** on the upper-left corner of the page, and then click **OK**. Your changes will not be stored if you do not properly save your changes.

The virtual host is the website proxy that is accepts requests for the web servers serving the website for which the ADC is proxying requests.

### Deployment

Alert Logic Managed Web Application Firewall (WAF) is designed to easily fit into complex data centers without sacrificing the inherent protection advantages of the reverse proxy deployment mode. This is achieved through the deployment options reverse proxy and routing proxy. Both deployment options offer the full set of WAF features including inspection, rewriting, blocking of outgoing server responses, accelerating, caching and compression.

The two deployment options can be used in combination on the same appliance as the deployment option applies to single websites. The same appliance can  serve websites deployed in routing proxy and reverse proxy mode at the same time.

#### Reverse proxy

In reverse proxy, the appliance terminates all traffic destined to the website it protects. For HTTP(S), traffic requests are validated and forwarded to the backend web server on behalf of the client.

A number of IP addresses are assigned to the appliance. The number of IP addresses required depends on the number of SSL websites, and the type of SSL certificates used. As a general rule, one unique IP address is required for each certificate deployed on the appliance.

To direct traffic through the reverse proxy, either NAT rules or DNS must be altered to point to the appliance. If it is required that traffic to other (non-http) services reach the web server from the Internet, then you must create separate NAT rules  for the ports serving those services that bypass the appliance.

Reverse proxy completely shields the web server infrastructure and allows for inspection of both client requests and server responses. This also rewrites and inserts cryptographic tokens that allow protection against session hijacking, cross-site request forgery, and similar attacks.

Reverse proxy is easy to implement, but a number of extra IP addresses are required. For more complex data centers, reverse proxy is not recommended because of the number of changes that are required for the network firewall NAT rules.

#### Routing proxy

Routing proxy deployment has all the advantages of reverse proxy both in terms of protection, acceleration, caching and compression. All features available for reverse proxy are also available in routing proxy deployment.

The major difference is that routing proxy deployment does not require more than one IP address for each of the WAF appliances network interfaces and the only change necessary on the network firewall (or router) is to configure it to route traffic to the protected web servers through WAF. Web traffic to the protected servers are picked up and validated while traffic to other protocols like SSH, SMTP and FTP are routed through to the backend web servers.

The ability to route traffic to other services also means that only the HTTP services on the backend web servers  are protected by the appliance. Sine the IP addresses and network firewall policy rules leave a small footprint, this deployment option is the best one for complex data centers.

### Virtual web server

<colgroup></colgroup>| **              Web server            ** Read only | Protocol and fully qualified domain name (FQDN) for the website the proxy is configured for. |
| **              Website status            ** Drop-down list | Controls if WAF serves the website  by the  node.<dl><dt>                Enabled              </dt><dd>The WAF node serves requests to the website.</dd><dt>                Disabled              </dt><dd>Requests to the website are served with a default 404 not found error message.</dd></dl> |
| **              Proxy name            ** Input field | The name of the website proxy when listed in overview tables and reports.<dl><dt>                Valid input              </dt><dd>An alphanumeric string</dd><dt>                Default value              </dt><dd>The first part of the virtual host address. If the host address is intranet.domain.tld, the proxy name defaults to "intranet."</dd></dl> |
| **              Deployment            ** Drop-down list | The proxy deployment mode.<dl><dt>                Valid input              </dt><dd>Select deployment mode from list,</dd><dt>                Default value              </dt><dd>Reverse Proxy</dd></dl> For a description of the deployment options, refer to [Deployment](#ref_services_virtual_host_deployment.md). |
| **              Listen IP            ** Select combo | The IP address to which the virtual host is bound. Click **Edit list** to change the IP address configuration.<dl><dt>                Valid input              </dt><dd>One or more IP addresses in the select list to the left.</dd><dt>                Default value              </dt><dd>The IP address(es) configured when creating the website proxy.</dd></dl> |
| **              HTTP listen port            ** Input field | The port number the virtual HTTP host is listening to.<dl><dt>                Valid input              </dt><dd>A valid TCP/IP Port number</dd><dt>                Input example              </dt><dd>`80`</dd><dt>                Default value              </dt><dd>The port number set for the server when created.</dd></dl> |
| **              HTTPS listen port            ** Input field | The port number the virtual HTTPS host is listening to.<dl><dt>                Valid input              </dt><dd>A valid TCP/IP Port number</dd><dt>                Input example              </dt><dd>`443`</dd><dt>                Default value              </dt><dd>The port number set for the server when created.</dd></dl> |
| **              Vhost test            ** Button | Click **HEAD Request** to test the VHOST. |

### SSL certificate

In the SSL certificate section, the current SSL certificate in use is displayed. To upload a new certificate, click the **Manage certificates**.

When you create an SSL website, WAF gives this website a temporary SSL certificate. You are able to substitute the temporary certificate with a signed certificate. These actions are only intended for SSL enabled website proxies, and the SSL section is only shown for SSL enabled website proxies.

#### Exporting certificate from web server

When you create a website proxy for an existing HTTPS web server, you need to export the SSL certificate from the web server, and import the certificate toWAF. WAF supports the imports of  the following formats:

* **PKCS12 (or PFX)**: The standard format that Microsoft IIS servers use. It stores public key, private key, and the key chain in one single encrypted file.
* **PEM**: Commonly used in *nix based web servers like Apache and Nginx. When ordering certificates, this format is often referred to as “Apache format.”
* **Intermediate**: A subordinate certificate where the chain begins at the trusted root, through the intermediate and ending with the SSL certificate issued to you.

The links below open procedures that refer to third party products and guidelines, and may change at the vendors discretion.

The following options show you how to export an SSL certificate from the most common servers. To export a certificate from the web server, refer to the vendors guidelines.

#####       Export an SSL certificate from a Microsoft IIS server    

When you export an SSL certificate from a Microsoft IIS server, the certificate is usually obtained in PKCS12 (<kbd>.pfx</kbd>) format. The instructions for exporting from IIS 7 below includes the SSL certificate chain.

Microsoft guidelines can be found on the links below:

* IIS 5.0: [How to back up a server certificate in Internet Information Services 5.0](http://support.microsoft.com/default.aspx?scid=kb;en-us;232136&amp;sd=tech)
* IIS 6.0: [Exporting a Client Certificate for One-to-One Mapping](http://www.microsoft.com/technet/prodtechnol/WindowsServer2003/Library/IIS/6584a227-fc47-42f4-9e86-abcd7e72cca0.mspx)

###### Add the certificate

**To add a certificate**:

1. Open the **Windows Start** menu.
2. In the Search box, type MMC and then click **OK**.
3. Click the **File** tab, and then select **Add/Remove Snap-in**.
4. Click on **Certificates**, and then click **Add**.
5. Select **Computer Account**, and then click **Next**.
6. Select **Local Computer**, and click **Finish**.
7. Click **OK** to close the Add/Remove snap-in window.
8. In the center pane, double-click **Certificates (Local Computer)** in the center window.

###### Export the certificate                

**To export the certificate**:

1. Double-click on the **Personal** folder, and then click **Certificates**.
2. Right-click the certificate you want would like to backup, and then select **ALL TASKS** and then **Export**.
3. Follow the Certificate Export Wizard to backup your certificate to a .pfx file.
4. Select **Yes, export the private key**.
5. Select **Include all certificates in certificate path if possible**.
Do not select the **delete Private Key** option.
6. Type a password you can remember, and then save the file.
7. Click **Finish**. You see the following message, "The export was successful."
8. Click **OK**.

##### Export an SSL certificate from an Apache server

For apache-based web and application servers with default PEM encoding,  the SSL certificate can be copied directly from the file system and imported as is when the default PEM encoding is used.

Obtain the SSL-certificate file from the web servers file system. By default, the file is PEM-encoded.

The exact location may vary, but the Apache config file (<kbd>httpd.conf</kbd>) shows the exact location as in the example below:

<kbd>&amp;lt;VirtualHost 192.168.0.1:443&amp;gt;</kbd>

<kbd>DocumentRoot /var/www/html2</kbd>

<kbd>ServerName www.yourdomain.com</kbd>

<kbd>SSLEngine on</kbd>

<kbd>SSLCertificateFile /path/to/your_domain_name.crt SSLCertificateKeyFile</kbd>

<kbd>&amp;gt;/path/to/your_private.key</kbd>

<kbd>SSLCertificateChainFile /path/to/CA_chain.crt</kbd>

<kbd>&amp;lt;/VirtualHost&amp;gt;</kbd>

**Where:**

<kbd>SSLCertificateFile</kbd> is the server public key.

<kbd>SSLCertificateKeyFile</kbd> is the server private key.

<kbd>SSLCertificateChainFile</kbd> is the certificate chain.

Keep the contents of the files open. You will need it for the PEM (Apache) certificate upload section.

#### Importing the SSL certificate

When you create an SSL website, WAF assigns the website a temporary SSL certificate. You are able to substitute the temporary certificate with a signed certificate.

Depending on the format of the certificate, select the appropriate action in the bullet list.

##### Importing the PKCS12 format

To import a certificate in PKCS12 format:

1. Select **Import SSL certificate (PKCS12 format)**.
2. Click **Choose File** to browse your system for the file location.
3. In **Passphrase input**, type the passphrase.
4. Leave **Validate certificate chain** selected.
      When selected, WAF validates that the certificate chain is complete and ordered correctly. Do not clear this option unless the certificate import generates certificate chain errors that you must adjust manually after import.      6. Click **Save settings** in the lower right corner of the page.
7. Click **apply settings** at the top of the page to apply the certificate to the run-time configuration.

##### Importing the PEM format

**To import a certificate in PEM format:**

1. Select **Import SSL certificate (PEM format)**.
2. Open the .PEM file(s) in a text-editor. When obtained from the web server, the following extension convention is usually used:                    
<kbd>*.crt</kbd> – public keys, both server and CA chain
<kbd>*.key</kbd> – the private key
3. Copy the public certificate section of the certificate into the **SSL public key/certificate** field.                    
The public certificate is the section of the certificate file between (and including) the certificate start and end tags.
<kbd>-----BEGIN CERTIFICATE-----</kbd>
<kbd>Certificate characters</kbd>
<kbd>-----END CERTIFICATE--</kbd>
4. Copy the (SSL) private key section of the certificate into the **SSL private key** field.                     
The (SSL) private key is the section of the certificate file between (and including) the private key start and end tags.
<kbd>-----BEGIN RSA PRIVATE KEY-----</kbd>
<kbd>Private key characters</kbd>
<kbd>-----END RSA PRIVATE KEY-----</kbd>
5. In the **Passphrase**, field type the passphrase for the private key  (if the original private key was encrypted).
6. Leave **Validate certificate chain** selected.                    When selected, WAF validates that the certificate chain is complete and ordered correctly. Do not clear this option unless the certificate import is generates certificate chain errors that you must adjust manually after import.
7. Click **Save Settings** in the lower right corner of the page.
8. Click **Apply Settings** at the top of the page to apply the certificate to the run-time configuration.
9. (Optional) In **SSL authority certificate(s) chain**, if a certificate authority chain is provided with your certificate, enter the entire list of certificates (more than one certificate may be provided).
10. Click **Save settings**. The imported certificate is displayed in the certificate table along with the certificate chain (if any). Verify that the certificate is imported correctly.
11. Click the **Apply settings**.

#####  Importing the intermediate certificate

To import an intermediate certificate:

1. Select **Edit Certificate Chain**.
2. Open the intermediate certificate in a text-editor. When obtained from the web server, the following extension convention is usually used:                
The public key/certificate is the section of the certificate file between (and including) the certificate start and end tags.
<kbd>&amp;lt;-----BEGIN CERTIFICATE---&amp;gt;</kbd>
<kbd>Certificate characters</kbd>
<kbd>&amp;lt;-----END CERTIFICATE---&amp;gt;</kbd>
3. Click **Save settings** in the lower right corner of the page.
4. Click **apply settings** at the top of the page to apply the certificate to the run-time configuration.

### SSL settings

Minimum SSL protocol version.

<!-- Need information for SSL Settings -->
### SSL ciphers

<!-- Need information for SSL Ciphers -->
### Virtual host aliases

To configure WAF to handle requests for host aliases to the main configured domain name (e.g. www.mydomain.com), add a list of aliases in this section.

If the web system that answers requests to `www.mydomain.com` also serves requests to `mydomain.com`, `www.mydomain.net` and `mydomain.net` and uses the same content as `www.mydomain.com`, then WAF handles and validates the alias domain names as aliases to the main virtual host when added to this section.

<colgroup></colgroup>| **              Virtual host aliases            ** Input area | A list of host names.<dl><dt>                Valid input              </dt><dd>Host names separated by new-line.
Wildcard character * can be used to substitute the server name and sub domains.</dd><dt>                Input example              </dt><dd>``mydomain.com``
``www.mydomain.net``
``*.mydomain.net - matches www.mydomain.net, www.intra.mydomain.net, a.b.c.d.e.f.mydomain.net...``
`10.10.10.20`</dd><dt>                Default value              </dt><dd>`&amp;amp;lt;none&amp;amp;gt;`</dd></dl> |

When WAF is deployed as a proxy, requests for virtual host aliases are filtered and forwarded without modification to the host header.

#### Wildcards

You can use the wildcard character `*` to match the server name part of the domain name (e.g. www). If for instance, the domain names `www. domain.net`, `www2.domain.net`, `www3.domain.net` and `webserver.domain.net` all point to the same server the wildcard expression `*.domain.net` is used to match all HTTP requests pointing to domain.net. This is provided that the DNS records of the respective hosts all point to WAF.

#### Default proxy

When enabled, the proxy is used as the default host for requests of the IP address to which the proxy is configured to listen. The default proxy responds to all requests for virtual hosts that are not configured as primary host name, or as a virtual host for other proxies listening to the same IP address. This allows you to configure a single proxy that serves requests for several host names that the same backend web server serves without adding all the virtual host names in WAF.

### Timeouts

<colgroup></colgroup>| **              Client READ header timeout            ** Input field | Max time to wait for the client request header.<dl><dt>                Unit              </dt><dd>Seconds</dd><dt>                Valid input              </dt><dd>Number in range 2 - 7200</dd><dt>                Default value              </dt><dd>`60`</dd></dl> |
| **              Client READ body timeout            ** Input field | Max time to wait for the client request body.<dl><dt>                Unit              </dt><dd>Seconds</dd><dt>                Valid input              </dt><dd>Number in range 2 - 7200</dd><dt>                Default value              </dt><dd>`60`</dd></dl> |
| **              Client SEND timeout            ** input field | Max time to wait for a client send to complete.<dl><dt>                Unit              </dt><dd>Seconds</dd><dt>                Valid input              </dt><dd>Number in range 2 - 7200</dd><dt>                Default value              </dt><dd>`60`</dd></dl> |

### HTTP request and connection throttling

####  HTTP request throttling

<colgroup></colgroup>| **              HTTP request throttling status            ** Info | Displays the global HTTP throttling status. Click **configure** to be redirected to the [HTTP request throttling ](ref_services_http_global.md#ref_services_http_global.md#d0e2024) section where you can change your settings. |
| **              Maximum burst rate            ** Input field | The amount of requests the client is allowed to exceed the allowed request rate. For instance, if the maximum burst rate is set to 20 per second and the request rate is limited to five request, then the client can issue 20 requests for one second. Then must wait four seconds until the rate is balanced. When a client  loads an html page, it typically results in a lot of sub-requests for graphic elements, style sheets, javascript, etc. Setting a reasonable burst rate allows for fast page loads when the request rate is limited.<dl><dt>                Unit              </dt><dd>requests / second</dd><dt>                Valid input              </dt><dd>Number in the range 0 - 1000000</dd><dt>                Default value              </dt><dd>`20`</dd></dl> |
| **              Throttling action            ** Drop-down list | How to handle exceeding limits of the client.<dl><dt>                Delay              </dt><dd>Delay responses to slow down the client
Default selection</dd><dt>                Error 503              </dt><dd>Return `HTTP error 503`</dd></dl> |
| **              Throttling zone            ** Drop-down list | Client request rate is tracked across website proxies using four global databases, throttling zones. To account for different usage patterns throttling limits are defined separately for each global throttling zone. |

#### HTTP connection throttling

<colgroup></colgroup>| **              HTTP connection throttling status            ** Info | Displays the global HTTP connection throttling status. Click **configure** to be redirected to the [HTTP connection limiting](ref_services_http_global.md#ref_services_http_global.md#d0e2200) section where you can change your settings. |
| **              HTTP connection throttling zone            ** Drop-down list | Client request rate is tracked across website proxies using four global databases, throttling zones. To account for different usage patterns throttling limits are defined separately for each global throttling zone. |

### Client source IP                  

HTTP requests often pass through one or more proxy servers before reaching the endpoint web server. Examples include web gateways in the client network, content delivery networks (CDN), caching servers, SSL accelerators, layer 7 load balancers and web application firewalls. Each time the request passes through a proxy server, the source IP of the request changes to the IP address of the proxy server. This meanst he source IP from the network connection (socket) cannot be the IP address of the original request. To account for this, the standard is that proxy servers insert the client source IP in a request header named X-Forwarded-For. This is the default behavior of Alert Logic Managed Web Application Firewall (WAF).

Another option is to configure WAF as a **Transparent Proxy**, which reinserts the client source IP before it forwards the request to the backend web environment.

#### Transparent proxy

Play tricks at the network level to inject the client IP as the source of the request to the backend server. This requires modification of default gateway at the backend server to make the response go back through WAF.

<table>
  <colgroup>
    <col />
    <col />
  </colgroup>
  <tbody>
    <tr>
      <td>
        <b>              Transparent Proxy            </b>
      </td>
      <td>
        <ul>
          <li>WAF inserts the client source IP as the source IP of the request it forwards to the backend web server.</li>
          <li>Backend web servers must be configured to use WAF as the default gateway to ensure inspection of return web traffic and a response to the client request.                                </li>
          <li>IP-Forwarding (routing) must be enabled in WAF.</li>
          <li>Performance drawbacks because connections from WAF to backend web servers cannot be kept alive and because all traffic, including non-HTTP, from web servers have to pass through WAF.</li>
          <li>Because WAF must be the default gateway, transparent proxy is only recommended for smaller deployments where WAF is not deployed in combination with a load balancer.                                </li>
        </ul>
        <p>You must enable and configure transparent proxy.</p>
      </td>
    </tr>
  </tbody>
</table>
You can apply transparent proxy configuration to both routing proxy and reverse proxy deployment modes. When enabled, WAF inserts  the client source IP in the request to the backend web server to preserve it. In practice, the transparent proxy spoofs the client source IP which is why this feature is sometimes also called client impersonation.

While transparent proxy preserves the client source IP in the HTTP requests the backend web server receives, it has a few drawbacks of performance and availability risk. Because the original client IP is inserted as the source IP of the connection that is made to the backend, every request to not reuse connections from other client IPs requires a new connection. This negatively impacts the performance. WAF deployed as either reverse or routing is easy to bypass if both nodes in a cluster fails, because only a change a NAT rule or a static route is required. This is further complicated when it is proxying transparently because the backend web servers are configured to use the WAF cluster as a gateway. This means that each backend web server must be reconfigured to restore availability in the unlikely event that both WAF nodes in a cluster fails.

The original client source IP needs WAF configured as the default gateway for the web server response to come back through WAF. This also means that it is complicated and error prone  to implement use transparent proxy in high performance deployments where WAF is deployed in combination with a load balancer.

##### Configuring transparent proxy

To minimize the availability impact on the web properties the configuration of transparent proxy must performed in the following order:

<dl>1. If WAF is deployed as a cluster, create a cluster interface with an VIP that the backend web servers can reach in **System**&amp;gt; **Clustering**.
2. Enable IP Forwarding in **Services** &amp;gt; **Network** &amp;gt; **Network routing**.
3. Edit the segmentation table to make sure that routing does not violate network segmentation settings in **Services** &amp;gt; **Network** &amp;gt; **Network routing**. By default, routing cannot traverse network interfaces.
4. Configure backend web servers to use WAF as default gateway.

</dl>#### Proxy protocol

Alert Logic allows you to enable proxy protocol, which is designed to safely transport connection information without losing any information. Enabling proxy protocol allows WAF to work with multiple layers of NAT or TCP proxy protocols, does not require infrastructure changes, has no impact on NAT firewalls, and is scalable.

<colgroup></colgroup>| **              Enable proxy protocol            ** Check box | Safely transport connection information without losing any information |

Enabling proxy protocol on the WAF is not necessary unless you are configuring both communicating endpoints. If you have configured the other communicating endpoint to proxy protocol, you can enable proxy protocol in the WAF.

You must configure proxy protocol on both endpoints of the connection. If one endpoint connection is not configured to use proxy protocol, the websites stop communicating, and WAF does not function properly.

#### Trusted proxy

Since the X-headers are part of the client request WAF receives, and the client can manipulate it, they cannot be trusted. The information that the proxy insert can only be trusted if the client does not control that information. This is if the proxy that receives the request from the client, for instance a load balancer in front of WAF, follows the standard of appending the source IP it receives the request from to the X-Forwarded-For header. In addition, it must overwrite values in X-Forwarded-Proto and X-Forwarded-Port headers with protocol and port information to be trusted. Such a proxies, defined by one or more IPs, are referred to as **Trusted Proxies**.

When WAF receives a request from a trusted proxy, IP based blocking extracts and uses the IP address of the client source IP from the X-Forwarded-For header in place of the actual request (socket) IP for both HTTP Throttling. For the IP based blocking controls, the X-Forwarded-For IP transparently replaces the socket IP and the network blocking controls works without other modification to the policy.

<table>
  <colgroup>
    <col />
    <col />
  </colgroup>
  <tbody>
    <tr>
      <td>
        <b>              Use trusted proxy - extract client source IP from X-Forwarded-For header            </b>
        <p>Check box</p>
      </td>
      <td>
        <p>Enable Trusted Proxy functionality.</p>
        <p>When enabled, if a request is received from a proxy from the list of trusted proxies:</p>
        <ul>
          <li>WAF extracts the client source IP from the X-Forwarded-For header</li>
          <li>Enable this option to use the extracted client source IP for HTTP Throttling </li>
          <li>Use the extracted client source IP for IP whitelisting controls</li>
          <li>Transparently enforces the source IP based request blocking at layer 7 based on the extracted IP instead of at the network level</li>
        </ul>
        <p>Default: <code>&amp;lt;disabled&amp;gt;</code></p>
      </td>
    </tr>
    <tr>
      <td>
        <b>              Reset X-Forwarded-For header to last untrusted source in list            </b>
        <p>Check box</p>
      </td>
      <td>
        <p>Following the proposed standard, the X-Forwarded-For header may contain a comma separated list of IP addresses. Depending on the configuration options in the endpoint web server and application, it may be logged with a comma separated list, which you may not want.                           </p>
        <p>For WAF to always forward the X-Forwarded-For a single IP address, enable this option. </p>
        <p>Default: <code>&amp;lt;disabled&amp;gt;</code></p>
      </td>
    </tr>
    <tr>
      <td>
        <b>              Forward X-Forwarded-For and X-Forwarded-Proto headers from trusted proxy unaltered            </b>
        <p>Check box</p>
      </td>
      <td>
        <p>Leave X-Headers untouched from trusted proxy.</p>
        <p>If WAF is deployed behind another reverse proxy, by default, WAF inserts the source IP from that proxy in the X-Forwarded-For header sent to the backend web server. If the X-Forwarded-For header is already present, the source IP is appended to the header.                           </p>
        <p>While this behavior conforms to standards, you may not always want it. You can configure trusted proxies to forwarded the X-Forwarded-For header as it is received from the trusted proxy without modifying it.                           </p>
        <p>Default: <code>&amp;lt;disabled&amp;gt;</code></p>
      </td>
    </tr>
    <tr>
      <td>
        <b>               Trusted CIDR ranges            </b>
        <p>Input field</p>
      </td>
      <td>
        <p>List of Trusted CIDR ranges from which X-Forwarded-For header is forwarded unmodified to the backend web server.</p>
        <dl>
          <dt>                Valid input              </dt>
          <dd>
            <p>IP addresses with net mask (IP/mask) in CIDR notation separated by newline</p>
          </dd>
          <dt>                Input example              </dt>
          <dd>
            <p>
              <code>192.168.0.8/32</code> - the IP address 192.168.0.8                                    </p>
            <p>
              <code>192.168.0.0/24</code> - IP addresses 192.168.0.0 - 255                                    </p>
            <p>
              <code>192.168.0.8/29</code> - IP addresses 192.168.0.8-15                                    </p>
          </dd>
          <dt>                Default value              </dt>
          <dd>
            <p>
              <code>&amp;lt;none&amp;gt;</code>
            </p>
          </dd>
        </dl>
      </td>
    </tr>
  </tbody>
</table>##### X-Forwarded-For

The standard for forwarding client source IP from layer 7 proxies. Header is always inserted.

<table>
  <colgroup>
    <col />
    <col />
  </colgroup>
  <tbody>
    <tr>
      <td>
        <b>              X-Forwarded-For            </b>
      </td>
      <td>
        <ul>
          <li>Client source IP is inserted in X-Forwarded-For header</li>
          <li>Client source IP is present in the header even if the request passed through other proxy servers</li>
          <li>Standards compliant approach</li>
          <li>Better performance because connections to backend web servers can be kept alive</li>
          <li>May require modifications to backend applications to read the X-Forwarded-For header</li>
        </ul>
        <p>The X-Forwarded header is always inserted.</p>
      </td>
    </tr>
  </tbody>
</table>
The X-Forwarded-For (XFF) HTTP header field is a standard to identify the originating IP address of a client connecting to a web server through an HTTP proxy or load balancer. This is an HTTP request header the developers of Squid caching proxy server introduced. An effort has been started at IETF for standardizing the Forwarded HTTP header.

When the request passes through multiple proxy servers, each server adds the respective source IP to the X-Forwarded-For header. The X-Forwarded-For header then contains a list of IP addresses the request has passed through. The leftmost IP address is the original client IP. The rightmost IP address is the last proxy in the chain, and the source IP of the request is the address of the last proxy.

This allows the endpoint web server to extract and log the original client IP address from the XFF header for applications that need this data. The endpoint web server no longer needs to extract data for the IP address of the last proxy in the chain from which the request received.

WAF is a proxy-based device that terminates requests from clients and makes requests to the backend web server on behalf of the client. To make the original source IP available to the backend web application, WAF forwards the source IP address to the backend server in the X- Forwarded-For header.

##### Other X-headers

In addition to the X-Forwarded-For header Layer 7, proxies often insert X-headers with information about which protocol and port from the request they received. The following headers are:

* X-Forwarded-Proto: Contains the protocol the request was received on - HTTP or HTTPS
* X-Forwarded-Port: Contains the port the request was received on

Contrary to the X-Forwarded-For header, these headers are not lists. This means that WAF overwrites their information   if it receives the request from a proxy that already inserted them.

If requests through WAF passes through further layer 7 proxies on their way to the backend servers,  you must copy the value of those headers into reserved custom headers like X-WSM-Forwarded-Proto. WAF does this to keep the value of these headers as received  intact. You can insert request heads to copy the value of those headers in [Health Checking section in Load Balancing](ref_services_load_balancing.md#ref_services_load_balancing_health_checking.md).

### Redirects

Redirects tells the client to get the requested resource elsewhere. The Redirect feature instructs clients to make a new request with a different URL. It often redirects HTTP requests for resources requiring encryption to corresponding pages on an SSL encrypted connection - HTTPS.

When redirecting, WAF sends an `HTTP 301 - Permanently Moved` response code.

#### Match types

WAF allows for either `prefix`, `regex` or `vhost regex` based matching of client requests.

#####       Prefix    

If prefix match is selected, the requested URL is matched left to right beginning with a slash (`/secret`).

##### Regex 

If Regex match is selected, the requested URL is matched using a regular expression. You can match asp files in a specific directory and instruct the client to request a php file in another directory on another server using HTTPS instead of HTTP.

Do not select Regex match type unless you really need it. Prefix is cheaper CPU wise.

#####       Vhost regex    

The vhost regex type allows for matching on elements in the virtual host name. The vhost regex redirects to a different virtual host optionally with some of the matched elements in the target URL- like redirecting foo.alertlogic.com to http://www.alertlogic.com/foo or foo.alertlogic.net to http://www.alertlogic.com/net/foo.

The syntax is dependent on the match type selected.

#### Prefix match

<table>
  <colgroup>
    <col />
    <col />
  </colgroup>
  <tbody>
    <tr>
      <td>
        <b>              Enable external redirects            </b>
        <p>Check box</p>
      </td>
      <td>
        <p>When selected, WAF redirects client requests based on redirect rules configured.</p>
      </td>
    </tr>
    <tr>
      <td>
        <b>              Proto            </b>
        <p>Drop-down list</p>
      </td>
      <td>
        <p>For website proxies serving both HTTP and HTTPS, select the protocol to match.</p>
        <p>If for instance, you only want to serve a specific page using the HTTPS protocol match the corresponding HTTP page and redirect to HTTPS on the same site.                           </p>
      </td>
    </tr>
    <tr>
      <td>
        <b>              Match type            </b>
        <p>Drop-down list</p>
      </td>
      <td>
        <p>See above.</p>
      </td>
    </tr>
    <tr>
      <td>
        <b>              Match            </b>
        <p>Input field</p>
      </td>
      <td>
        <p>The client request to match.</p>
        <p>If prefix match is selected, the requested URL is matched left to right beginning with a slash (<code>/secret</code>). Only complete path segments are matched so prefix match type is basically matching on a "directory" basis.                           </p>
        <dl>
          <dt>                Valid input              </dt>
          <dd>
            <p>A case-sensitive (%-decoded) path beginning with a slash</p>
          </dd>
          <dt>                Input example              </dt>
          <dd>
            <p>
              <code>/secret</code> - matches requests for<code> /secret</code>,<code> /secret/</code>,<code> /secret/secret_file1.php</code>, etc. Does not match <code>/secret_file.php</code>.                                    </p>
            <p>
              <code>/</code> - matches requests for any resource, useful for setting up an HTTP proxy which redirects all requests to the same "location" on an HTTPS proxied website.                                    </p>
          </dd>
          <dt>                Default value              </dt>
          <dd>
            <p>
              <code>&amp;lt;none&amp;gt;</code>
            </p>
          </dd>
        </dl>
      </td>
    </tr>
    <tr>
      <td>
        <b>              Redirect externally to            </b>
        <p>Input field</p>
      </td>
      <td>
        <p>The new URL path to which the client is redirected.</p>
        <p>If prefix match is selected, the new URL path corresponds to the prefix matched. If /secret is entered in the match field (above) then the part of the request following the prefix (/secret) is sent to the new URL path.                           </p>
        <dl>
          <dt>                Valid input              </dt>
          <dd>
            <p>An absolute URL beginning with a scheme and hostname. A URL-path beginning with a slash may also be used, in which case the scheme and hostname of the current server is added.                                    </p>
          </dd>
          <dt>                Input example              </dt>
          <dd>
            <p>
              <code>https://ssl.somename.tld/moresecret</code> - In combination with the prefix match example above, <code> /secret</code> requests for <code>/secret</code> is redirected to <code>https://ssl.somenane.tld/moresecret,
 /secret/secret_file1.php</code> is redirected to <code>https://ssl.somenane.tld/moresecret/secret_file1.php</code>, etc.                                    </p>
            <p>
              <code>https://ssl.somename.tld/</code> - In combination with the prefix match example / above is redirect any request to <code>https://ssl.somename.tld</code>.                                    </p>
          </dd>
          <dt>                Default value              </dt>
          <dd>
            <p>
              <code>&amp;lt;none&amp;gt;</code>
            </p>
          </dd>
        </dl>
      </td>
    </tr>
    <tr>
      <td>
        <b>              Code            </b>
        <p>Drop-down list</p>
      </td>
      <td>
        <p>Select the error code you want displayed</p>
        <ul>
          <li>301 Moved Permanently </li>
          <li>302 Moved Temporarily</li>
          <li>303 See Other</li>
          <li>307 Temporary Redirect</li>
          <li>308 Permanent Redirect</li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>#### Regex match

<table>
  <colgroup>
    <col />
    <col />
  </colgroup>
  <tbody>
    <tr>
      <td>
        <b>              Enable external redirects            </b>
        <p>Check box</p>
      </td>
      <td>
        <p>When select, WAF redirects client requests based on redirect rules configured.</p>
      </td>
    </tr>
    <tr>
      <td>
        <b>              Proto            </b>
        <p>Drop-down list</p>
      </td>
      <td>
        <p>For website proxies serving both HTTP and HTTPS, select the protocol to match.</p>
        <p>If for instance you only want to serve a specific page using the HTTPS protocol match, the corresponding HTTP page redirects to HTTPS on the same site.                           </p>
      </td>
    </tr>
    <tr>
      <td>
        <b>              Match type            </b>
        <p>Drop-down list</p>
      </td>
      <td>
        <p>See above.</p>
      </td>
    </tr>
    <tr>
      <td>
        <b>              Match            </b>
        <p>Input field</p>
      </td>
      <td>
        <p>The client request to match.</p>
        <p>If Regex match is selected, the requested URL is matched using a regular expression. The supplied regular expression is matched against the requested URL-path. If it matches, the server substitutes any parenthesized matches into the redirect URL path sent in the redirect response to the client.                           </p>
        <dl>
          <dt>                Valid input              </dt>
          <dd>
            <p>A valid regular expression</p>
          </dd>
          <dt>                Input example              </dt>
          <dd>
            <p>
              <code>(.+)\.jsp</code> - matches requests for any URL path ending in .jsp. The path and filename, but not the extension is the substitute variable $1 (for instance a request for <code>/secret/secret_java1.jsp</code> which results in $1 containing /<code>secret/secret_java1</code> making it possible to redirect to <code>https://ssl.somename.tld$1.php</code>. This results in the client being redirected to <code>https://ssl.somename.tld/secret/secret_java1.php</code>).                                    </p>
          </dd>
          <dt>                Default value              </dt>
          <dd>
            <p>
              <code>&amp;lt;none&amp;gt;</code>
            </p>
          </dd>
        </dl>
      </td>
    </tr>
    <tr>
      <td>
        <b>              Redirect externally to            </b>
        <p>Input field</p>
      </td>
      <td>
        <p>The new URL path to which the client is redirected.</p>
        <p>If Regex match is selected, the parenthesized matches in $1, $2, etc. is substituted into the new URL path allowing fine grained and complex redirect rules.                           </p>
        <dl>
          <dt>                Valid input              </dt>
          <dd>
            <p>An absolute URL beginning with a scheme and hostname optionally with $1, $2, $3, etc. as placeholders to substitute matches.                                    </p>
          </dd>
          <dt>                Input example              </dt>
          <dd>
            <p>
              <code>https://ssl.somename.tld$1.php</code> - In combination with the regex match example <code>(.+)\.jsp</code>, requests for any URL path ending in <code>.jsp</code> is redirected to <code>https://ssl.somename.tld/</code>, but the extension <code>jsp</code> is php. For example, <code>/secret/secret_java1.jsp</code> is redirected to <code>https://ssl.somename.tld/secret/secret_java1.php</code>.                                    </p>
          </dd>
          <dt>                Default value              </dt>
          <dd>
            <p>
              <code>&amp;lt;none&amp;gt;</code>
            </p>
          </dd>
        </dl>
      </td>
    </tr>
    <tr>
      <td>
        <b>              Code            </b>
        <p>Drop-down list</p>
      </td>
      <td>
        <p>Select the error code you want displayed</p>
        <ul>
          <li>301 Moved Permanently </li>
          <li>302 Moved Temporarily</li>
          <li>303 See Other</li>
          <li>307 Temporary Redirect</li>
          <li>308 Permanent Redirect</li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>#### Vhost regex match

<table>
  <colgroup>
    <col />
    <col />
  </colgroup>
  <tbody>
    <tr>
      <td>
        <b>              Enable external redirects            </b>
        <p>Check box</p>
      </td>
      <td>
        <p>When selected, WAF redirects client requests based on redirect rules configured.</p>
      </td>
    </tr>
    <tr>
      <td>
        <b>              Proto            </b>
        <p>Drop-down list</p>
      </td>
      <td>
        <p>For website proxies serving both HTTP and HTTPS, select the protocol to match.</p>
        <p>If for instance, you only want to serve a specific page using the HTTPS protocol, match the corresponding HTTP page and redirect to HTTPS on the same site.                           </p>
      </td>
    </tr>
    <tr>
      <td>
        <b>              Match type            </b>
        <p>Drop-down list</p>
      </td>
      <td>
        <p>See above.</p>
      </td>
    </tr>
    <tr>
      <td>
        <b>              Match            </b>
        <p>Input field</p>
      </td>
      <td>
        <p>The vhost part of client request to match.</p>
        <p>If vhost regex match is selected, the vhost part of the client request is matched using a regular expression. If it matches, the server substitutes any parenthesized matches into the redirect URL path sent in the redirect response to the client.                           </p>
        <dl>
          <dt>                Valid input              </dt>
          <dd>
            <p>A valid regular expression</p>
          </dd>
          <dt>                Input example              </dt>
          <dd>
            <pre>foo\.alertlogic\.com</pre>
            <pre>www\.alertlogic\.(\w){1,5}</pre>
          </dd>
          <dt>                Default value              </dt>
          <dd>
            <p>
              <code>&amp;lt;none&amp;gt;</code>
            </p>
          </dd>
        </dl>
      </td>
    </tr>
    <tr>
      <td>
        <b>              Redirect externally to            </b>
        <p>Input field</p>
      </td>
      <td>
        <p>The new URL path to which the client is redirected.</p>
        <p>If the match expression contains parentheses, the parenthesized matches are placed in the variables $c1, $c2, $c9. These variables are used in the redirected URL to allow for fine grained and flexible redirects.                           </p>
        <dl>
          <dt>                Valid input              </dt>
          <dd>
            <p>An absolute URL beginning with a scheme and hostname, optionally with $c1, $c2, $c9 as placeholders to substitute matches.</p>
            <p>The placeholder variable names are different from the regex type above.</p>
          </dd>
          <dt>                Input example              </dt>
          <dd>
            <p>
              <code>http://www.alertlogic.com/foo</code>
            </p>
            <p>In combination with the match example, <code>foo.alertlogic.com</code> redirects requests for the hostname <code>foo</code> to a corresponding <code>subdir</code>.</p>
            <p>
              <code>http://www.alertlogic.com/$c1</code>
            </p>
            <p>In combination with the match,<code> www\.alertlogic\.(\w{1,5}</code> redirects <code>www.alertlogic.net/somepath?somequery </code>to<code> www.alertlogic.com/dk/somepath?somequery</code></p>
          </dd>
          <dt>                Default value              </dt>
          <dd>
            <p>
              <code>&amp;lt;none&amp;gt;</code>
            </p>
          </dd>
        </dl>
      </td>
    </tr>
    <tr>
      <td>
        <b>              Code            </b>
        <p>Drop-down list</p>
      </td>
      <td>
        <p>Select the error code you want displayed</p>
        <ul>
          <li>301 Moved Permanently </li>
          <li>302 Moved Temporarily</li>
          <li>303 See Other</li>
          <li>307 Temporary Redirect</li>
          <li>308 Permanent Redirect</li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>#### Examples summary

The examples from the table above are summarized below. Substitute `ssl.somename.tld` with the correct address.

<dl><dt>        On an HTTP proxy, redirect all requests to the corresponding location on an HTTPS proxy      </dt><dd>**              Match type            **: prefix
**              Match            **: /
**              Redirect externally to            **: https://ssl.somename.tld/</dd><dt>        On an HTTP proxy, redirect all requests for resources in `/secret` to `/moresecret` on an HTTPS proxy      </dt><dd>**              Match type            **: prefix
**              Match            **: `/secret`
**              Redirect externally to            **: https://ssl.somename.tld/moresecret</dd><dt>        On an HTTP proxy, redirect all requests for `.jsp` to a `.php` script with the same name and location on an HTTPS proxy      </dt><dd>**              Match type            **: regex
**              Match            **: `(.+)\.jsp`
**              Redirect externally to            **: https://ssl.somename.tld$1.php</dd><dt>        Virtual host redirect - redirect requests to somehost.somename.cc to www.somename.tld/cc/somehost/      </dt><dd>**              Match type            **: vhost regex
**              Match            **: `(\w+)\.somename\.(\w){1,5}
`
**              Redirect externally to            **: http://www.somename.tld/$c2/$c1</dd></dl>
<!-- Options and Traffic statistics are new section. Please incorporate links -->
### Options

<colgroup></colgroup>| **                Accept underscore characters in request headers              ** Check box | This option allows underscore characters to show up in request headers. |

<!-- Traffic statistics are new section. Please incorporate links -->
### Traffic statistics

<colgroup></colgroup>| **                Enable traffic statistics              ** Check box | Allows traffic statistics to be logged in the Traffic statistics section. |

### Lower button bar

<colgroup></colgroup>| **              Save settings            ** | Click **Save settings** to save settings. |
