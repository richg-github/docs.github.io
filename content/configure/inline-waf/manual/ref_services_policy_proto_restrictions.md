# Protocol Restrictions 

The Alert Logic Managed Web Application Firewall (WAF) Protocol Restrictions page includes the following sections. Click on the link to go to the corresponding section to learn more:

<!--<MadCap:menuProxy mc-linked-toc="$topicHeadings" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />-->
To go to the documentation for the previous section of Alert Logic Managed Web Application Firewall (WAF) , see [Policy](ref_services_policy.md). To go to  the documentation for next subsection in the WAF section, see [Website Global Policy](ref_services_policy_policy_global.md).

**To access the Protocol restrictions section in the WAF management interface**:

1. On the left panel, under Services, click **Websites**.
2. On the Websites page, click the website you want to manage.
3. Under WAF, click **Policy**, and then scroll down to the Protocol restrictions section.

If you want to see all the settings on the Policy page, on the upper-right corner, change  the **Display preset** to **Advance**.

To save configuration changes or edits you make to any features and options, you must click **Save** on the lower-right of the section or page where you are making changes. Click **apply changes** on the upper-left corner of the page, and then click **OK**. Your changes will not be stored if you do not properly save your changes.

## Protocol restrictions

### Allowed HTTP methods, protocol versions, and web services

####  Protocol version allowed                        

Restrict which HTTP protocol versions are allowed.

Corresponding violation: `HTTP Protocol version`

<colgroup></colgroup>| **              HTTP 1.0            ** Check box | Allow / disallow HTTP 1.0 requests Default: `<allow>` |
| **              HTTP 1.1            ** Check box | Allow / disallow HTTP 1.1 requests Default: `<allow>` |
| **              HTTP 2.0            ** Check box | Allow / disallow HTTP 2.0 requests Default: `<allow>` |

####  Methods allowed                        

Restrict which HTTP methods are allowed.

Corresponding violation: `Method illegal`

<colgroup></colgroup>| **              HEAD            ** Check box | Allow / disallow HTTP method HEAD. Default: `<allow>` |
| **              GET            ** Check box | Allow / disallow HTTP method GET. Default: `<allow>` |
| **              POST            ** Check box | Allow / disallow HTTP method POST. Default: `<allow>` |
| **              OPTIONS            ** Check box | Allow / disallow HTTP method OPTIONS. Default: `<allow>` |
| **              PUT            ** Check box | Allow / disallow HTTP method PUT. Default: `<allow>` |
| **              DELETE            ** Check box | Allow / disallow HTTP method DELETE. Default: `<allow>` |
| **              MKCOL            ** Check box | Allow / disallow HTTP method MKCOL. Default: `<allow>` |
| **              COPY            ** Check box | Allow / disallow HTTP method COPY. Default: `<allow>` |
| **              MOVE            ** Check box | Allow / disallow HTTP method MOVE. Default: `<allow>` |
| **              PROPFIND            ** Check box | Allow / disallow HTTP method PROPFIND. Default: `<allow>` |
| **              PROPPATCH            ** Check box | Allow / disallow HTTP method PROPPATCH. Default: `<allow>` |
| **              LOCK            ** Check box | Allow / disallow HTTP method LOCK. Default: `<allow>` |
| **              UNLOCK            ** Check box | Allow / disallow HTTP method UNLOCK. Default: `<allow>` |
| **              PATCH            ** Check box | Allow / disallow HTTP method PATCH. Default: `<allow>` |

#### Web services                        

WAF supports inspection of XML and JSON based web services requests, including SOAP and XML RPC.

XML based requests are learned like other queries and positive and negative policies and combinations thereof can be enforced.

Corresponding violation: `Content type not enabled`

<colgroup></colgroup>| **              Enable XML web services support            ** Check box | Enable / disable support for XML web services support . If enabled, WAF will parse requests with Content-Type = text/xml and treat the XML as a query. Default: `<enabled>` |
| **              Enable XML DTD validation            ** Check box | Enable / disable validation for XML DTD. Default: `<enabled>` |
| **              Enable JSON web services support            ** Check box | Enable / disable support for JSON web services support. If enabled, WAF will parse requests with Content-Type = application/json, text/x-json or text/json and treat the JSON request payload as a query. Default: `<enabled>` |
| **              Parse text/plain content type requests            ** Check box | Enable / disable support for POST requests with Content Type text/plain. If enabled, WAF will accept requests with the text/plain Content Type and parse the payload of the request. As there is no standard for how the payload is composed, the parser is configurable. The default configuration parses the payload as a carriage return / newline separated list of parameter name / value pairs in the form name=value. This is the format used by the Direct Web request (or DWR) Java library. To change the way the payload is parsed, click the **advanced** button. This will display the regular expression that extracts the name / value pairs. If you want to change it you may want to contact Alert Logic support to get help doing it. It not complicated if you are comfortable with regular expressions though. `([^\r\n\=]+)=?([^\n\r]*)` The values are captured in the two parentheses. The first parenthesis `([^\r\n\=]+)` matches the parameter name. Note the '+' after the bracketed list of negated (^) characters. This means one or more occurrences of the characters matched by the bracketed list (anything but carriage return (\r), newline (\n) or equals (=). The `=?` part matches an optional equals sign. The last parenthesis ([^\n\r]*) the value but is optional as set by the asterisk (*) after the bracketed list. When changing the regular expression, it is a requirement that there is at least one pair of parentheses matching something. The simplest allowed regular expression would be (.+) which will match the entire payload. When composing regular expressions, note that the expression is run with the /gsi options meaning that the expression is iterated over until there are no more matches (/g), the payload is treated as one string (including \r and \n) (/s) which redefines the meaning of the meaning of the "anything" meta character (.) to include \r and \n and finally that matching is case insensitive (\i). Default: `<disabled>` |

#### HTTP Tunneling and bypass                        

WAF allows for encapsulating other protocols in the HTTP protocol, so called HTTP tunneling.

Corresponding violation: `Content type not enabled`

<colgroup></colgroup>| **              Allow HTTP tunneling            ** Check box | Enable / disable HTTP tunneling (Content-Type = application/octet-stream). When HTTP tunneling is enabled, requests with content type application/octet-stream are passed through without parsing the payload. Default: `<disabled>` |
| **              Bypass Flash Remoting            ** Check box | Enable / disable Flash Remoting (Content-Type = application/x-amf). When Flash Remoting is enabled requests with content type application/octet-stream are passed through without parsing the payload. Default: `<disabled>` |
| **              Bypass ActiveSync WBXML (binary XML) and message/rfc822            ** Check box | Enable / disable WBXML (binary xml) and message/rfc822 content types. When enabled, binary XML and content type message/rfc822 will be bypassed. This is necessary for Activesync synchronization with mobile devices and outlook web access to work. Default: `<disabled>` |
| **              Bypass unknown or missing PUT Content-Type requests            ** Check box | Enable / disable unknown or missing PUT content types. Default: `<disabled>` |
| **              Websockets            ** Check box | Enable / disable websockets. Default: `<disabled>` |
| **              Bypass custom content types            ** Check box  **Content types** Input field | Enable / disable custom content types. Default: `<disabled>`  Enter the content types you want to enable bypassing in the input field. |

### Headers, restrict length and number

Restrict length and number for HTTP request headers.

If a header fails this check, the entire request is blocked and handled accordingly.

<colgroup></colgroup>| **                Header name maximum length              ** Input field | Maximum length for each inbound HTTP header name. Corresponding violation: `Header name length`<dl><dt>                Valid input              </dt><dd>An integer in the interval 1 to 8192</dd><dt>                Unit              </dt><dd>Bytes</dd><dt>                Default value              </dt><dd>`64`</dd></dl> |
| **                Header value maximum length              ** Input field | Maximum length for each inbound HTTP header value. Corresponding violation: `Header value length`<dl><dt>                Valid input              </dt><dd>An integer in the interval 1 to 8192</dd><dt>                Unit              </dt><dd>Bytes</dd><dt>                Default value              </dt><dd>`4096`</dd></dl> |
| **                Maximum number of headers              ** Input field | Maximum number of HTTP headers in request. Corresponding violation: `Maximum number of headers`<dl><dt>                Valid input              </dt><dd>An integer</dd><dt>                Default value              </dt><dd>`50`</dd></dl> |

### Cookies, restrict length and number

Restrict type, length, number and type for HTTP request cookies.

If a cookie fails this check, the entire request is blocked and handled accordingly.

<colgroup></colgroup>| **                Accept Version0              ** Check box | Allow / disallow version 0 cookies. Version 0 is most widely used on the internet today. Corresponding violation: `Cookie version not allowed` Default: `<allow>` |
| **                Accept Version1              ** Check box | Allow / disallow version 1 cookies. Corresponding violation: `Cookie version not allowed` Default: `<allow>` |
| **                Cookie name maximum length              ** Input field | Maximum length for each cookie name. Corresponding violation: `Cookie name length`<dl><dt>                Valid input              </dt><dd>An integer in the interval 1 to 8192</dd><dt>                Unit              </dt><dd>Bytes</dd><dt>                Default value              </dt><dd>`64`</dd></dl> |
| **                Cookie value maximum length              ** Input field | Maximum length for each cookie value. Corresponding violation: `Cookie value length`<dl><dt>                Valid input              </dt><dd>An integer in the interval 1 to 8192</dd><dt>                Unit              </dt><dd>Bytes</dd><dt>                Default value              </dt><dd>`1024`</dd></dl> |
| **                Maximum number of cookies              ** Input field | Maximum number of cookies in request. Corresponding violation: `Maximum number of cookies`<dl><dt>                Valid input              </dt><dd>An integer</dd><dt>                Default value              </dt><dd>`20`</dd></dl> |

### Request, restrict length and number

Restrict length and number for HTTP request in general.

If the request fails this check, the entire request is blocked and handled accordingly.

<colgroup></colgroup>| **                Request line maximum length              ** Input field | Maximum allowed length of the request line. When the request is displayed in the browser address bar the request line is everything following the protocol://domain.name.tld part of the request. The request line is the emphasized part of http://domain.name.tld**/path/to/resource?query=1&amp;string=1** Corresponding violation: `Request line maximum length`<dl><dt>                Valid input              </dt><dd>An integer in the interval 1 to 8192</dd><dt>                Unit              </dt><dd>Bytes</dd><dt>                Default value              </dt><dd>`2048`</dd></dl> |
| **                Request path maximum length              ** Input field | Maximum allowed length of the path part of the request line. The path part is the emphasized part of http://domain.name.tld**/path/to/resource**?query=1&amp;string=1 Corresponding violation: `Request path maximum length`<dl><dt>                Valid input              </dt><dd>An integer in the interval 1 to 8192</dd><dt>                Unit              </dt><dd>Bytes</dd><dt>                Default value              </dt><dd>`512`</dd></dl> |
| **                Query string maximum length              ** Input field | Maximum allowed length of the query part of the request line. The query part is the emphasized part of http://domain.name.tld/path/to/resource?**query=1&amp;string=1** Corresponding violation: `Query string maximum length`<dl><dt>                Valid input              </dt><dd>An integer in the interval 1 to 8192</dd><dt>                Unit              </dt><dd>Bytes</dd><dt>                Default value              </dt><dd>`1536`</dd></dl> |
| **                POST form payload limit              ** Input field | Defines the maximum allowed POST content length. If a given POST request length fails the check, the entire request is blocked and handled accordingly. Corresponding violation: `Payload length exceeded`<dl><dt>                Valid input              </dt><dd>An integer in the interval 1 to 2048000</dd><dt>                Unit              </dt><dd>Bytes</dd><dt>                Default value              </dt><dd>`524288`</dd></dl> |

### Request parameters, restrict size and number

<colgroup></colgroup>| **                GET Parameter name maximum length              ** Input field | Maximum length for each GET parameter name. Corresponding violation: `GET parameter name length`<dl><dt>                Valid input              </dt><dd>An integer in the interval 1 to 8192</dd><dt>                Unit              </dt><dd>Bytes</dd><dt>                Default value              </dt><dd>`64`</dd></dl> |
| **                GET Parameter value maximum length              ** Input field | Maximum length for each GET parameter value. Corresponding violation: `GET parameter value length`<dl><dt>                Valid input              </dt><dd>An integer in the interval 1 to 8192</dd><dt>                Unit              </dt><dd>Bytes</dd><dt>                Default value              </dt><dd>`512`</dd></dl> |
| **                GET Parameter combined length              ** Input field | Maximum length for each GET parameter name + value pair. Corresponding violation: `GET parameter combined length`<dl><dt>                Valid input              </dt><dd>An integer in the interval 1 to 8192</dd><dt>                Unit              </dt><dd>Bytes</dd><dt>                Default value              </dt><dd>`576`</dd></dl> |
| **                GET Maximum number of parameters              ** Input field | Maximum number of GET parameters in request. Corresponding violation: `Maximum number of GET parameters`<dl><dt>                Valid input              </dt><dd>An integer in the interval 1 to 1000</dd><dt>                Default value              </dt><dd>`100`</dd></dl> |
| **                POST Parameter name maximum length              ** Input field | Maximum length for each POST parameter name. Corresponding violation: `POST parameter name length`<dl><dt>                Valid input              </dt><dd>An integer in the interval 1 to 524288</dd><dt>                Unit              </dt><dd>Bytes</dd><dt>                Default value              </dt><dd>`64`</dd></dl> |
| **                POST Parameter value maximum length              ** Input field | Maximum length for each POST parameter value. Corresponding violation: `POST parameter value length`<dl><dt>                Valid input              </dt><dd>An integer in the interval 1 to 524288</dd><dt>                Unit              </dt><dd>Bytes</dd><dt>                Default value              </dt><dd>`65536`</dd></dl> |
| **                POST Parameter combined length              ** Input field | Maximum length for each POST parameter name + value pair. Corresponding violation: `POST parameter combined length`<dl><dt>                Valid input              </dt><dd>An integer in the interval 1 to 524288</dd><dt>                Unit              </dt><dd>Bytes</dd><dt>                Default value              </dt><dd>`65600`</dd></dl> |
| **                POST Maximum number of parameters              ** Input field | Maximum number of POST parameters in request. Corresponding violation: `Maximum number of POST parameters`<dl><dt>                Valid input              </dt><dd>An integer in the interval 1 to 8192</dd><dt>                Default value              </dt><dd>`200`</dd></dl> |

### File uploads, restrict size and number

<colgroup></colgroup>| **                Maximum number of files              ** Input field | Maximum number of allowed files to upload in request. Corresponding violation: `Maximum number of upload files`<dl><dt>                Valid input              </dt><dd>An integer in the interval 1 to 100</dd><dt>                Default value              </dt><dd>`1`</dd></dl> |
| **                Individual file size              ** Input field | Maximum allowed size for each individual file in upload request. Corresponding violation: `Maximum filesize`<dl><dt>                Valid input              </dt><dd>An integer in the interval 1 to 1048576000</dd><dt>                Unit              </dt><dd>Bytes</dd><dt>                Default value              </dt><dd>`2097152` (2 mb)</dd></dl> |
| **                POST upload payload limit              ** Input field | Maximum allowed size for entire upload request, i.e. total size of all files in upload request. Corresponding violation: `Total upload size`<dl><dt>                Valid input              </dt><dd>An integer in the interval 1 to 1048576000</dd><dt>                Unit              </dt><dd>Bytes</dd><dt>                Default value              </dt><dd>`2097152` (2 mb)</dd></dl> |

#### File name validation

<colgroup></colgroup>| **Allowed patterns/chars** Check box Input field | Disable/Enable patterns and chars Default: `<enabled>` Enter regex for allows patterns/chars |
| **	Disallowed extensions - standard** Check box Input field | Disable/Enable disallowed standard extensions Default: `<enabled>` Enter regex for disallowed standard extensions<dl><dd></dd></dl> |
| **	Disallowed extensions - custom** Check box Input field | Disable/Enable disallowed custom extensions  Default: `<enabled>`  Enter regex for disallowed custom extensions<dl><dd></dd></dl> |
