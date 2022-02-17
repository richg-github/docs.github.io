# Caching

The ADC Caching page includes the following sections. Click on the link to go to the corresponding section to learn more:

<!--<MadCap:menuProxy mc-linked-toc="$topicHeadings" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />-->
To go to the documentation for the previous section of ADC, see [Load Balancing](ref_services_load_balancing.md). To go to  the documentation for next subsection in the ADC section, see [Application Delivery Controller (ADC) Acceleration](ref_services_acceleration.md).

**To access the Caching page in the WAF management interface**:

1. On the left panel, under Services, click **Websites**.
2. On the Websites page, click the website you want to manage.
3. Under ADC, click **Caching**.

To save configuration changes or edits you make to any features and options, you must click **Save** on the lower-right of the section or page where you are making changes. Click **apply changes** on the upper-left corner of the page, and then click **OK**. Your changes will not be stored if you do not properly save your changes.

### Static Caching                  

Alert Logic Managed Web Application Firewall (WAF) locally stores documents that can be cached. Any further requests for documents found in the cache are automatically delivered to clients directly from WAF. The back-end web servers can focus on delivering dynamic content with improved response times to clients, without the overhead of delivering static content like images, PDF documents, static HTML documents, style-sheets and others.

Caching content must only be activated where appropriate as caching. In particular for dynamic content, which involves the risk of losing confidentiality to private data.

<colgroup></colgroup>| **              Enable static content caching            ** Checkbox | If enabled, WAF stores static content from the web-server locally on WAF. This dramatically accelerates response times and off-loads the web-server. Default: `<enabled>` |
| **              Default caching action            ** Input field | WAF can either cache all responses unless  the backend server explicitly instructs no-cache or only cache content with response headers that indicate that the response is cache-able.<dl><dt>                Cache unless specifically instructed not to              </dt><dd>Cache all responses but honors Expires, Cache-Control: no-cache, private and no-store headers.</dd><dt>                Do not cache unless headers indicate content is cacheable              </dt><dd>Only cache responses if headers Expires, Cache-Control or Last-Modified indicates that the content is cache-able.</dd></dl> |
| **              Inactive remove threshold            ** Input field | Defines how long to keep data that is not requested in the cache.<dl><dt>                Valid input              </dt><dd>Number (seconds)</dd><dt>                Default value              </dt><dd>`3600`</dd></dl> |
| **              Default caching time            ** Input field | Response code defines  how long to store cached responses in cache if backend serve does not set rexpiration.<dl><dt>                Valid input              </dt><dd>List of error codes and seconds.</dd><dt>                Default value              </dt><dd>`200 302 301 = 3600`
`404 = 600`
`any = 10` (any error code not specified directly).</dd></dl> |

### Dynamic caching

Use this option only appropriate when the dynamically served content has the characteristics of static content. An example of this data can be news articles generated from a database.

If appropriate, the effect of dynamic content caching can be dramatic. For instance, if an article on a news site is requested at a rate of 100 requests/sec, enabling caching with a content expiry of 20 seconds results in 1 in every 2000 requests reaching the web server. The remaining 1999 is served from the WAF cache.

Caching content must only be activated where appropriate as caching. In particular for dynamic content, which involves the risk of losing confidentiality to private data.

<colgroup></colgroup>| **              Enable dynamic content caching            ** Check box | If enabled, WAF store a dynamic content from the web server locally for a configurable number of seconds. Default: `<disabled>` |
| **              Dynamic content expiry            ** Input field | Store dynamically cached documents for the specified period.<dl><dt>                Valid input              </dt><dd>Number (seconds)</dd><dt>                Default value              </dt><dd>`60`</dd></dl> |
| **              Caching locations            ** | Cache response from requests matching regular expressions. Enter regular expressions to match part of, or the entire path part you want cached. The expressions match from left to right. Full match is not implied, but matching always start at the beginning of line. For example, the expression`/news` will match any URI that starts starting with` /news`.<dl><dt>                Valid input              </dt><dd>A valid regular expression</dd><dt>                Input example              </dt><dd>`/news/.+\.php` cache responses from php scripts served from locations in and below the directory news.</dd><dt>                Default value              </dt><dd>`none`</dd></dl> |

### Lower button bar                  

<colgroup></colgroup>| **              Flush DYNAMIC cache            ** | Delete the contents of the website proxy static document cache. |
| **              Flush STATIC cache            ** | Delete the contents of the website proxy static document cache. |
| **              Default values            ** | Revert to default values. |
| **              Save settings            ** | Click **Save settings** to save settings. |
