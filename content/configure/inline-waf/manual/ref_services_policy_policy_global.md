# Website Global Policy

The Alert Logic Managed Web Application Firewall (WAF) Website Global Policy page includes the following sections. Click on the link to go to the corresponding section to learn more:

<!--<MadCap:menuProxy mc-linked-toc="$topicHeadings" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />-->
To go to the documentation for the previous section of Alert Logic Managed Web Application Firewall (WAF), see [Protocol Restrictions ](ref_services_policy_proto_restrictions.md). To go to  the documentation for next section in the WAF section, see [Web Applications](ref_services_policy_web_applications.md).

**To access the Website global policy section in the WAF management interface**:

1. On the left panel, under Services, click **Websites**.
2. On the Websites page, click the website you want to manage.
3. Under WAF, click **Policy**, and then scroll down to the Website policy section.

If you want to see all the settings on the Policy page, on the upper-right corner, change  the **Display preset** to **Advance**.

To save configuration changes or edits you make to any features and options, you must click **Save** on the lower-right of the section or page where you are making changes. Click **apply changes** on the upper-left corner of the page, and then click **OK**. Your changes will not be stored if you do not properly save your changes.

#### Validate static requests separately

The Static content policy allows requests without parameters based on *file extension* (i.e. .gif) and *allowed path characters*.

To define a static content policy enter or edit **file extensions** and **allowed path characters**.

<dl><dt>        File extension      </dt><dd>The file extension is defined as a list of comma separated values.</dd><dt>        Allowed path characters      </dt><dd>Allowed path characters are defined by selecting them on a list.
The letter A denotes all international alphanumeric characters and other characters are represented by their glyph, their UTF-8 number and a description.</dd></dl>
As static content is not supposed to have any parameters (hence the denotation "static") only requests without parameters and with the method `GET` are validated against this rule.

It is possible to allow static requests in general.

<table>
  <colgroup>
    <col />
    <col />
  </colgroup>
  <tbody>
    <tr>
      <td>
        <b>                Allow all static requests              </b>
        <p>Radio button</p>
      </td>
      <td>
        <p>If selected, requests without parameters like requests for graphic elements, stylesheets, javascript, etc. are allowed in general.                           </p>
        <p>Allowing all static requests is faster but less secure as only input to web applications will be inspected when this option is enabled.                           </p>
      </td>
    </tr>
    <tr>
      <td>
        <b>                Validate static requests path and extension               </b>
        <p>Radio button</p>
      </td>
      <td>
        <p>If selected, requests without parameters like requests for graphic elements, stylesheets, javascript, etc. are validated using allowed path extension and allowed path characters.                           </p>
        <p>Default: <code>&amp;lt;selected&amp;gt;</code></p>
      </td>
    </tr>
    <tr>
      <td>
        <b>                Allowed path characters              </b>
        <p>List of check boxes</p>
      </td>
      <td>
        <p>Allowed path characters are defined by selecting them on a the list which appears when activating the button <b>Edit</b>.                           </p>
        <p>In the list the letter A denotes all international alphanumeric characters and other characters are represented by their glyph, their UTF-8 number and a description.                           </p>
        <dl>
          <dt>                  Valid input                </dt>
          <dd>
            <p>All characters in the list</p>
          </dd>
          <dt>                  Input example                </dt>
          <dd>
            <ul>
              <li>
                <p>Hyphen-minus ("-", UTF-8: 2d)</p>
              </li>
              <li>
                <p>All international alphanumeric</p>
              </li>
              <li>
                <p>Space (" ", UTF-8: 20)</p>
              </li>
            </ul>
          </dd>
          <dt>                  Default value                </dt>
          <dd>
            <p>The path characters in the input example above.</p>
          </dd>
        </dl>
      </td>
    </tr>
    <tr>
      <td>
        <b>                Allowed static file extensions              </b>
        <p>Input field</p>
      </td>
      <td>
        <p>The file extension is defined as a list of comma separated values.</p>
        <dl>
          <dt>                  Valid input                </dt>
          <dd>
            <p>A list of comma separated file extensions without a trailing period.</p>
          </dd>
          <dt>                  Input example                </dt>
          <dd>
            <p>css,png,ico,jpg,js,jpeg,gif,swf</p>
          </dd>
          <dt>                  Default value                </dt>
          <dd>
            <p>css,png,ico,js,jpg,jpeg,gif,swf</p>
          </dd>
        </dl>
      </td>
    </tr>
    <tr>
      <td>
        <b>                Validate cookies for static requests              </b>
        <p>Check box</p>
      </td>
      <td>
        <p>Enable / disable validation of cookies for requests for static content.</p>
        <p>Default: <code>&amp;lt;disabled&amp;gt;</code></p>
      </td>
    </tr>
  </tbody>
</table>#### URL path validation

The URL regular expressions filter matches URLs without parameters on a proxy global basis. If a request matches any of the defined regular expressions, it will be marked as valid by WAF and forwarded to the back-end server.

For examples of global URL regular expressions, please refer to [Examples of global URL regular expressions](ref_services_policy_global_regular_expressions.md#ap_global_url_regular_expressions).

Full match is implied for each regular expression, meaning that each will match from the start to the end of the request (a caret ^ and dollar $ will be appended if not already present).

<colgroup></colgroup>| **                Negative validation              ** Check box | Select or clear to enable validation of the path element of the URL against negative signatures. Paths not matching attack signatures will be allowed. |
| **                Positive validation              ** Check box | Select or clear to enable positive validation of the path element of the request URL. Paths matching one of the regular expressions in the list will be allowed. |
| **                Allowed path              ** | In the list enter one or more regular expressions defining the global path policy.<dl><dt>                  Valid input                </dt><dd>Valid regular expressions.</dd><dt>                  Input example                </dt><dd>(/[\w\-]+)+\.(htm|html|shtml|pdf|asp|aspx|php|jsp)</dd><dt>                  Default value                </dt><dd>`None`</dd></dl> |

#### Denied URL paths

The URL regular expressions block filter matches URLs without parameters on a proxy global basis. If a request matches any of the defined regular expressions it will instantly be blocked.

Suppose for instance that a global paths policy rule allows all URL paths's with the extension ".php" but that you want to block access to all resources in the /admin directory - including subdirectories. To do that simply add the policy rule "/admin/".

The expressions are matching from left to right. Full match is not implied but matching always start at start of line. This implies that for instance the expression /admin will match any URI starting with /admin

<table>
  <colgroup>
    <col />
    <col />
  </colgroup>
  <tbody>
    <tr>
      <td>
        <b>                Denied path              </b>
        <p>Input fields</p>
      </td>
      <td>
        <p>In the list enter one or more regular expressions defining the global denied path policy.</p>
        <dl>
          <dt>                  Valid input                </dt>
          <dd>
            <p>A valid regular expressions</p>
          </dd>
          <dt>                  Input example                </dt>
          <dd>
            <p>/admin (any request starting with "/admin")</p>
            <p>/testarea (any request starting with "/testarea")</p>
            <p>.+\.php (any request for files with the extension ".php")</p>
            <p>.+\.htm([^l]|$) (block .htm but allow .html)</p>
          </dd>
          <dt>                  Default value                </dt>
          <dd>
            <p>
              <code>none</code>
            </p>
          </dd>
        </dl>
      </td>
    </tr>
    <tr>
      <td>
        <p>
          <b>                  Add predefined                </b>
        </p>
        <p>Drop-down list</p>
      </td>
      <td>
        <p>Select one of the following predefined regular expressions:</p>
        <ul>
          <li> Block directory browsing </li>
          <li>Generic - Block access to admin path</li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>#### Query and Cookie validation

Depending on the web server and web application technology and design of the web applications on the back end web server cookie names and values may in some cases be parsed as part of a general request object with the risk that client request cookies may be used to bypass validation controls. It is therefore recommended that cookies are parsed and validated as an integral part of the client query. That is as request parameters.

WAF parses cookies and when learning is enabled the Learner maps cookie values as global parameters.

<colgroup></colgroup>| **                  Cookie validation enabled                ** Check box | If enabled client request cookies will be parsed and validated as request parameters. Default: `enabled` |

##### Validation

In the global parameters section, parameters which all or many URLs have in common can be added. For instance in many CMS systems an URL can be viewed in a printer friendly version by adding a specific parameter to the URL.

When adding parameters to the list the name of the parameter is interpreted by WAF as regular expressions. Like with the global URL-regular expressions full match from start to end is implied. The value can either be a regular expression or a predefined input validation class.

<table>
  <colgroup>
    <col />
    <col />
  </colgroup>
  <tbody>
    <tr>
      <td>
        <b>                Enable global parameter signature based negative matching              </b>
        <p>Check box</p>
      </td>
      <td>
        <p>Select or clear the check box <b>Enable global parameter signature based negative matching</b> to enable signature bases matching of parameter names and corresponding values.                              </p>
        <p>When learning is enabled for the website this option should be enabled as it ensures that parameters not being validated by positive policy rules are validated negatively and thus not rejected by default.                              </p>
      </td>
    </tr>
    <tr>
      <td>
        <b>                Enable global parameter regexp matching              </b>
      </td>
      <td>
        <p>Select or clear the check box <b>Enable global parameter regexp matching</b> to enable global parameter regexp matching.                              </p>
      </td>
    </tr>
    <tr>
      <td>
        <b>                Name              </b>
        <p>Input fields</p>
      </td>
      <td>
        <p>In the list enter a regular expression matching the parameter name or names you want to match.</p>
        <dl>
          <dt>                  Valid input                </dt>
          <dd>
            <p>A valid regular expression.</p>
          </dd>
          <dt>                  Input example                </dt>
          <dd>
            <ul>
              <li>
                <p>
                  <code>\w{1,32}_btn</code> - matches all parameter names which start with a string of up to 32 characters and ends with the specific string '_btn'.                                                </p>
              </li>
              <li>
                <p>
                  <code>print</code> - matches the specific name print.                                                </p>
              </li>
            </ul>
          </dd>
          <dt>                  Default value                </dt>
          <dd>
            <p>
              <code>None</code>
            </p>
          </dd>
        </dl>
      </td>
    </tr>
    <tr>
      <td>
        <b>                Type              </b>
        <p>Drop-down list</p>
      </td>
      <td>
        <p>Input validation type.</p>
        <dl>
          <dt>                  Valid input                </dt>
          <dd>
            <p>Options from the drop-down list</p>
            <dl>
              <dt>                      Class                    </dt>
              <dd>
                <p>A predefined named regular expression like <em>numeric</em> or <em>alphanumeric</em>. Editing the class definition will affect all policy components that uses it.                                                </p>
              </dd>
              <dt>                      Regexp                    </dt>
              <dd>
                <p>Regular expression. See<a href="ref_services_policy_global_regular_expressions.md#d0e12930"> Examples of global parameters regular expressions</a>.                                                </p>
              </dd>
              <dt>                      Bypass                    </dt>
              <dd>
                <p>The parameter will be completely bypassed.</p>
              </dd>
            </dl>
          </dd>
          <dt>                  Default value                </dt>
          <dd>
            <p>
              <code>Class</code>
            </p>
          </dd>
        </dl>
      </td>
    </tr>
    <tr>
      <td>
        <b>                Update              </b>
        <p>Drop-down list</p>
      </td>
      <td>
        <p>Controls how the Learner handles the parameter.</p>
        <p>When update is set to <code>manual</code> the parameter entry will not be maintained and updated by the Learner. When set to <code>auto</code> the entry will be maintained by the Learner.                              </p>
      </td>
    </tr>
    <tr>
      <td>
        <b>                Value              </b>
        <p>Depends on <code>type</code></p>
      </td>
      <td>
        <p>Value for input validation.</p>
        <dl>
          <dt>                  Valid input                </dt>
          <dd>
            <ul>
              <li>
                <p>A class selected from the class drop-down list.</p>
              </li>
              <li>
                <p>A regular expression</p>
              </li>
            </ul>
          </dd>
          <dt>                  Default value                </dt>
          <dd>
            <ul>
              <li>
                <p>When <code>type</code> = <code>class</code>: <code>num</code></p>
              </li>
              <li>
                <p>When <code>type</code> = <code>regex</code>: <code>empty</code></p>
              </li>
            </ul>
          </dd>
        </dl>
        <p>When type is <code>class</code> the corresponding regular expression of the input validation class is displayed to the right of the class selector.                              </p>
      </td>
    </tr>
  </tbody>
</table>
For examples of specifying global parameters using regular expressions please refer to [Examples of global parameters regular expressions](ref_services_policy_global_regular_expressions.md#d0e12930).

For more general examples using regular expressions for input validation please refer to [Examples of regular expressions for input validation](ref_services_policy_global_regular_expressions.md#ap_validating_input_parameters).

Full match is implied for each regular expression, meaning that each will match from the start to the end of the request (a caret ^ and dollar $ will be appended if not already present).

#### Headers validation

<colgroup></colgroup>| **                  Allow only RFC defined headers                ** Check box | Enable / disable enforcement of strict HTTP compliant headers. If enabled, WAF will enforce strict HTTP header compliance according the RFC standards and deny any custom HTTP header sent in the request. Default: `<disabled>` |
| **                  Input headers validation rules                ** Check box | The header validation policy rules allow for enforcing a combination of positive and negative validation rules on either specific named headers or all headers. "All" header rules also applies to specific named headers. For each header policy entry the options are:<dl><dt>                    Status                  </dt><dd>`On` or `Off` - enabling or disabling the policy rule.</dd><dt>                    Rule type                  </dt><dd>`Negative` or `Positive` - Negative will look for the presence of strings matching the specified regular expression (like searching for Carriage Return in a header) and Positive will require the entire header value to match the specified regular expression.</dd><dt>                    Match                  </dt><dd>`General` or `Named` - General will apply the policy rule to all headers and Named will only apply the policy rule to a named header.</dd><dt>                    Header                  </dt><dd>Only applies to `Named` header rules. The name of the header to validate using the specified regular expression.</dd><dt>                    Regex                  </dt><dd>The regular expression specifying the validation rule for the header.</dd><dt>                    Description                  </dt><dd>A description of the policy rule - like "XSS match tags".</dd></dl> |

##### Denied headers

Requests can be blocked/logged based on the value of a header.

<colgroup></colgroup>| **                    Enable headers blocking                  ** Check box | Select or clear to enable blocking of requests based on header content. Requests with headers matching the blocking rules will denied. |
| **                    Header                  ** Input fields | Enter name of header to match.<dl><dt>                      Valid input                    </dt><dd>The name of an HTTP header</dd><dt>                      Input example                    </dt><dd>User-Agent</dd><dt>                      Default value                    </dt><dd>`None`</dd></dl> |
| **                    Allowed path                  ** Input fields | Regular expression to match header value. Note that full match is not implied so the regex `string` will match any value containing "string".<dl><dt>                      Valid input                    </dt><dd>Valid regular expressions.</dd><dt>                      Input example                    </dt><dd>rogue-spam-bot</dd><dt>                      Default value                    </dt><dd>`None`</dd></dl> |

#### Attack signatures usage

The use of attack signatures can be enabled or disabled for each request method supported.

##### Negative filtering column                        

The check boxes in the negative filtering column enable or disable the use of attack signatures for validating input. The settings only applies to requests or or request parts for which negative filtering is enabled.

<colgroup></colgroup>| **                    Attack Class                  ** | The name of the signature attack class |
| **                    HEAD                  ** Check box | Select or clear to enable signature for method `HEAD`. Default: Signature dependent. |
| **                    GET                  ** Check box | Select or clear to enable signature for method `GET`. Default: Signature dependent. |
| **                    POST                  ** Check box | Select or clear to enable signature for method `POST`. Default: Signature dependent. |
| **                    PUT                  ** Check box | Select or clear to enable signature for method `PUT`. Default: Signature dependent. |
| **                    DELETE                  ** Check box | Select or clear to enable signature for method `DELETE`. Default: Signature dependent. |
| **                    MKCOL                  ** Check box | Select or clear to enable signature for method `MKCOL`. Default: Signature dependent. |
| **                    COPY                  ** Check box | Select or clear to enable signature for method `COPY`. Default: Signature dependent. |
| **                    MOVE                  ** Check box | Select or clear to enable signature for method `MOVE`. Default: Signature dependent. |
| **                    PROPFIND                  ** Check box | Select or clear to enable signature for method `PROPFIND`. Default: Signature dependent. |
| **                    PROPPATCH                  ** Check box | Select or clear to enable signature for method `PROPPATCH`. Default: Signature dependent. |
| **                    LOCK                  ** Check box | Select or clear to enable signature for method `LOCK`. Default: Signature dependent. |
| **                    UNLOCK                  ** Check box | Select or clear to enable signature for method `UNLOCK`. Default: Signature dependent. |
| **                    PATCH                  ** Check box | Select or clear to enable signature for method `PATCH`. Default: Signature dependent. |

##### Classification column                        

The check boxes in the classification column enable or disable the use of attack signatures for classifying log records and learning samples. If for instance the website takes HTML as in input like some CMS'es and bulletin board systems does this is likely to trick the Cross Site Scripting (XSS) signature. If it is not possible to white-list the IP address(es) from which the input originates or to only allow access to the CMS via VPN it might be necessary to disable the XSS signature in order to ensure that the Learner gets the data samples.

<colgroup></colgroup>| **                    Attack Class                  ** | The name of the signature attack class |
| **                    HEAD                  ** Check box | Select or clear to enable signature for method `HEAD`. Default: Signature dependent. |
| **                    GET                  ** Check box | Select or clear to enable signature for method `GET`. Default: Signature dependent. |
| **                    POST                  ** Check box | Select or clear to enable signature for method `POST`. Default: Signature dependent. |
| **                    OPTIONS                  ** Check box | Select or clear to enable signature for method `OPTIONS`. Default: Signature dependent. |

#### Session and CSRF protection                     

WAF has the ability to protect against session hijacking and CSRF (Cross Site Request Forgery) by:

1. Binding client IPs to session cookies by issuing a validation cookie containing a cryptographic token (a checksum) which validates session id + client IP + a secret for each client request.
2. By binding forms to sessions and verifying the origin of the form through insertion of a form validation parameter containing a cryptographic token which proves that the action formulator (the system issuing the page containing a form with an action) knows a session specific secret.
3. Additionally idle sessions are timed out in order to prevent users from staying logged in making them vulnerable to CSRF attacks.

When the web system issues a session cookie WAF detects it and issues a corresponding session validation cookie. In order to be able to identify the session cookie it is necessary to enter the name of the cookie containing the session id - i.e. PHPSESSID, JSESSIONID, ASPSESSIONID, SID.

An easy way to identify the session cookie name for the site you are configuring protection is to establish a session with the site (logging in, visiting the site or whatever actions are necessary to make the site issue a session cookie) and then view the cookies issued for that specific site in your browser.

<dl><dt>          Finding session cookie name in Firefox        </dt><dd>When a session is established view the cookie in **Tools**-&amp;amp;gt;**Options**+**Privacy**-&amp;amp;gt;**Cookies**-&amp;amp;gt;**Show Cookies**
Enter the domain name of the site in the search field.</dd></dl><colgroup></colgroup>| **                  Session ID name                ** Input field | The name of the cookie containing the session identifier. This field value is required to enable session and form (CSRF) protection.<dl><dt>                    Valid input                  </dt><dd>Any regular expression matching the name of the session id cookie.</dd><dt>                    Input example                  </dt><dd>`PHPSESSID`
`JSESSIONID`
`ASPSESSIONID`
`ASPSESSIONID\w+ (matching asp session id's with random strings appended to the name like `ASPSESSIONIDAAQTDQRT`)`
`SID`</dd><dt>                    Default value                  </dt><dd>`&amp;amp;lt;none&amp;amp;gt;`</dd></dl> |
| **                  Secret for signing checksums                ** Input field | A hard to guess string used to generate session cookie validation tokens.<dl><dt>                    Valid input                  </dt><dd>Any string</dd><dt>                    Input example                  </dt><dd>didnqdndnwqdnqdagdiddbuqh3shjethdnssbvsunjn</dd><dt>                    Default value                  </dt><dd>`&amp;amp;lt;random value&amp;amp;gt;`</dd></dl> |
| **                  Idle session timeout                ** Input field | Idle session timeout specifies the maximum duration of an idle session before it is dropped resulting in the user being logged out from the web site.<dl><dt>                    Valid input                  </dt><dd>A number (integer) in the interval 10 - 86400 (24 hours).</dd><dt>                    Input example                  </dt><dd>`900` - 15 minutes</dd><dt>                    Default value                  </dt><dd>`600`</dd></dl> |

##### Cookie flags                        

<colgroup></colgroup>| **                    Add Secure flag to session cookie                  ** Check box | Add secure flag to session cookie to instruct users browser to only send the cookie over an SSL connection. Default: `<disabled>` |
| **                    Make session cookie HttpOnly                  ** Check box | Add HttpOnly flag to session cookie to instruct users browser to make the cookie inaccessible to client side script. Default: `<disabled>` |
| **Add SameSite flag to session cookie** Checkbox Drop-down option | Add SameSite flag to session cookie for none, lax, or strict. Default: `<disabled>` |

#####  HSTS - HTTP Strict Transport Security                        

HSTS is a mechanism enabling web sites to declare themselves accessible only via secure connections - HTTPS. The policy is declared by web sites via the Strict-Transport-Security HTTP response header field. When enabling HSTS in WAF the Strict-Transport-Security header will be injected in server responses if it is not already present.

<colgroup></colgroup>| **                    Enable HSTS                  ** Check box | Add Strict-Transport-Security header to backend server responses if not already present. Default: `<disabled>` |
| **                    Max age                  ** Check box | Max age corresponds to the required "max-age" directive in the HSTS directive and specifies the number of days, after the reception of the STS header field, during which the User Agent (browser) regards the web server (from which the HSTS header was received) as a Known HSTS Host.. Default: `<365>` |

##### Session protection configuration                        

<colgroup></colgroup>| **                    Enable session protection                  ** Check box | Enable / disable validation of session identifiers. If enabled, WAF will issue a validation cookie containing a cryptographic token (a checksum) which validates session id + client IP + secret for signing checksums (above) for each client request. The validation cookie is named __PFV__ and is issued whenever WAF detects a set_cookie with a cookie name matching the value configured (above) from the web site to protect. Default: `<disabled>` |
| **                    Session violation action                  ** Check box | What WAF should do when an invalid session id is detected. Session violation actions<dl><dt>                      Block request                    </dt><dd>The request is blocked and a session cookie with max-age=0 is sent back to the client resulting in the clients browser to expire the session cookie.</dd><dt>                      Drop session, allow request                    </dt><dd>The session cookie is removed from the request before the request is allowed to reach the web system.
In the deny log the request will be listed with action = strip.</dd></dl> Default: `<Drop session, allow request>` |

##### CSRF protection configuration                        

<colgroup></colgroup>| **                    Generate request form validation tokens (CSRF protection)                  ** Check box | Enable / disable generation of request form validation tokens (CSRF protection) If enabled, WAF will parse web system responses of type text/* searching for form tags. When forms tags are detected a session specific checksum validating the form action is inserted as a hidden parameter (named ___pffv___) to the form. Default: `<disabled>` Now go to **Policy**->**Web applications** to enable request validation for specific applications (see [Web application settings](ref_services_policy_web_applications.md#ref_services_policy_web_applications.md#web_applications_settings)). If configured the Learner will learn and configure CSRF protection for applications. |
| **                    Form violation action                  ** Check box | What WAF should do when an invalid request is detected. Form violation actions<dl><dt>                      Block request                    </dt><dd>The request is blocked and a session cookie with max-age=0 is sent back to the client resulting in the clients browser to expire the session cookie.</dd><dt>                      Drop session, allow request                    </dt><dd>The session cookie is removed from the request before the request is allowed to reach the web system.
In the deny log the request will be listed with action = strip.</dd></dl> Default: `<Drop session, allow request>` |

##### Exceptions

<colgroup></colgroup>| **                Enable CSRF Exception by Regular Expression              ** Check box |  |
| **                Regular Expression              ** Input field |  |

#####  Request authorization configuration                        

<colgroup></colgroup>| **                    Enable request authorization                  ** Check box | Enable / disable request authorization for configured web applications. If enabled, WAF will authorize access to resources based on session validity. Request authorization is only enforced for resources for which this feature is enabled. Default: `<disabled>` Now go to **Policy**->**Web applications** to enable request authorization for specific applications and other resources incl. static files (see [Web application settings](ref_services_policy_web_applications.md#ref_services_policy_web_applications.md#web_applications_settings)). |

#### Trusted clients - IP whitelisting                     

List if IP addresses which are trusted / whitelisted. The in- and output filters can be configured to be bypassed for the whitelisted addresses.

<colgroup></colgroup>| **                  Whitelist                ** Input field | Per default, requests originating from any IP address (0.0.0.0/0) is affected when Pass Through Mode is enabled. The white list allows for the definition of specific IP address(es) or networks for which Pass Through Mode is enabled.<dl><dt>                    Valid input                  </dt><dd>IP address with net mask (IP/mask) in CIDR notation</dd><dt>                    Input example                  </dt><dd>`192.168.0.8/32` - the IP address 192.168.0.8
`192.168.0.0/24` - IP addresses 192.168.0.0 - 255
`192.168.0.8/29` - IP addresses 192.168.0.8-15</dd><dt>                    Default value                  </dt><dd>`&amp;amp;lt;none&amp;amp;gt;`</dd></dl> |

#####  IP pass through                        

IP pass through allows for configuring overriding of filter actions based on the source of the request.

<colgroup></colgroup>| **                    Enable HTTP request blocking bypass for trusted clients                  ** Check box | Enable / disable HTTP pass through With Pass Through for trusted clients enabled, all requests will be forwarded to the real server, but will be otherwise handled the usual way (ie. WAF will learn about the site and log any would be blocked requests not matching the applied access control list). Default: `<disabled>` |
| **                    Enable IP network blocking bypass for trusted clients                  ** Check box | Enable / disable network blocking pass through When enabled, IP addresses listed as trusted clients will be included in the global list of IP addresses that are allowed to bypass network blocking and DoS mitigation controls. Note that the address will not be bypassed unless network blocking bypass is allowed in **Services**->**Network** Default: `<disabled>` |

#### Trusted domains

The trusted domains is a whitelist of domains which is composed of 1) the domain of the website proxy virtual host and the domains of the host names in Virtual host aliases and 2) a list of other trusted domains which can be entered manually.

The effective list of trusted domains is used in Remote File Inclusion signatures to leave out URLs targeting hosts within the list and when validating redirects to allow redirects to hosts within the list.

<colgroup></colgroup>| **                  Effective trusted domains                ** | This is the effective list of trusted domains, i.e. the automatically generated list of the domain of the website proxy virtual host, the domains of the host names in Virtual host aliases and the manually entered domains (if any). |
| **                  Other trusted domains                ** | Enter additional domains to the list of trusted domains. Domains are separated by newline. |
| **                  Include other trusted domains in domains list                ** | When enabled the manually entered domains will be added to the effective trusted domains list. |

#### Evasion protection

<colgroup></colgroup>| **Block overlong UTF-8 sequences** Check box |  |
| **                  Block multiple and %u encoded requests                ** Check box | Enable / disable blocking of multiple (or %u) encoded requests. In an attempt to evade detection attackers often try to encode requests multiple times. If enabled, WAF will block requests which after being decoded still contains encoded characters. Default: `<enabled>` |

##### Duplicate parameter names                        

If duplicate parameter names are allowed, wrongly configured web application behavior may result in Alert Logic Managed Web Application Firewall (WAF) not learning the web site correctly and may also lead to WAF bypassing vulnerabilities depending on the target application/web server technology.

An attacker may submit a request to the web application with several parameters with the same name depending on the technology the web application may react in one of the following ways:

1. It may only take the data from the first or the last occurrence of the duplicate parameter
2. It may take the data from all the occurrences and concatenate them in a list or put them in an array

In the case of concatenation it will allow an attacker to distribute the payload of for instance an SQL injection attack across several duplicate parameters.

As an example ASP.NET concatenates duplicate parameters using ',' so `/index.aspx?page=22&amp;page=42` would result in the backend web application parsing the value of the 'page' parameter as page=22,42 while WAF may see it as two parameters with values 22 and 42.

This behavior allows the attacker to distribute an SQL injection attack across the three parameters.

`/index.aspx?page='select data&amp;page=1 from table` would result in the backend web application parsing the value of the 'page' parameter as 'select data, 1 from table while WAF may see it as two parameters with values `'select data` and `1 from table`.

By default, when WAF validates parameters negatively it automatically concatenates the payload of duplicate parameters. It is mostly in the case where a positive application or global rule allows a specific parameter with an input validation rule that makes room for attacks like the above the parameter duplication problem exists. In the page example above the attack would be stopped because the page parameter would be learned as numeric input (an integer). This would not allow text input like in the example above. Nevertheless it is important to configure WAF to mimic the target web applications parsing of requests as closely as possible.

<colgroup></colgroup>| **                    Block duplicate parameter names                  ** Check box | Enable / disable blocking of duplicate parameter names. If enabled, WAF blocks requests containing duplicate parameter names. Default: `<disabled>` |
| **                    Join duplicate parameter names                  ** Check box | Enable / disable concatenation duplicate parameters. If enabled, WAF will concatenate the values of the duplicate parameters using the configured join separator (below). Default: `<enabled>` |
| **                    Join separator                  ** Input field | Character(s) used for separating concatenated parameter values.<dl><dt>                      Valid input                    </dt><dd>A string of 0 to 5 characters</dd><dt>                      Input example (in quotes)                    </dt><dd>`','` - comma, ASP and ASP.NET</dd><dt>                      Default value                    </dt><dd>`''` - empty string</dd></dl> |

The best option is to disallow duplicate parameter names. It may not be practical though as the use of duplicate parameters may be intended in some applications - the most prominent example being PHP which parses parameter names suffixed with `[]` as an array - like par1[]=22&amp;par1[]=42 becoming array(22,42). If this feature is not in use block it.

If the application technology is ASP/IIS or ASP.NET/IIS and it is not possible to disallow duplicate parameters the recommended setting is to join duplicate parameters using ',' as in the join separator example above.

#### Time restricted access                     

Access to a website can be restricted on a time basis.

##### Opening hours                        

For each weekday enter opening hours.

<colgroup></colgroup>| **                    Opens                  ** Input field | Time the website opens on the weekday.<dl><dt>                      Valid input                    </dt><dd>24h time string in the format hh:mm.</dd><dt>                      Input example                    </dt><dd>08:00</dd><dt>                      Default value                    </dt><dd>`00:00`</dd></dl> |
| **                    Closes                  ** Input field | Time the website closes on the weekday.<dl><dt>                      Valid input                    </dt><dd>24h time string in the format hh:mm.</dd><dt>                      Input example                    </dt><dd>18:00</dd><dt>                      Default value                    </dt><dd>`24:00`</dd></dl> |

##### Website is closed                        

To specify dates where the website is closed enter a list of dates in the format mm/dd separated by whitespace, comma or semicolon.

##### When website is closed redirect to                        

URL to redirect the visitor to when website is closed.

This field is required.

#### Input validation classes

Characters classes are useful when you want to use a predeclared set of criteria used by WAF for input request validation. Eg. if you have lots of HTML forms that use an input field "email", you can define a class and a regular expression which defines what a valid e-mail address is. This class can then be used throughout the entire policy.

When a `class` is changed, all affected policy elements are automatically updated to reflect the change.

<colgroup></colgroup>| **                  Rank                ** Read only | The class rank when used by the Learner. To change the rank, place the cursor in one of the classes input fields. The rank number will be indented. Use the buttons                              **Move up** and **Move down** in the lower button panel to change the class' rank. |
| **                  Name                ** Input field | The class' name.<dl><dt>                    Valid input                  </dt><dd>A text string. No spaces or special characters.</dd><dt>                    Input example                  </dt><dd>`my_class`</dd><dt>                    Default value                  </dt><dd>`&amp;amp;lt;none&amp;amp;gt;`</dd></dl> |
| **                  Value                ** Input field | The class regular expression.<dl><dt>                    Valid input                  </dt><dd>A valid regular expression.
Full match is implied for each regular expression, meaning that each will match from the start to the end of the request (a caret ^ and dollar $ will be appended if not already present).</dd><dt>                    Input example                  </dt><dd>`[A-Za-z]{1,32}` - a string of max. 32 7-bit letters.</dd><dt>                    Default value                  </dt><dd>`&amp;amp;lt;none&amp;amp;gt;`</dd></dl> |
| **                  X                ** Button | Mark class for deletion. When classes are saved the marked classes will be deleted. When deleting classes that are in use in the policy you will be prompted to accept replacement of the deleted classes with existing classes. Learner data samples using deleted classes will be deleted. |

For more information about classes and their corresponding regular expressions, refer to [Regular expressions](ref_services_policy_global_regular_expressions.md#top).

#####  Negative signatures policy                        

Some user input is so complex and unpredictable that, to avoid false positives, positive validation of input ends up being very general and loose. An example of this is free text input fields which often get mapped to the input validation class "printable" which basically allows all printable characters. It is often better validate such input negatively - which WAF does by default.

WAF determines if an input should be validated negatively based on the input validation class rank. By default the threshold is the class `Printable`. If a parameters input is learned/configured to be the class configured as threshold the signatures policy will be used instead of the class regular expression.

<colgroup></colgroup>| **                    Move up                  ** | Change the rank of the selected class. To move the class upwards. Select the class by clicking anywhere in the class row. When selected the class rank number is highlighted and indented. Click **Move up** to move the class one step upwards. |
| **                    Move down                  ** | Change the rank of the selected class. Works as described above. |
| **                    Add new                  ** | Add new class. When clicked an empty row will appear at the bottom of the class list. Fill out the blanks and place the class in the class hierarchy with the move buttons. |
| **                    Use negative checking above and including class rank                  ** Drop-down list | The class rank above and including which input will be validated negatively.<dl><dt>                      Valid input                    </dt><dd>Values in the drop-down list.</dd><dt>                      Input example                    </dt><dd>`standard`</dd><dt>                      Default value                    </dt><dd>`printable`</dd></dl> To disable negative class checking select `disabled` in the list. |
