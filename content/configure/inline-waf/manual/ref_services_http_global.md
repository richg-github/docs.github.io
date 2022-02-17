# Global

The Service Global page includes the following sections. Click on the link to go to the corresponding section to learn more:

<!--<MadCap:menuProxy mc-linked-toc="$topicHeadings" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />-->
To go to the documentation for the previous section of Services, see [Websites](ref_services.md). To go to  the documentation for next subsection in the Services section, see [Network](ref_services_network.md).

To manage website security profiles, under Services  on the left panel, click **Websites** to go to the Website Overview page, and then click the **Global** tab.

To save configuration changes or edits you make to any features and options, you must click **Save** on the lower-right of the section or page where you are making changes. Click **apply changes** on the upper-left corner of the page, and then click **OK**. Your changes will not be stored if you do not properly save your changes.

Global HTTP settings that affect all websites.

### Source based blocking

When a client source IP is deployed behind a layer 7 proxy (for instance, a load balancer), the original client source IP becomes lost. This happens because the proxy (or proxies) terminate the requests that pass through before reaching Alert Logic Managed Web Application Firewall (WAF), and then reconnects to WAF on behalf of the client. The connection source IP, as seen from WAF, will then be the source IP of the proxy. Since all requests  appear as if they come from the proxy before they reach WAF, source IP based blocking controls apply to the proxy, and consequently all traffic is blocked.

If you want to use source IP based blocking controls, you can configure WAF to enforce the controls at the application layer instead of at the network layer. When an IP is blocked, WAF does not send a response to a request. This is the equivalent of "silent drop" at the network level.

The controls are enabled or disabled by a global master switch. When enabled, blocking is either enabled for single websites or  enforced for all websites with a global master switch.

<colgroup></colgroup>| **              Application layer source IP blocking enabled            ** Check box | Global master switch to enable or disable the application layer blocking feature. When enabled,  the application layer blocking feature will be enforced for all websites. Default: `<disabled>` |
| **              Enable application layer source blocking for all websites            ** Check box | Turn application layer source blocking on for all websites regardless of single website configuration. This is useful when all websites are being repeatedly and systematically attacked from one or more source IPs. Default: `<disabled>` |

### Response logging

<!--Need information for Response logging -->
<colgroup></colgroup>| **                Response logging for allowed violations enabled              ** Check box | Default: `<disabled>` |
| **                Enable response logging for all websites              ** Check box | Default: `<disabled>` |

### Response inspection

<!-- Need information for Response inspection table -->
<colgroup></colgroup>| **                Response inspection enabled              ** Check box | Default: `<disabled>` |
| **                Enable response inspection for all websites              ** Check box | Default: `<disabled>` |
| **                Enable global settings override              ** Check box | Default: `<disabled>` |
| **                  Extensionless maximum URL path depth levels                ** Input field | Valid input numeric Default value: `3` |
| **Response header normality limit** Drop-down list | Default: `<disabled>` |
| **                Response body normality limit              ** Drop-down list | Default: `<> 0.0032%, Z = 4.0>` |
| **                Request time normality limit              ** Drop-down list | Default: `<disabled>` |
| **Server response time normality limit** Drop-down list | Default: `<disabled>` |
| **                Text Code ratio normality limit              ** Drop-down list | Default: `<> 0.0032%, Z = 4.0>` |
| **                Maximum text chunk normality limit              ** Drop-down list | Default: `<> 0.0032%, Z = 4.0>` |
| Anomaly detection response codes               Input field | Valid input            <dd>numeric</dd><dt>              Default value            </dt><dd>`&amp;lt;empty&amp;gt;`</dd> |

<!-- Need information for Response inspection -->
### Server ID

The server ID is the name of the server that is sent in the response header "Server," and is also called the server banner.Alert Logic recommends you hide, mask, or alter the server banner.

The server id can be set for each website proxy, or globally for all websites.

<colgroup></colgroup>| **              Enforce server id for all website proxies            ** Check box | Enable / disable to enforce the global server id for all websites. Default: `<disabled>` |
| **              Server ID            ** Input field | The global server ID. An empty string completely removes the server ID (prevent sending the Server header).<dl><dt>                  Valid input                </dt><dd>alpha-numeric, space, dash, slash, underscore, period and parentheses</dd><dt>                  Default value                </dt><dd>`&amp;amp;lt;empty&amp;amp;gt;`</dd></dl> |

### HTTP request throttling

HTTP request throttling tracks client request rate across all websites and enforces configured limits. When WAF is configured to be aware of receiving the request from proxies at the application layer ([Trusted proxy](ref_services_virtual_host.md#ref_services_client_source_ip.md)), these controls are transparently enforced at the application layer.

<colgroup></colgroup>| **              Enable client HTTP request throttling            ** Check box | Enable / disable HTTP request throttling for all websites. Default: `<disabled>` |

#### Max HTTP request rate throttling zones

Client request rate is tracked across website proxies using four global databases, throttling zones. To account for different usage patterns, throttling limits are defined separately for each global throttling zone.

<colgroup></colgroup>| **              Zone T1, T2, T3 and T4            ** Input field | Each zone defines a maximum request rate in seconds. If for instance a website proxy is assigned to Zone T3, client requests to that site are throttled down to a maximum of 5 req/sec per IP. As the aim of throttling client requests typically is to prevent clients from consuming excessive system resources, request throttling is not enabled on a global basis and client requests are tracked and throttled across all websites. This means that in the above example client requests are tracked across all website proxies and that the Zone T3 limits enforced for other websites using Zone T3. By default, Zone T1 is selected for all sites.<dl><dt>                  Unit                </dt><dd>Requests / second</dd><dt>                  Valid input                </dt><dd>Number in the range 0 - 1000000</dd><dt>                  Default value                </dt><dd>`T1 = 50, T2 = 10, T3 = 5, T4 = 1`</dd></dl> |

#### Website settings

<colgroup></colgroup>| **              Maximum burst rate            ** Input field | The amount of requests the client is allowed to exceed with the allowed request rate. If for instance, the maximum burst rate is set to 20 and the request rate is limited to five request per second, then the client may issue 20 requests for one second, but has to wait 4 seconds until the rate is balanced. When a client for instance loads an HTML page, it typically results in a lot of sub-requests for graphic elements, style sheets, javascript, etc. Setting a reasonable burst rate will allow for fast page loads when the request rate is limited.<dl><dt>                  Unit                </dt><dd>requests / second</dd><dt>                  Valid input                </dt><dd>Number in the range 0 - 1000000</dd><dt>                  Default value                </dt><dd>`20`</dd></dl> |
| **              Throttling action            ** Drop-down list | How to handle clients exceeding limits.<dl><dt>                  Delay                </dt><dd>Slow down the client by delaying responses
Default selection</dd><dt>                  Error 503                </dt><dd>Return HTTP error 503</dd></dl> |
| **              Throttling zone            ** Drop-down list | Client request rate is tracked across website proxies using four global databases, throttling zones. To account for different usage patterns, throttling limits are defined separately for each global throttling zone. |
| **              Precedence            ** Drop-down list | The global website settings can either be default settings when a website is created or enforced settings for all websites.<dl><dt>                  Default web site settings                </dt><dd>When creating a website the settings defaults to the global website settings.</dd><dt>                  Enforced for all websites                </dt><dd>The global website settings are enforced for all websites overruling settings defined in website proxies.</dd></dl> |

### HTTP connection limiting

HTTP connection limiting tracks client connection concurrency across all websites and enforces configured limits.

When WAF is configured to be aware of receiving the request from proxies at the application layer ([Trusted proxy](ref_services_virtual_host.md#ref_services_client_source_ip.md)), these controls are transparently enforced at the application layer.

<colgroup></colgroup>| **              Enable client HTTP connection limiting            ** Check box | Enable / disable connection limiting for all websites. Default: `<disabled>` |

#### Max HTTP connections limiting zones

Client connection concurrency is tracked across website proxies using four global databases, connection limiting zones. To account for different usage patterns, connection limits are defined separately for each global limiting zone.

<colgroup></colgroup>| **              Zone L1, L2, L3 and L4            ** Input field | Each zone defines maximum allowed concurrent connections per client IP. If for instance a website proxy is assigned Zone L1, client IPs are not allowed to establish more than four concurrent connections to the website proxy. However, as client connections are tracked across all website proxies, the limits are also tracked and enforced for other websites using Zone L1. Browsers typically establish up to four concurrent connections when loading a web page, however many clients access the website from behind the same gateway and this can result in a much higher concurrency from that IP. By default, Zone L1 is selected for all sites.<dl><dt>                  Unit                </dt><dd>Requests / second</dd><dt>                  Valid input                </dt><dd>Number in the range 0 - 1000000</dd><dt>                  Default value                </dt><dd>`L1 = 100, L2 = 20, L3 = 10, L4 = 4`</dd></dl> |

#### Web site settings

<colgroup></colgroup>| **              Limiting zone            ** Drop-down list | Client request rate is tracked across website proxies using four global databases, throttling zones. To account for different usage patterns throttling, limits are defined separately for each global throttling zone. |
| **              Precedence            ** Drop-down list | The global website settings can either be the default settings for when a website is created or enforced settings for all websites.<dl><dt>                  Default web site settings                </dt><dd>When creating a website, the settings default to the global website settings.</dd><dt>                  Enforced for all websites                </dt><dd>The global website settings are enforced for all websites, overruling settings defined in website proxies.</dd></dl> |

### SSL

SSL operations consume extra CPU resources. The most CPU-intensive operation is the SSL handshake.

There are two ways to minimize the number of these operations per client:

* Enabling keepalive connections to send several requests via one connection (this is done for single websites in the [Acceleration page](ref_services_acceleration.md#ref_services_acceleration.md).
* Reusing SSL session parameters to avoid SSL handshakes for parallel and subsequent connections.

This section applies to optimizing SSL by configuring SSL session timeouts and the SSL session cache.

<table>
  <colgroup>
    <col></col>
    <col></col>
  </colgroup>
  <tbody>
    <tr>
      <td>
        <b>               SSL Session Timeout            </b>
        <p>Input field</p>
      </td>
      <td>
        <p>When to time out sessions stored in the session cache.</p>
        <p>Sessions are stored in the SSL session cache shared between worker processes and configured by the ssl_session_cache directive. 1 megabyte of cache contains about 4000 sessions. The default cache timeout is five minutes. This timeout can be increased using the ssl_session_timeout directive. Below is a sample configuration optimized for a multi-core system with 10 megabyte shared session cache:                              </p>
        <dl>
          <dt>                  Unit                </dt>
          <dd>
            <p>Minutes</p>
          </dd>
          <dt>                  Valid input                </dt>
          <dd>
            <p>Number in the range 1 - 60</p>
          </dd>
          <dt>                  Default value                </dt>
          <dd>
            <p>
              <code>10</code>
            </p>
          </dd>
        </dl>
      </td>
    </tr>
    <tr>
      <td>
        <b>               SSL Session Cache            </b>
        <p>Drop-down list</p>
      </td>
      <td>
        <p>SSL session cache size in number of SSL sessions.</p>
      </td>
    </tr>
    <tr>
      <td>
        <b>               Name Based Virtual Hosts (SNI)            </b>
        <p>Drop-down list</p>
      </td>
      <td>
        <p>Enable / Disable Server Name Indication.</p>
        <p>Allow several HTTPS sites using the same IP address.</p>
        <p>If enabled WAF, allows binding an HTTPS virtual host to an IP address that is already in use by another HTTPS host.                              </p>
        <p>Clients supporting TLS SNI (Server Name Indication) includes the requested hostname in the first message of the SSL handshake (connection setup). This allows the server to determine the correct named virtual host for the request and set the connection up accordingly using the correct vhost SSL certificate from the start. Clients not supporting SNI do not include the requested hostname and are served the certificate from the first vhost using the shared IP.                              </p>
        <p>The most common browsers support of SNI is:</p>
        <ul>
          <li>Mozilla Firefox 2.0 or later</li>
          <li>Opera 8.0 or later (with TLS 1.1 enabled)</li>
          <li>Internet Explorer 7.0 or later (not XP)</li>
          <li>Google Chrome </li>
          <li>Safari 3.2.1 on Mac OS X 10.5.6</li>
        </ul>
        <p>Since there is still a lot of XP based IE users out there it is not recommended to rely on SNI if broad SSL support is required. Create some more virtual IP addresses instead (cluster or virtual IPs.                              </p>
        <p>Default <code>&amp;lt;disabled&amp;gt;</code>.                              </p>
      </td>
    </tr>
    <tr>
      <td>
        <p>
          <b>SNI Client Authentication</b>
          <!--Need information for SNI Client Authentication. -->
        </p>
        <p>Drop-down list</p>
      </td>
      <td>
        <p>Default <code>&amp;lt;Disallowed&amp;gt;</code>.                              </p>
      </td>
    </tr>
  </tbody>
</table>### HTTP global request limit

Sets the maximum upload / request size that is allowed across all websites. Maximum configurable value is 1073741824 bytes (1 GB).

### HTTP error log level

Sets the log level for proxy core engine error logging to the Proxy log, in [Logs under System.](ref_system_logs.md#ref_system_logs.md)

### HTTP global access logging

Enable or disable debug access logging. When enabled, every website configured on an appliance keeps an access log that is rotated every three days. These logs are available in the WAF log directory prefixed with "debug." When normal access logging is enabled for a website, WAF does not log to the debug file.

### Proxy protocol

Alert Logic allows you to enable proxy protocol for all listen address, which is designed to safely transport connection information without losing any information. Enabling proxy protocol allows WAF to work with multiple layers of NAT or TCP proxy protocols, does not require infrastructure changes, has no impact on NAT firewalls, and is scalable.

Enabling proxy protocol  is not necessary unless you are configuring both communicating endpoints. If you have configured the other communicating endpoint to proxy protocol, you can enable proxy protocol in the WAF.

You must configure proxy protocol on both endpoints of the connection. If one endpoint connection is not configured to use proxy protocol, the websites stop communicating, and WAF does not function properly.
