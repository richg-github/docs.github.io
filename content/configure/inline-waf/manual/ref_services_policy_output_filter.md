# Output Filter

The Alert Logic Managed Web Application Firewall (WAF) Output Filter page includes the following sections. Click on the link to go to the corresponding section to learn more:

<!--<MadCap:menuProxy mc-linked-toc="$topicHeadings" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />-->
To go to the documentation for the previous section of Alert Logic Managed Web Application Firewall (WAF), see [Web Applications](ref_services_policy_web_applications.md). To go to  the documentation for next section in the WAF section, see [Regular Expressions](ref_services_policy_global_regular_expressions.md).

**To access the Output filter section in the WAF management interface**:

1. On the left panel, under Services, click **Websites**.
2. On the Websites page, click the website you want to manage.
3. Under WAF, click **Policy**, and then scroll down to the Output filter section.

If you want to see all the settings on the Policy page, on the upper-right corner, change  the **Display preset** to **Advance**.

To save configuration changes or edits you make to any features and options, you must click **Save** on the lower-right of the section or page where you are making changes. Click **apply changes** on the upper-left corner of the page, and then click **OK**. Your changes will not be stored if you do not properly save your changes.

The *Output filter section* allows for configuring policies for rewriting headers and body of server responses sent to the client.

#### Backend server cloaking

A typical web server gives out a lot of information about it's version, installed software, operating system, etc.

This information is completely irrelevant for normal HTTP/HTTPS communication between clients and web server. However, attackers and worms can misuse this information to craft more targeted attacks on a vulnerable web application or server.

<colgroup></colgroup>| **              Server ID            ** Input field | The server name string that is sent in respones to clients in the Server header. When the website proxy is created the value is extracted from the backend server response in a short form. Leave the field empty to omit the Server header from responses.<dl><dt>                Valid input              </dt><dd>Alphanumeric, space, dash, underscore and period.</dd><dt>                Input example              </dt><dd>Apache/2.2</dd><dt>                Default value              </dt><dd>Backend server banner without details</dd></dl> |
| **              Enable Web server cloaking mode            ** Check box | Enable / disable Web server cloaking mode. If enabled, WAF removes web server information from the response sent back from the back-end server before forwarding it to the client thus protecting the web application and server from leaking potentially sensitive information. This includes stripping of all HTTP headers that start with "X-". Eg. header "X-Powered-By: PHP/4.4.0" will be removed. Default: `<enabled>` |
| **              Intercept backend error pages            ** Check box | Intercept error pages with error code 400 or higher sent by the backend web server and replace with a general error page. Configure error pages in [Error messages](ref_services_deny_and_error_handling.md#ref_services_deny_and_error_handling_error.md). Default: <checked> When enabled the original error code can be replaced with a general one (ie. 405 > 404) or the original error can be sent to the client.<dl><dt>                Show original backend error code              </dt><dd>The original error code is sent and the error code and name is displayed in the error message.</dd><dt>                Generalize backend error codes              </dt><dd>A general error code is sent and displayed.</dd></dl> |
| **              Exclude status codes            ** Input field | Exclude specific error codes from error interception (if enabled).<dl><dt>                Valid input              </dt><dd>list of error codes separated by space</dd><dt>                Input example              </dt><dd>401 403</dd><dt>                Default value              </dt><dd>&amp;amp;lt;empty&amp;amp;gt;</dd></dl> |

#### Output headers validation and rewriting

##### Redirects validation

Redirects validation protects against attacks that redirect victims to phishing or malware sites through target applications that use untrusted data to determine the destination pages.

<colgroup></colgroup>| **                Block redirects to non trusted domains              ** | When enabled WAF will validate redirects from the protected web applications and only allow redirects to domains in the **trusted domains** whitelist. |
| **                Whitelist              ** | The whitelist is the effective list of trusted domains. Redirects are allowed to hosts in the domains in this list. The list can be edited in Trusted domains ( See [Trusted Domains](ref_services_policy_policy_global.md#ref_services_policy_policy_global.md#global_trusted_domains)) in the global policy section. |

##### Response headers rewriting

WAF allows for rewriting arbitrary response header values using regular expressions for matching the value to rewrite.

<table>
  <colgroup>
    <col></col>
    <col></col>
  </colgroup>
  <tbody>
    <tr>
      <td>
        <b>                Enable response header rewriting              </b>
      </td>
      <td>
        <p>Check or clear the check box <b>Enable response header re-writing</b> to enable this feature.                              </p>
      </td>
    </tr>
    <tr>
      <td>
        <b>                Header              </b>
      </td>
      <td>
        <p>In the list enter a the name of the header to match.</p>
        <dl>
          <dt>                  Valid input                </dt>
          <dd>
            <p>Any header field.</p>
          </dd>
          <dt>                  Input example                </dt>
          <dd>
            <ul>
              <li>
                <p>
                  <code>Location</code> - matches a redirect response header.                                                </p>
              </li>
              <li>
                <p>FooBar - matches the custom header field FooBar.</p>
              </li>
            </ul>
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
        <b>                Action              </b>
        <p>Drop-down options</p>
      </td>
      <td>
        <p>Action to take if there is a search match.</p>
        <p>Replace: replace matched string with replace string.</p>
        <p>Strip:</p>
        <p>Insert: </p>
        <dl>
          <dt>                  Valid input                </dt>
          <dd>
            <p>Drop-down options</p>
          </dd>
          <dt>                  Default value                </dt>
          <dd>
            <p>
              <code>Replace</code>
            </p>
          </dd>
        </dl>
      </td>
    </tr>
    <tr>
      <td>
        <b>                Search for              </b>
      </td>
      <td>
        <p>A regular expression matching the string to replace.</p>
        <dl>
          <dt>                  Valid input                </dt>
          <dd>
            <p>A regular expression.</p>
          </dd>
          <dt>                  Input example                </dt>
          <dd>
            <ul>
              <li>
                <p>
                  <code>
                    <code>xxxhost\.xxx\.tld</code>
                  </code> - matches <code>xxxhost.xxx.tld</code></p>
              </li>
              <li>
                <p>
                  <code>
                    <code>[a-z]{1,32}\.xxx\.tld</code>
                  </code> - matches any host name in the xxx.tld domain consisting of characters a-z (case insensitive) with length 1 - 32 characters.                                                </p>
              </li>
              <li>
                <p>
                  <code>http://</code> - matches http://                                                </p>
              </li>
            </ul>
          </dd>
          <dt>                  Default value                </dt>
          <dd>
            <p>
              <code>none</code>
            </p>
          </dd>
        </dl>
        <p>Notice the use of backslash ("\") in the examples above to escape the metacharacter ".". Without escaping the "." it will be interpreted as a metacharacter matching any character resulting in the regular expression also matching strings like xxxyhost2xxx4tld and xxxhost_xxx_tld (a.o.).                              </p>
        <p>The regular expressions matches case insensitive in a repetitive fashion meaning that if more than one instance of the search pattern is present in the string they will all be replaced.                              </p>
      </td>
    </tr>
    <tr>
      <td>
        <b>                Replace with              </b>
      </td>
      <td>
        <p>A string to replace with</p>
        <dl>
          <dt>                  Valid input                </dt>
          <dd>
            <p>Any text string</p>
          </dd>
          <dt>                  Input example                </dt>
          <dd>
            <ul>
              <li>
                <p>
                  <code>
                    <code>yyyhost.yyy.tld</code>
                  </code>
                </p>
              </li>
              <li>
                <p>
                  <code>newhost.yyy.tld</code>
                </p>
              </li>
              <li>
                <p>
                  <code>https://</code>
                </p>
              </li>
            </ul>
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
  </tbody>
</table>#### Output body validation and rewriting

WAF allows for parsing and rewriting the body of server responses. This is useful for screening (and replacing) output for confidential data like credit card numbers. Note however that rewriting server responses involves parsing the complete document and therefore will introduce added latency.

It is important that the correct response content type is configured in [Web application behavior](ref_services_policy.md#Web).

<table>
  <colgroup>
    <col></col>
    <col></col>
  </colgroup>
  <tbody>
    <tr>
      <td>
        <b>              Search for            </b>
      </td>
      <td>
        <p>A regular expression matching the string to replace.</p>
        <dl>
          <dt>                Valid input              </dt>
          <dd>
            <p>A regular expression.</p>
          </dd>
          <dt>                Input example              </dt>
          <dd>
            <ul>
              <li>
                <p>
                  <code>
                    <code>(?:\d{4}[\-\x20]?){2}\d{4,5}[\-\x20]?(?:\d{2,4})?</code>
                  </code> - matches a payment card number                                             </p>
              </li>
            </ul>
          </dd>
          <dt>                Default value              </dt>
          <dd>
            <p>
              <code>none</code>
            </p>
          </dd>
        </dl>
        <p>As with the response header rewrite function the the regular expressions matches case insensitive in a repetitive fashion meaning that if more than one instance of the search pattern is present in the string they will all be replaced. Also meta characters should be escaped if they are to be interpreted literally.                           </p>
      </td>
    </tr>
    <tr>
      <td>
        <b>              Action            </b>
        <p>Drop-down options </p>
      </td>
      <td>
        <p>Action to take if there is a search match.</p>
        <p>Replace: replace matched string with replace string.</p>
        <p>Block: block the rest of the response and log the violation.</p>
        <dl>
          <dt>                Valid input              </dt>
          <dd>
            <p>Drop-down options</p>
          </dd>
          <dt>                Default value              </dt>
          <dd>
            <p>
              <code>Replace</code>
            </p>
          </dd>
        </dl>
      </td>
    </tr>
    <tr>
      <td>
        <b>              Replace with            </b>
      </td>
      <td>
        <p>A string to replace with</p>
        <dl>
          <dt>                Valid input              </dt>
          <dd>
            <p>Any text string</p>
          </dd>
          <dt>                Input example              </dt>
          <dd>
            <ul>
              <li>
                <p>
                  <code>
                    <code>masked_payment_card</code>
                  </code>
                </p>
              </li>
            </ul>
          </dd>
          <dt>                Default value              </dt>
          <dd>
            <p>
              <code>none</code>
            </p>
          </dd>
        </dl>
      </td>
    </tr>
  </tbody>
</table>##### Exceptions                        

WAF can be configured to not rewrite the response body if the request is originating from trusted clients or if the requested path matches a regular expression.

<colgroup></colgroup>| **                Do not re-write from whitelisted IP's (trusted clients)              ** | Check or clear the check box to exclude requests from trusted clients / whitelisted IP from being rewritten. The list of trusted clients is edited in the [Global Policy](ref_services_policy_policy_global.md#global_trusted_clients) section. |
| **                Do not re-write from URIs matching regex              ** | Enter a regular expressions matching the path part of the requests to be excluded. Only responses with content types text/*`[sometype]`* will be rewritten.<dl><dt>                  Valid input                </dt><dd>A valid regular expression</dd><dt>                  Input example                </dt><dd>^/forms/ (do not rewrite requests starting with /forms/)
^.+\.js (do not rewrite files with the extension ".js")</dd><dt>                  Default value                </dt><dd>`none`</dd></dl> |
