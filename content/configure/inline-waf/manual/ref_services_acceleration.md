# Application Delivery Controller (ADC) Acceleration

The ADC Acceleration page includes the following sections. Click on the link to go to the corresponding section to learn more:

<!--<MadCap:menuProxy mc-linked-toc="$topicHeadings" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />-->
To go to the documentation for the previous section of ADC, see [Caching](ref_services_caching.md). To go to  the documentation for next section of the manual, see [Learning](ref_services_learning.md).

**To access the Acceleration page in the WAF management interface**:

1. On the left panel, under Services, click **Websites**.
2. On the Websites page, click the website you want to manage.
3. Under ADC, click **Acceleration**.

To save configuration changes or edits you make to any features and options, you must click **Save** on the lower-right of the section or page where you are making changes. Click **apply changes** on the upper-left corner of the page, and then click **OK**. Your changes will not be stored if you do not properly save your changes.

## Acceleration

Alert Logic Managed Web Application Firewall (WAF) accelerates web server performance by caching static content and compressing traffic to clients. Caching of static documents potentially improves performance by 300 - 500 percent, depending on the mix of static and dynamic content.Dynamic compression of transmission data potentially reduces bandwidth usage by 30 - 60 percent, which increases transfer rate by 50 - 100 percent.

### Compression

HTTP compression reduces the transfer volume of static and dynamically generated web pages to approximately one third of their original size proportionally speeds up the load time performance. This results in reduced traffic costs and in a better experience for the web site visitors.

The performance gain depends on the ratio of which content from the web server is compressed, size of the pages and the clients bandwidth.

#### Compression level

Set the gzip compression level which is a trade off between CPU resources and bandwidth consumption. High compression levels saves more bandwidth but consumes more CPU and vice versa.

The default compression level is set at 3 which is moderate but fast.

#### Compress response content-types,

Compression of server responses is based on the response content type.

<colgroup></colgroup>| **              Text            ** Checkbox | If enabled, WAF compresses HTTP documents matching content-type `text/*`. Default: `<enabled>` |
| **              Images            ** Checkbox | If enabled, WAF compresses HTTP documents matching content-type `image/*`. You usually do not need to enable compression  for images. Most images are already optimized/compressed for the web, which results in a waste of processing power if enabled. Default: `<disabled>` |
| **              Application data            ** Checkbox | If enabled, WAF compresses HTTP documents matching content-type `application/*`. Default: `<disabled>` |

#### Exceptions

In some cases, you may need to specify exceptions from the compression by content type policy. Exceptions are defined using regular expressions matching the path segment of the requested URL (the URI).

<colgroup></colgroup>| **              Enable Compression Exception by Regular Expression            ** Checkbox | If enabled, WAF matches the URI using the regular expressions in the list. If there is a match, compression is disabled for the server response. |
| **              Regular expression            ** Input fields | Enter regular expressions matching part of or the entire path part you want excluded from compression. Unlike filter policy regular expressions, the expression do not have to match the entire path from start to end. For example, `a` is a valid regular expression matching all paths containing an `a`, while `\.class` would match all paths containing `.class`.<dl><dt>                Valid input              </dt><dd>A valid regular expression</dd><dt>                Input example              </dt><dd>`^/forms/ `(do not compress responses from paths starting with /forms/)
`^.+\.jar `(do not compress responses from files with the extension `.jar`)</dd><dt>                Default value              </dt><dd>`none`</dd></dl> |

### HTTP connection reuse

HTTP connection reuses socket connections already established which dramatically improves response times for clients that have support for keep-alive.

<colgroup></colgroup>| **              Enable keep-alive requests            ** Checkbox | Enable / disable support for HTTP/1.1 keep-alive requests. If enabled, WAF supports keep-alive protocol specification as defined by HTTP/1.1 standard. Default: `<enabled>` |
| **              Max Keep-Alive requests            ** Input field | Maximum number of requests on a kept alive connection. This setting limits the number of requests allowed per connection when keep-alive requests is enabled. If it is set to 0, unlimited requests will be allowed.<dl><dt>                Valid input              </dt><dd>Number in range 0 - 10000</dd><dt>                Input example              </dt><dd>`100`</dd><dt>                Default value              </dt><dd>`10`</dd></dl> |
| **              Max Keep-Alive timeout            ** Input field | Max idle time on a keep alive connection. This value defines the number of seconds WAF waits for a subsequent request before closing the connection.<dl><dt>                Valid input              </dt><dd>Number (seconds) in range 1 - 300</dd><dt>                Default value              </dt><dd>`5`</dd></dl> Keep-Alive timeout sets the timeout on *idle* connections. As long as the connection is active (the client is requesting content with a maximum of keep-alive timeout between each request), the Max Keep-Alive requests value determines when the connection is closed and the client has to re-establish the connection. |
