# Preserve the Client IP Address

HTTP requests often pass through one or more proxy servers before they reach the endpoint web server, which changes the source IP address for the request.  As a result, endpoint web servers cannot rely on the source IP from the network connection (socket) to be the IP address of the original request. For this reason, you may want to use one of two options to preserve the original client IP address: X-Forwarded-For (XFF), or transparent proxy.

## X-Forwarded-For

The XFF field in the HTTP header identifies the originating IP address of a client connecting to a web server through an HTTP proxy or load balancer. The HTTP header field is the standard for preserving the client IP.

**Key elements of X-Forwarded-For are the following**:

* Standards compliant approach
* The default behavior of WAF
* Client source IP is inserted in XFF header
* Client source IP is present in the header even if the request has passed through other proxy servers
* Better performance because connections to backend web servers can be kept alive

The XFF  header identifies the originating IP address of a client connecting to a web server through an HTTP proxy or load balancer.

When the request passes through multiple proxy servers, each server adds its respective source IP to the XFF  header. This makes XFF header contain a list of IP addresses the request passed through. The leftmost IP address is the original client IP. The rightmost IP address is the second-to-last proxy in the chain, and the source IP of the request is the address of the last proxy.

This allows the endpoint web server that received the request to extract and log the original client IP address from the XFF header.

The Alert Logic Managed Web Application Firewall (WAF), as a proxy-based device, terminates requests from clients and makes requests to the backend web server on behalf of the client. The WAF forwards the source IP address to the backend server in the XFF header. This allows the original source IP available to the backend web application.

**Direct request through WAF**

A client with an IP address of 10.10.10.10 makes a direct request through WAF with an IP address of 192.168.100.10. When the request reaches the web server, the XFF  header and source IP will be:

* Source IP: 192.168.100.10
* XFF: 10.10.10.10

**Request through forward proxy through WAF**

A client with an IP address of 10.10.10.10 makes a request through a forward proxy with an IP address of 10.200.200.20, and through WAF with an IP address of 192.168.100.10. When the request reaches the web server, the XFF  header and source IP will be:

* Source IP: 192.168.100.10
* XFF: 10.10.10.10, 10.200.200.20

**Request through forward proxy through load balancer through WAF**

A client with an IP address of 10.10.10.10 makes a request through a forward proxy with an IP address of 10.200.200.20, through a load balancer with an IP address of 192.168.100.5, and through a WAF with an IP address of 192.168.100.10. When the request reaches the web server, the X-Forwarded-For header and source IP will be:

* Source IP: 192.168.100.10
* XFF: 10.10.10.10, 10.200.200.20, 192.168.100.5

## X-Forwarded-For options 

If WAF deploys behind another reverse proxy, WAF inserts the source IP from that proxy in the XFF  header sent to the backend web server. If the XFF  header is already present, the source IP appends to the header.

This configuration calls for WAF to read the source IP from the XFF header. WAF uses it in place of the source IP for IP blocking functions, and when logging blocked requests. The client can set the XFF  header which should not be trusted by default. While this behavior conforms to standards, it is not always recommended if some or all requests pass through some other proxy server.

For that reason, WAF only extracts a client source IP from the XFF header from those IP addresses that are designated as trusted proxies. When extracting the source IP from the header, WAF uses the last IP address in the XFF  list.

### Reset X-Forwarded-For header to last untrusted source in list                

The XFF header may contain a comma separated list of IP addresses. Depending on the configuration options in the endpoint web server and application, the XFF header may be logged as a comma separated list of IP addresses, which is not desirable.

WAF can forward the XFF header as a single IP address. For applications that cannot select an IP address in the list, this configuration enables the XFF header as a replacement of the client source IP.

To enable the XFF  header:

1. On the Websites page, click the website you want to change.
2. Click **ADC**, and then click **Virtual host**.
3. Under **Trusted Proxy**, select  **Reset X-Forwarded-For header to last untrusted source in list**.
4. Click **Save settings**, and then click **Apply changes**.

When the XFF  header is enabled, the behavior differs depending on whether the request is from a trusted proxy or an untrusted proxy.

#### **Trusted proxy**

If a trusted proxy makes the request, the list of IP addresses in the XFF  header replaces the last untrusted IP address in that list.

A client with an IP address of 10.10.10.10 makes a request through a forward proxy with an IP address of 10.200.200.20 through a load balancer with an IP address of 192.168.100.5 that is designated as a trusted proxy; and then through WAF with an IP address of 192.168.100.10. When the request reaches the web server, the XFF header and source IP are:

* Source IP: 192.168.100.10
* X-Forwarded-For: 10.200.200.20

#### **Untrusted proxy**

If an untrusted proxy makes the request, the list of IP addresses in the XFF header is replaced with the IP of the untrusted source.

A client with an IP address of 10.10.10.10 makes a request through a forward proxy with an IP address of 10.200.200.20, through a load balancer with an IP address of 192.168.100.5, that is not designated as a trusted proxy; and then through WAF with an IP address of 192.168.100.10. When the request reaches the web server, the XFF  header and source IP will be:

* Source IP: 192.168.100.10
* XFF: 192.168.100.5

### Keep X-Forwarded-For header from trusted proxy

When requests are received from a trusted proxy, you may want to leave the XFF  header unchanged and forward the header to the endpoint web server.

To configure your trusted proxy settings:

1. On the Websites page, click the website you want to change.
2. Click **ADC**, and then click **Virtual host**.
3. In the “List of trusted proxies,” add the IP address of one or more trusted proxies or networks as a single IP address or in CIDR notation.
4. If you want the X-Forwarded-For header from the trusted proxies to be left unchanged, select **Forward X-Forwarded-For and X-Forwarded-Pro to headers from trusted proxy unaltered**.
5. To reset the X-Forwarded-For header to the last source IP before either WAF or a trusted proxy, select **Reset X-Forwarded-For header to last untrusted source in list**.
6. Click **Save settings**, and then click **Apply changes**.

## X-Forwarded-For web server and application configuration

You can configure the endpoint application or web server to use the information in the XFF header rather than the client source IP. You can configure standard web applications like Wordpress, Drupal, and Sharepoint to use the XFF  header rather than the source IP. For server-based web analytic tools based on reading web server logs, you must configure the web server to log the XFF header information in addition to, or in place of, the client source IP.

However, the client can set the XFF header which results in the contents of the header being altered to contain false information. When WAF sets the XFF  header, the last address in the list cannot be forged. WAF receives a request of the source IP, which is the last address in the list.

Configure WAF to replace the header with the last untrusted source IP to ensure the X-Forwarded-For header can be trusted.

In the following examples, where possible, the last IP address in the XFF  list is extracted from the header.

### IIS 7 and later

To have IIS 7 log the XFF header, you must install the IIS Advanced Logging feature. You can download the module [here](http://www.iis.net/downloads/microsoft/advanced-logging).

After you install the module, you must add the XFF log field.

**To add the log field**:

1. Open the **Add Fields** box
2. Open IIS Manager.
3. In the Connections navigation pane, click the appropriate server, website, or directory for which you want to configure advanced logging.
4. On the Home page, in the IIS section, double-click **Advanced Logging**.
5. Under **Actions** on the right, click **Edit Logging Fields**.
6. Click **Add Fields**.

**To add your fields**:

1. In the Category list, select **Default**.
2. In **Field ID**, type <kbd>X-Forwarded-For</kbd>.
3. In the Source Type list, select **Request Header**.
4. In the Source Name field, type <kbd>X-Forwarded-For</kbd>.
5. In the **Add Logging** field, click **OK**.

**To define and enable advanced logging**:

1. Select a **Log Definition**. By default, there is only one: <kbd>%COMPUTERNAME%-Server</kbd>. The log definition you select must be **Enabled**.
2. Under **Actions**, click **Edit Log Definition**.
3. Click **Select Fields**, and then select **X-Forwarded-For logging field**.
4. Click **OK**.
5. Under **Actions**, click **Apply**.
6. Click **Return To Advanced Logging**.
7. Under **Actions**, click **Enable Advanced Logging**.

### Apache Web Server

Apache includes  built-in support for conditional logging based on environmental variables, which allows Apache Web Server to use the XFF header in place of the client source. This configuration is possible if the header is set and otherwise uses the client source IP.

This example is based on the following standard log format definition:

<kbd>LogFormat "%h %l %u %t \"%r\" %&amp;gt;s %b \"%{Referer}i\" \"%{User-agent}i\"" combined CustomLog log/acces_log combined</kbd>

To log the X-Forwarded-For header conditionally in place of the client source IP, change the above log definition to:

1. <kbd>LogFormat "%h %l %u %t \"%r\" %&amp;gt;s %b \"%{Referer}i\" \"%{User-Agent}i\"" combined</kbd>
2. <kbd>LogFormat "%{X-Forwarded-For}i %l %u %t \"%r\" %&amp;gt;s %b \"%{Referer}i\" \"%{User-Agent}i\"" proxy</kbd>
3. <kbd>SetEnvIf X-Forwarded-For "^.*\..*\..*\..*" forwarded</kbd>
4. <kbd>CustomLog "logs/access_log" combined env=!forwarded</kbd>
5. <kbd>CustomLog "logs/access_log" proxy env=forwarded</kbd>

In line 2, an additional log format which logs X-Forwarded-For in place of <kbd>%h</kbd> (remote host) is defined and named “proxy”.

In line 3, a simple regular expression matching an IP address is run against the X-Forwarded-Header and if it matches, an environment variable named “forwarded” is set.

In lines 4 and 5, the log formats are selected based on the status of the “forwarded” environment variable.

### Apache Tomcat

For versions of Apache Tomcat greater than version 6.0.21 or Tomcat 7, Remote IP Valve can automatically log the XFF header. When an IP address is present in the XFF header, the valve automatically logs it in place of the source IP.

To load the valve, add <kbd>org.apache.catalina.valves.RemoteIpValve</kbd> to server.xml before the <kbd>AccessLogValve</kbd> declaration.

For more information, see [this document](http://www.techstacks.com/howto/configure-access-logging-in-tomcat.html).

### Wordpress and other PHP based applications

To have functions that use <kbd>$_SERVER['REMOTE_ADDR']</kbd>, use the first IP address in the XFF header to replace the IP address in that variable with the last address in the XFF  list.

For Wordpress, place the code below at the top of wp-config.php:

<kbd>if(isset($_SERVER['HTTP_X_FORWARDED_FOR'])) { $xffaddrs = explode(',',$_SERVER['HTTP_X_FORWARDED_FOR']); $_SERVER['REMOTE_ADDR'] = end($xffaddrs); }</kbd>

### Drupal

Drupal directly supports operation behind a reverse proxy. Configuration options are similar to the WAF trusted proxy where it restricts the usage of the header to trusted proxies.

To configure Drupal to run behind WAF, add the following lines at the bottom of the settings.php file:

<kbd># Tell Drupal it's behind a proxy</kbd>

<kbd>$conf['reverse_proxy'] = TRUE;</kbd>

<kbd># Tell Drupal what addresses the proxy server(s) use</kbd>

<kbd>$conf['reverse_proxy_addresses'] = array('10.10.10.10','10.10.10.11');</kbd>

Where 10.10.10.10 and 10.10.10.11 are the IP addresses of the two WAF nodes in a WAF cluster.

### Sharepoint

If you want Sharepoint to use an IP address in the XFF  header in place of the source IP, you must install the  module, ARR helper.

As with Drupal, the module allows you to configure trusted proxies. For more information, [see this article](http://blogs.iis.net/anilr/archive/2009/03/03/client-ip-not-logged-on-content-server-when-using-arr.aspx).

## Transparent proxy

You can apply the transparent proxy as a configuration option to both the routing proxy and reverse proxy deployment modes. When client source IP is enabled, WAF inserts the client source IP in the request to the backend web server. Because WAF is spoofing the client source IP, this feature is sometimes called "client impersonation."

Transparent proxy preserves the client source IP in the HTTP requests, but can affect performance and availability. For every request, a new connection must be made, otherwise connections from other client IPs are used. The original client IP is inserted as the source IP of the connection made to the backend web server, and the newly created connection  impacts performance on the web server. When acting as a transparent proxy, WAF must be configured as the backend default gateway for the web server. Therefore, a transparent proxy requires an extra step, since the backend web server’s default gateway must change. For this reason, Alert Logic does not recommend a transparent proxy mode if you deploy WAF with a load balancer for a high-performance environment.

**Key elements of transparent proxy are the following**:

* Reinserts the client source IP before forwarding the request to the backend web environment.
* WAF inserts the client source IP as the source IP of the request it forwards to the backend web server.
* You must configure backend web servers to us WAF as the default gateway for the backend server response to be returned to the client.
* You must enable IP forwarding (routing) in WAF.
* Performance drawbacks may occur from connections from WAF to backend web servers.
* WAF must be the default gateway. 
The transparent proxy setting is only recommended for smaller deployments where WAF is not deployed in combination with a load balancer.

### Transparent proxy disadvantages

Transparent proxy has some disadvantages in terms of performance, complexity of administration, and lack of transparency in how the HTTP stack operates. This includes availability risk, because other network equipment or server OSes may not accept the transparent proxy fundamentally “lying to the network.” Spoofing the client for every request made to the web server also causes performance issues because TCP connections to the backend web server cannot be kept open and re-used. The repeated re-establishment of the TCP connection introduces added latency, which affects user experience, and ultimately can affect search engine position.

**Disadvantages of transparent proxy are the following**:

| Caveat | Reason |
|---|---|
| Poor performance | Lack of TCP keepalive |
| Complicated to take out of line in case a problem occurs | Web servers use the Web Security Manager proxy as the default gateway, and must be re-configured to use the network default gateway for the stack to work without Web Security Manager |
| Difficult to troubleshoot | Part of the network configuration is done on the web server. |
| Availability is not guaranteed | Transparent proxy relies on other network equipment and server OSes to accept it, which may not be the case after updates. |
| Testing is uncertain, including risks associated with applying updates and rebooting | Testing prior to releasing software updates to Web Security Manager is more uncertain in regards to uncovering potential issues with transparent proxy, because it depends on the surrounding network to accept it. This increases the risk associated with applying updates and rebooting the appliance in customer-specific networks. |

### Configure the transparent proxy

To minimize the availability impact on the web properties, configure the transparent proxy in the order described below.

If WAF is deployed as a cluster, create a cluster interface with a VIP that is reachable by the backend web servers.

1. On the Websites page, click **Services**, and then click **Network**.
2. Select **Enable IP Forwarding** in Network routing.
3. Check the Network segmentation table to verify routing does not violate network segmentation settings. Edit the segmentation table if necessary. By default, routing cannot cross network interfaces.
4. Configure backend web servers to use WAF as the default gateway.

**To configure the transparent proxy for each website in the website list:**

1. On the Websites page, under **ADC**, click **Virtual host**.
2. In the Client Source IP, under Transparent Proxy, select **Preserve client source IP**.
3. In the **ADC** tab, click **Load balancing**.
4. In the Advance settings, clear **Enable real server keepalive**.
5. Click **Save settings**, and then click **Apply changes**.
