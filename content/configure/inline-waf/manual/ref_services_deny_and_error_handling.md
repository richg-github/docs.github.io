# Deny and Error Handling

The Alert Logic Managed Web Application Firewall (WAF) Deny and Error Handling page includes the following sections. Click on the link to go to the corresponding section to learn more:

<!--<MadCap:menuProxy mc-linked-toc="$topicHeadings" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />-->
To go to the documentation for the previous section of Alert Logic Managed Web Application Firewall (WAF) management integration, see [Policy](ref_services_policy.md). To go to  the documentation for next subsection in the WAF section, see [Application Delivery Controller (ADC)](ch_adc.md).

**To access the Deny and error handling page in the WAF management interface**:

1. On the left panel, under Services, click **Websites**.
2. On the Websites page, click the website you want to manage.
3. Under WAF, click **Deny and error handling**.

To save configuration changes or edits you make to any features and options, you must click **Save** on the lower-right of the section or page where you are making changes. Click **apply changes** on the upper-left corner of the page, and then click **OK**. Your changes will not be stored if you do not properly save your changes.

When a request is blocked at the application level, WAF can either close the connection and not respond, send an HTTP error code along with an error message, or redirect the client to a URL.

### Deny action

WAF distinguishes between violations that are Query and Authentication. () and Parameter (given value for a known parameter failed the access policy)

<dl><dt>        URL Policy Violation      </dt><dd>Violations related generally to the URL like HTTP method and headers, path and parameter names.</dd><dt>        Parameter Policy Violation      </dt><dd>Violations related to the content of query parameters.</dd><dt>        Authentication Required      </dt><dd>Violations related to authentication and authorization.</dd></dl>
For each type a Deny Action can be configured.

<colgroup></colgroup>| **              Deny with [deny type]            ** Radio button | Display *404 not found* or *403 authentication required *error message. When a request is denied the corresponding error page (403 or 404) is displayed. Default: `<selected>` |
| **              Close connection             ** Radio button | Close the connection. When a request is denied WAF simply closes the connection. No response is sent to the offending client. Default: `<not selected>` |
| **              Redirect            ** Radio button | Redirect the request. When a request is denied WAF sends HTTP/302 and a Location redirect HTTP header which redirects the offending client to the URL configured. Default: `<not selected>` |

### Error messages

WAF intercepts error messages from the backend and replaces them with a generic customizable error page. These are also the pages that are displayed If WAF is configured to display an error message when a request is denied.

The error pages are customizable and timed redirects can be inserted.

#### Document not found (error 40x)

When a request is denied with an error message or if the backend server returns an HTTP error 40x (400 401 402 404 405 406 407 408 409 410 411 412 413 414 415 416 417) the `Document not found` page is displayed.

<colgroup></colgroup>| **                Heading              ** Input field | The heading of the message page.<dl><dt>                      Valid input                    </dt><dd>Any string</dd><dt>                      Default value                    </dt><dd>`Requested URL cannot be found`</dd></dl> |
| **                Message              ** Input field | The message displayed.<dl><dt>                      Valid input                    </dt><dd>Any string not containing html tags.
Newlines are transformed into &amp;amp;lt;br&amp;amp;gt;.
Use [b]text[/b] to put some text in bold typeface.
Use [p]paragraph text[/p] to insert paragraphs.</dd><dt>                      Default value                    </dt><dd>`We are sorry, but the page you are looking for cannot be found. The page has either been removed, renamed or is temporarily
 unavailable.`</dd></dl> |
| **                Error              ** Input field | The error message displayed.<dl><dt>                      Valid input                    </dt><dd>Any string</dd><dt>                      Default value                    </dt><dd>`HTTP 404 Not Found`</dd></dl> |
| **                Nav. back              ** Input field | The error page contains two navigation buttons. The **nav. back** button will take the user to the page the user came from.<dl><dt>                      Valid input                    </dt><dd>Any string</dd><dt>                      Default value                    </dt><dd>`Back to previous page`</dd></dl> |
| **                Nav. forward              ** Input field | The error page contains two navigation buttons. The **nav. forward** button will take the user to the web site homepage.<dl><dt>                      Valid input                    </dt><dd>Any string</dd><dt>                      Default value                    </dt><dd>`Proceed to homepage`</dd></dl> |
| **                Include redirect text and script              ** Check box | Enable / disable insertion of timed redirect javascript with corresponding text. If enabled a redirect text and a piece of javascript displaying a configurable countdown is displayed with the error text configured (above). Default: `<disabled>` |
| **                Redirect text              ** Input field | The redirect message displayed.<dl><dt>                      Valid input                    </dt><dd>Any string not containing html tags.
Newlines are transformed into &amp;amp;lt;br&amp;amp;gt;.
Use [b]text[/b] to put some text in bold typeface.
Use [p]paragraph text[/p] to insert paragraphs.
Use [countdown] to display countdown.
Use [link]link text[/link] to insert link to configured redirect target server.</dd><dt>                      Default value                    </dt><dd>`You will be redirected to a an error page in [countdown] seconds. [link]Click here[/link] to be redirected immediately.`</dd></dl> |
| **                Redirect delay              ** Input field | Idle session timeout specifies tha maximum duration of an idle session before it is dropped resulting in the user being logged out from the web site.<dl><dt>                      Valid input                    </dt><dd>A number (integer) in the interval 2 - 3600 (one hour).</dd><dt>                      Input example                    </dt><dd>60 - (one minute)</dd><dt>                      Default value                    </dt><dd>`10`</dd></dl> |
| **                Redirect URL              ** Input field | The URL to redirect to.<dl><dt>                      Valid input                    </dt><dd>A valid URL</dd><dt>                      Input example                    </dt><dd>`http://sorryserver.mydomain.tld`</dd><dt>                      Default value                    </dt><dd>`none`</dd></dl> |
| **                Alert Logic Managed Web Application Firewall (WAF) text              ** Read only Trial license only. | In WAF Trial error messages contains the message Alert Logic Managed Web Application Firewall (WAF) - TRIAL VERSION |

#### Authentication required (error 403)

When a client request fails authentication or resource authorization and the request is denied with an error message or if the backend server returns an HTTP error 403 the `Authentication required` page is displayed.

<colgroup></colgroup>| **                Heading              ** Input field | The heading of the message page.<dl><dt>                      Valid input                    </dt><dd>Any string</dd><dt>                      Default value                    </dt><dd>`Not allowed`</dd></dl> |
| **                Message              ** Input field | The message displayed.<dl><dt>                      Valid input                    </dt><dd>Any string</dd><dt>                      Default value                    </dt><dd>`Access to the page you are trying to access is restricted to authorized clients. Please contact the site administrator if
 this is an error.`</dd></dl> |
| **                Error              ** Input field | The error message displayed.<dl><dt>                      Valid input                    </dt><dd>Any string</dd><dt>                      Default value                    </dt><dd>`HTTP 403 Forbidden`</dd></dl> |
| **                Nav. back              ** Input field | The error page contains two navigation buttons. The **nav. back** button will take the user to the page the user came from.<dl><dt>                      Valid input                    </dt><dd>Any string</dd><dt>                      Default value                    </dt><dd>`Back to previous page`</dd></dl> |
| **                Nav. forward              ** Input field | The error page contains two navigation buttons. The **nav. forward** button will take the user to the web site homepage.<dl><dt>                      Valid input                    </dt><dd>Any string</dd><dt>                      Default value                    </dt><dd>`Proceed to homepage`</dd></dl> |
| **                Include redirect text and script              ** Check box | Enable / disable insertion of timed redirect javascript with corresponding text. If enabled a redirect text and a piece of javascript displaying a configurable countdown is displayed with the error text configured (above). Default: `<disabled>` |
| **                Redirect text              ** Input field | The redirect message displayed.<dl><dt>                      Valid input                    </dt><dd>Any string not containing html tags.
Newlines are transformed into &amp;amp;lt;br&amp;amp;gt;.
Use [b]text[/b] to put some text in bold typeface.
Use [p]paragraph text[/p] to insert paragraphs.
Use [countdown] to display countdown.
Use [link]link text[/link] to insert link to configured redirect target server.</dd><dt>                      Default value                    </dt><dd>`You will be redirected to a an error page in [countdown] seconds. [link]Click here[/link] to be redirected immediately.`</dd></dl> |
| **                Redirect delay              ** Input field | Idle session timeout specifies tha maximum duration of an idle session before it is dropped resulting in the user being logged out from the web site.<dl><dt>                      Valid input                    </dt><dd>A number (integer) in the interval 2 - 3600 (one hour).</dd><dt>                      Input example                    </dt><dd>60 - (one minute)</dd><dt>                      Default value                    </dt><dd>`10`</dd></dl> |
| **                Redirect URL              ** Input field | The URL to redirect to.<dl><dt>                      Valid input                    </dt><dd>A valid URL</dd><dt>                      Input example                    </dt><dd>`http://sorryserver.mydomain.tld`</dd><dt>                      Default value                    </dt><dd>`none`</dd></dl> |
| **                Alert Logic Managed Web Application Firewall (WAF) text              ** Read only Trial license only. | In WAF, Trial error messages contains the message Alert Logic Managed Web Application Firewall (WAF) - TRIAL VERSION |

#### Server error (error 50x)

When the backend server returns an HTTP error 50x (500 501 502 503 504 505 506 507) the `Server error` page is displayed.

<colgroup></colgroup>| **                Heading              ** Input field | The heading of the message page.<dl><dt>                      Valid input                    </dt><dd>Any string</dd><dt>                      Default value                    </dt><dd>`Requested URL cannot be found`</dd></dl> |
| **                Message              ** Input field | The message displayed.<dl><dt>                      Valid input                    </dt><dd>Any string</dd><dt>                      Default value                    </dt><dd>`We are sorry, but the page you are looking for cannot be found. The page has either been removed, renamed or is temporarily
 unavailable.`</dd></dl> |
| **                Error              ** Input field | The error message displayed.<dl><dt>                      Valid input                    </dt><dd>Any string</dd><dt>                      Default value                    </dt><dd>`HTTP 502 Bad Gateway`</dd></dl> |
| **                Nav. back              ** Input field | The error page contains two navigation buttons. The **nav. back** button will take the user to the page the user came from.<dl><dt>                      Valid input                    </dt><dd>Any string</dd><dt>                      Default value                    </dt><dd>`Back to previous page`</dd></dl> |
| **                Nav. forward              ** Input field | The error page contains two navigation buttons. The **nav. forward** button will take the user to the web site homepage.<dl><dt>                      Valid input                    </dt><dd>Any string</dd><dt>                      Default value                    </dt><dd>`Proceed to homepage`</dd></dl> |
| **                Include redirect text and script              ** Check box | Enable / disable insertion of timed redirect javascript with corresponding text. If enabled a redirect text and a piece of javascript displaying a configurable countdown is displayed with the error text configured (above). Default: `<disabled>` |
| **                Redirect text              ** Input field | The redirect message displayed.<dl><dt>                      Valid input                    </dt><dd>Any string not containing html tags.
Newlines are transformed into &amp;amp;lt;br&amp;amp;gt;.
Use [b]text[/b] to put some text in bold typeface.
Use [p]paragraph text[/p] to insert paragraphs.
Use [countdown] to display countdown.
Use [link]link text[/link] to insert link to configured redirect target server.</dd><dt>                      Default value                    </dt><dd>`You will be redirected to a an error page in [countdown] seconds. [link]Click here[/link] to be redirected immediately.`</dd></dl> |
| **                Redirect delay              ** Input field | Idle session timeout specifies tha maximum duration of an idle session before it is dropped resulting in the user being logged out from the web site.<dl><dt>                      Valid input                    </dt><dd>A number (integer) in the interval 2 - 3600 (one hour).</dd><dt>                      Input example                    </dt><dd>60 - (one minute)</dd><dt>                      Default value                    </dt><dd>`10`</dd></dl> |
| **                Redirect URL              ** Input field | The URL to redirect to.<dl><dt>                      Valid input                    </dt><dd>A valid URL</dd><dt>                      Input example                    </dt><dd>`http://sorryserver.mydomain.tld`</dd><dt>                      Default value                    </dt><dd>`none`</dd></dl> |
| **Backend errors** Check box |  |
| **                Alert Logic Managed Web Application Firewall (WAF) text              ** Read only Trial license only. | In WAF Trial error messages contains the message Alert Logic Managed Web Application Firewall (WAF) - TRIAL VERSION |

#### Lower button bar

<colgroup></colgroup>| **              Default values            ** | Revert to default values. |
| **              Save settings            ** | Click **Save settings** to save settings. |
