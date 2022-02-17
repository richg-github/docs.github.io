# Load Balancing

The ADC Load Balancing page includes the following sections. Click on the link to go to the corresponding section to learn more:

<!--<MadCap:menuProxy mc-linked-toc="$topicHeadings" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />-->
To go to the documentation for the previous section of ADC, see [Caching](ref_services_caching.md). To go to  the documentation for next subsection in the ADC section, see [Application Delivery Controller (ADC) Acceleration](ref_services_acceleration.md).

**To access the Load Balancing page in the WAF management interface**:

1. On the left panel, under Services, click **Websites**.
2. On the Websites page, click the website you want to manage.
3. Under ADC, click **Load Balancing**.

To save configuration changes or edits you make to any features and options, you must click **Save** on the lower-right of the section or page where you are making changes. Click **apply changes** on the upper-left corner of the page, and then click **OK**. Your changes will not be stored if you do not properly save your changes.

### Real web servers

<colgroup></colgroup>| **              Real server protocol            ** Drop-down list | HTTP or HTTPS<dl><dt>                Valid input              </dt><dd>Options from the drop down list
`HTTP` or `HTTPS`
HTTPS is only available if website virtual host is SSL-enabled.</dd><dt>                Default value              </dt><dd>The protocol initially set when the website proxy was created.</dd></dl> |
| **              Real host            ** Input field | Hostname or IP address of the web-server(s) Alert Logic Managed Web Application Firewall (WAF) is proxying requests for.<dl><dt>                Valid input              </dt><dd>Fully qualified hostname (FQDN) or IP address.</dd><dt>                Input example              </dt><dd>`web1.mycompany.com`
`10.10.10.10`</dd><dt>                Default value              </dt><dd>`&amp;amp;lt;none&amp;amp;gt;`</dd></dl> |
| **              Port            ** Input | The port number the real server is listening to.<dl><dt>                Valid input              </dt><dd>A valid TCP/IP Port number</dd><dt>                Default value              </dt><dd>`80`</dd></dl> |
| **              Role            ** Drop-down list | Define the servers role in the load balancing set.<dl><dt>                Active              </dt><dd>The server is operative and accepts requests.</dd><dt>                Backup              </dt><dd>The server is operative but should only be sent requests if none of the other servers in the load balancing set are available.</dd><dt>                Down              </dt><dd>The server is nor operative and will not respond to requests.</dd></dl> |
| **              Status            ** Read only | The status of the real server. `enabled`               or `disabled`. |
| **              X (delete)            ** Button | Mark the real server for deletion. The server is not deleted until the button **Save settings** in the lower button is clicked. |
| **Add new server** Button | Click to add a new server. |

### Timeouts                  

<colgroup></colgroup>| **              Real server CONNECT timeout (seconds)            ** Input field | Max time to wait for connection to the backend web server to succeed.<dl><dt>                Unit              </dt><dd>Seconds</dd><dt>                Valid input              </dt><dd>Number in range 2 - 75</dd><dt>                Default value              </dt><dd>`10`</dd></dl> |
| **              Real server SEND timeout            ** Input field | Max time to wait for sending request to backend web server to complete.<dl><dt>                Unit              </dt><dd>Seconds</dd><dt>                Valid input              </dt><dd>Number in range 2 - 7200</dd><dt>                Default value              </dt><dd>`60`</dd></dl> |
| **              Real server READ timeout            ** input field | Max time to wait for reading response from backend web server.<dl><dt>                Unit              </dt><dd>Seconds</dd><dt>                Valid input              </dt><dd>Number in range 2 - 7200</dd><dt>                Default value              </dt><dd>`60`</dd></dl> |

### Load balancing settings

The load balancing settings control the behavior of the *Load Balancer*.

<colgroup></colgroup>| **              Web Security Manager COOKIE based session persistence            ** Checkbox | When selected, WAF issues a cookie when a user first connects to the virtual host being proxied / load balanced. The load balancer ensures that the users session with the real server is not broken to which the cookie binds the session. This method requires that visitors have cookies enabled in their browser. Despite the name, this feature works equally well with HTTPS and HTTP. |
| **              HEADER based session persistence            ** Checkbox | When selected, WAF binds the user session to the real server based on a hash of a selected client request header. |
| **              Header            ** Input field | The header to use for calculating load balancing hash when header based session persistence is selected.<dl><dt>                Valid input              </dt><dd>An HTTP-header the client sent.</dd><dt>                Default value              </dt><dd>User-Agent</dd></dl> |
| **              SOURCE IP based session persistence            ** Checkbox | When selected, WAF binds the user session to the real server based on the visitors source IP. This method ensures that requests from visitors with cookies disabled are sent to the same server every time. To compensate for visitors changing IP address during the session (for instance because their requests are sent through different forward proxies), a mask is applied to the users source address (below). Applying a mask ensures that even if the users IP address changes the same server is selected. |
| **              IP mask:             ** Drop-down list | The mask to be applied to the visitors source ip address when calculating destination real server based on source hashing. The mask and resulting number of IP addresses within each "load balancing address chunk" is displayed in the drop down.<dl><dt>                Valid input              </dt><dd>Options from the drop down list</dd><dt>                Default value              </dt><dd>255.255.240.000 (4,096 hosts)</dd></dl> |
| **              Enable real server failover            ** Checkbox | When selected, WAF attempts to redirect a request to another real server in case the real server to which the session is bound fails. Disabling real server failover is only effective when session persistence is enabled. If real server failover is disabled, the user receives an error message and the session must be restarted (usuallyby closing and restarting the browser). |
| **              Max real server failover attempts            ** Input field | Maximum failover attempts in case a real server fails. This value defines how many times WAF tries other real servers in case a real server fails.<dl><dt>                Valid input              </dt><dd>Number in range 1 - (number of real servers -1)</dd><dt>                Input example              </dt><dd>`1`</dd><dt>                Default value              </dt><dd>`1`</dd></dl> |
| **              Real server retry interval (seconds)             ** Input field | Specifies for how long a failed real server is kept in error state before it tries to connect again.<dl><dt>                Valid input              </dt><dd>Number in range 1 -</dd><dt>                Input example              </dt><dd>`20`</dd><dt>                Default value              </dt><dd>`60`</dd></dl> |

### Health Checking

Health checking checks the real (backend) servers for errors and availability. If a server is not responding correctly (as configured), it is disabled until it responds correctly again.

<colgroup></colgroup>| **              Enable real server health checking            ** Checkbox | Enable / disable health checking Default: `<disabled>` |
| **              Request interval            ** Input field | How often the health check daemon checks the server.<dl><dt>                Valid input              </dt><dd>Number in range 10 - 60</dd><dt>                Default value              </dt><dd>`10`</dd></dl> |
| **              Request timeout             ** Input field | Max time to wait for real server to respond before marking the attempt as failed.<dl><dt>                Valid input              </dt><dd>Number in range 1 - 30</dd><dt>                Default value              </dt><dd>`2`</dd></dl> |
| **              Error threshold            ** Input field | Specifies how many failed health checks are recorded before the server is disabled.<dl><dt>                Valid input              </dt><dd>Number in range 1 - 10</dd><dt>                Default value              </dt><dd>`3`</dd></dl> |
| **              Request method            ** Drop-down list | What method is used for health checking.<dl><dt>                Valid input              </dt><dd>`HEAD` or `GET`</dd><dt>                Default value              </dt><dd>`HEAD`</dd></dl> The HEAD method only checks the server response code. If the server returns 200 OK within the configured timeout the request is a success. The GET method validates the page the server returns using a checksum. If the content of the page has changed (compared to the stored checksum) the request is marked as failed. If the request method is GET and the content of the requested resource is changed on all servers, all servers are disabled as they will fail the checksum check. Ensure to run a checksum re-generation immediately after this update. |
| **              Request path            ** Input field | The resource to request when health checking.<dl><dt>                Valid input              </dt><dd>A string starting with / specifying an application, static page, graphic or other content on the web server.</dd><dt>                Input example              </dt><dd>`/testpage.php`
`/index.aspx?showpage=999999`
`/graphics/1x1.gif`</dd><dt>                Default value              </dt><dd>``&amp;amp;lt;none&amp;amp;gt;``</dd></dl> |
| **              Force checksum re-generation            ** Checkbox | When request method GET is selected and settings are saved, WAF request the configured resource on all real servers to calculate a checksum. This is stored for further health checking. If the checksum is not the same on all servers, WAF returns an error and the new settings are not saved. The checksum is only generated when things change, like when a new request is configured or method is changed to GET. There can be situations where you want to have the checksum re-generated like if the content of the request page has changed. If this option is checked, the checksum is re-generated. Default: <`disabled`> |
| **              Action on failure            ** Option | Disable real server Log only |

### Insert request headers                  

These settings allow for inserting new headers with either a static value or with the value of different request variables.

<colgroup></colgroup>| **              Enable alternative host header            ** Checkbox | Enable/disable alternative host header. Default: <`disabled`> |
| **Host** Input field | Enter the alternative host header |
| **              Enable insert request headers            ** Checkbox | Enable/disable request headers insert. Default: <`disabled`> |
| **              Header             ** Input field | The name of the request header to insert<dl><dt>                Valid input              </dt><dd>Alphanumeric and -</dd><dt>                Input example              </dt><dd>`Foo-Bar`
`Client-IP`</dd><dt>                Default value              </dt><dd>``&amp;amp;lt;none&amp;amp;gt;``</dd></dl> |
| **              Value type            ** Drop-down list | Specify the type of input entered in the value field.<dl><dt>                variable              </dt><dd>Specifies  the value variable string in the field is interpreted as the name of a request variable, the value of which is inserted in the request with the header name specified.</dd><dt>                literal              </dt><dd>Specifies that the value string entered in the  field is inserted "as is". If "foo" is entered, the value "foo" is inserted.</dd></dl> |
| **              Condition            ** Input field | Enter the condition header |
| **              Value            ** Input field | The value to insert in the new header field can be literal or variable.<dl><dt>                Valid input              </dt><dd>If literal selected:
alphanumeric, space, dash, underscore, space and comma.
If variable selected:
See list below.</dd><dt>                Input example              </dt><dd>`remote_addr` - the IP address of the client</dd><dt>                Default value              </dt><dd>``&amp;amp;lt;none&amp;amp;gt;``</dd></dl> |
| **              X (delete)            ** Button | Mark the header for deletion. The server is not deleted until the button **Save settings** in the lower button is clicked. |

#### Request header variables

The variables below can be inserted in a header and forwarded to the backend server.

* `args`: This variable is the GET parameters in request line, e.g.<kbd>foo=123&amp;amp;bar=blahblah</kbd>.
* `cookie_COOKIE`: The value of the cookie COOKIE, e.g. to forward the value of the cookie SESSID enter `cookie_SESSID` or `cookie_sessid` as match is case insensitive.
* `hostname`: Set to the hostname of the WAF node.
* `http_HEADER`: The value of the HTTP header `HEADER` when converted to lowercase and with dashes converted to underscores, e.g. `User-Agent
 = http_user_agent`, `Referer = http_referer`
* `remote_addr`: The IP address of the client.
* `remote_port`:                   The port of the client.
* `request_method`: The method of request, usually GET or POST.
* `request_uri`: The original request URI as received from the client including the args.
* `scheme`: The HTTP scheme (i.e. http, https).
* `server_name`: The virtual host server name of the website proxy handling the request (i.e. www.alertlogic.com).
* `server_port`: The port of the server, to which the request arrived.
* `server_protocol`: The protocol of the request, e.g. HTTP/1.0 or HTTP/1.1.
* `uri`: The URI in the request without arguments, those are in the variable args.

### Advanced settings

These settings specify request time out, keep alive behavior. Web application behavior settings is also specified here.

<colgroup></colgroup>| **              Enable real server keepalive            ** Checkbox | Enable/disable support for keepalive to backend web servers. If enabled, WAF keeps connections to the backend web servers open and reuse then for new requests. This reduces the overhead of establishing the connection. Default: `<enabled>` |
| **Number of keep-alive connections to keep open** Drop-down list |  |
| **              Add HTTP/1.1 VIA header information            ** Checkbox | Enable/disable support for HTTP/1.1 VIA header sending information. If enabled, WAF appends the Via header in each forwarded request indicating to the backend server that the request if coming through a proxy server. Default: `<disabled>` |
| **              Upstream SSL session reuse enable            ** Checkbox | SSL session reuse to backend servers. When WAF connects to a backend server over SSL, the server creates a session for that connection. This session ID is sent as a part of the backend `Server Hello` message. To make things efficient, WAF behaves as a normal HTTP client (a browser) and reuses that session ID next time it connects to the backend server. This allows time saved from verifying the certificates and negotiating the keys. If the backend web server is configured to not support SSL, session reuse pages does not load or not load correctly - typically stylesheets, images, javascript files, etc. To account for this, disable upstream SSL session reuse Default: `<enabled>` |
| **              Upstream SSL session reuse enable            ** Checkbox |  |
| **              Proxy buffering enable            ** Checkbox | Proxy buffering. By default, WAF buffers the response from the backend web server for the web server to deliver the request as fast as possible regardless of how slow the connection is to the client. This ensures that clients do not consume the server resourceson slow connections. However, some applications are known to have problems with this behavior, like Comet applications. To account for such problems, disable proxy buffering. Default: `<enabled>` |
| **              Number of proxy buffers            ** List |  |
| **              Size of proxy buffers            ** List |  |
| **              Size of buffer for first response            ** List |  |
| **              Enable proxy interface IP sharding            ** Checkbox | SSL session reuse to backend servers. When WAF connects to a backend server over SSL, the server creates a session for that connection. This session ID is sent as a part of the backend `Server Hello` message. To make things efficient, WAF can behave as a normal HTTP client (a browser) and reuse that session ID next time it connects to the backend server. Thus the time spent in verifying the certificates and negotiating the keys is saved. If the backend web server is configured to not support SSL session reuse pages will not load or not load correctly - typically stylesheets, images, javascript files, etc will not load. To account for such problems disable upstream SSL session reuse Default: `<enabled>` |

### Lower button bar

<colgroup></colgroup>| **              Save settings            ** | Click **Save settings** to save settings. |
