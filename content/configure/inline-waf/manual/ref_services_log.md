# Log

The Alert Logic Managed Web Application Firewall (WAF) Log page includes the following sections. Click on the link to go to the corresponding section to learn more:

<!--<MadCap:menuProxy mc-linked-toc="$topicHeadings" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />-->
To go to the documentation for the previous section of Alert Logic Managed Web Application Firewall (WAF), see [Learning Settings](ref_services_learning_settings.md). To go to  the documentation for next subsection in the WAF section, see [Reports](ref_services_reports.md).

**To access the Log page in the WAF management interface**:

1. On the left panel, under Services, click **Websites**.
2. On the Websites page, click the website you want to manage.
3. Under Log, click **Deny log** to access the first section.

To save configuration changes or edits you make to any features and options, you must click **Save** on the lower-right of the section or page where you are making changes. Click **apply changes** on the upper-left corner of the page, and then click **OK**. Your changes will not be stored if you do not properly save your changes.

## Deny log

The Deny log window provides access to all denied request to the proxy. Filtering functions allows for specification of fine grained filtering of log information.

### Specifying filter criteria

The filter function allows you to specify conditions for showing a subset of the log entries. Until reset the filter conditions also apply to the log report.

When the log filter section is not expanded, a **Filter button** and current filter criteria is shown on a general level. When filter criteria are defined, a **RESET** button will be available at the left of the filter button. When the reset button is pressed, the filter criteria will be reset.

When the Filter button is clicked, the filter section expands and filter criteria can be specified. Following filter criteria are available:

<table>
  <colgroup>
    <col></col>
    <col></col>
  </colgroup>
  <tbody>
    <tr>
      <td>
        <b>              ID            </b>
        <p>Input field</p>
      </td>
      <td>
        <p>Number identifying a log entry.</p>
        <dl>
          <dt>                Valid input              </dt>
          <dd>
            <p>Number of type integer.</p>
          </dd>
          <dt>                Input example              </dt>
          <dd>
            <p>
              <code>20567</code>
            </p>
          </dd>
          <dt>                Default value              </dt>
          <dd>
            <p>
              <code>
                <code>&amp;lt;none&amp;gt;</code>
              </code>
            </p>
          </dd>
        </dl>
      </td>
    </tr>
    <tr>
      <td>
        <b>Ref ID</b>
        <p>Input field</p>
      </td>
      <td> </td>
    </tr>
    <tr>
      <td>
        <b>              Path            </b>
        <p>Input field</p>
      </td>
      <td>
        <p>Pattern or string specifying filter based on the URL path.</p>
        <dl>
          <dt>                Valid input              </dt>
          <dd>
            <p>A string or a simple wildcard.</p>
            <p>Use the following characters to specify wildcards:</p>
            <p>
              <code>* =</code> any string any length.                                    </p>
            <p>
              <code>? =</code> one occurrence of any character.                                    </p>
          </dd>
          <dt>                Input example              </dt>
          <dd>
            <ul>
              <li>
                <p>
                  <code>/store/*</code> - matches all URL paths beginning with string /store/ including the string itself.                                             </p>
              </li>
              <li>
                <p>
                  <code>*.php</code> - matches all url paths in all sub directories with the extension .php .                                             </p>
              </li>
            </ul>
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
        <b>              IP            </b>
        <p>Input field</p>
      </td>
      <td>
        <p>Source IP address of the originating client</p>
        <dl>
          <dt>                Valid input              </dt>
          <dd>
            <p>An IP address in the format xxx.xxx.xxx.xxx</p>
          </dd>
          <dt>                Input example              </dt>
          <dd>
            <p>
              <code>192.168.45.17</code>
            </p>
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
        <b>              Host            </b>
        <p>Input field</p>
      </td>
      <td>
        <p>Host information from the request blocked.</p>
        <dl>
          <dt>                Valid input              </dt>
          <dd>
            <p>A string or a simple wildcard.</p>
            <p>Use the following characters to specify wildcards:</p>
            <p>
              <code>* =</code> any string any length.                                    </p>
            <p>
              <code>? =</code> one ocurrence of any character.                                    </p>
          </dd>
          <dt>                Input example              </dt>
          <dd>
            <p>
              <code>www.mycompany.com</code>
            </p>
            <p>
              <code>*.mycompany.com</code>
            </p>
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
        <b>              Date from            </b>
        <p>Input field</p>
      </td>
      <td>
        <p>Filter based on request timestamp. Date from specifies the date of the oldest log records that should be included.</p>
        <dl>
          <dt>                Valid input              </dt>
          <dd>
            <p>A date string in the format: mm/dd/yyyy</p>
          </dd>
          <dt>                Input example              </dt>
          <dd>
            <p>
              <code>
                <code>04/27/2021</code>
              </code>
            </p>
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
        <b>              Date to            </b>
        <p>Input field</p>
      </td>
      <td>
        <p>Filter based on request timestamp. Date to specifies the date of the newest log records that should be included.</p>
        <p>Use <em>Date from</em> and <em>Date to</em> to specify a time interval.                           </p>
        <dl>
          <dt>                Valid input              </dt>
          <dd>
            <p>A date string in the format: mm/dd/yyyy</p>
          </dd>
          <dt>                Input example              </dt>
          <dd>
            <p>
              <code>
                <code>04/29/2021</code>
              </code>
            </p>
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
        <b>Risk</b>
        <p>Drop down menu</p>
      </td>
      <td>
        <p>Risk classification of the log entry. Options are:</p>
        <ul>
          <li>Critical                                        </li>
          <li>High</li>
          <li>Medium</li>
          <li>Low</li>
          <li>None</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>
        <p>
          <b>Deny action</b>
        </p>
        <p>Multiple check boxes</p>
      </td>
      <td>
        <p>Deny action taken on the request. Options are:</p>
        <dl>
          <dt>                Allow              </dt>
          <dd>
            <p>The request was allowed, either because the current mode and white list configuration or because the requests was allowed according to policy. If the request was allowed by policy the reason for the request being logged in the deny log is typically that the backend server responded with an error. Expand the request to see details.                                    </p>
          </dd>
          <dt>                Block              </dt>
          <dd>
            <p>The request was blocked by WAF.</p>
          </dd>
          <dt>                Block-IP              </dt>
          <dd>
            <p>The request was blocked by WAF and the source IP was blacklisted resulting in further requests from that source being blocked at the network level.                                    </p>
          </dd>
          <dt>                Strip              </dt>
          <dd>
            <p>The offending part of the request was stripped before allowing the request. Used for instance to remove session cookies for expired sessions.</p>
          </dd>
        </dl>
      </td>
    </tr>
  </tbody>
</table>### Response

| **Compromise Risk** Check box |  |
| **Unlikely ** Check box |  |

### Attack classification

<table>
  <colgroup>
    <col></col>
    <col></col>
  </colgroup>
  <tbody>
    <tr>
      <td>
        <b>              Attack classification            </b>
      </td>
      <td>
        <p> Options are:</p>
        <ul>
          <li>Unclassified </li>
          <li>SQL injection</li>
          <li>XPath injection</li>
          <li>SSI injection</li>
          <li>OS commanding</li>
          <li>XSS (Cross Site Scripting)</li>
          <li>Path traversal</li>
          <li>Enumeration</li>
          <li>Format string</li>
          <li>Buffer overflow</li>
          <li>DoS attempt</li>
          <li>Worm probe</li>
          <li>Access violation</li>
          <li>Malformed request</li>
          <li>HTML tags</li>
          <li>Session invalid</li>
          <li>XSRF (Cross Site Request Forgery)</li>
          <li>Session expired</li>
          <li>Detection evasion</li>
          <li>File inclusion</li>
          <li>CRLF injection</li>
          <li>HTTP request smuggling</li>
          <li>XQuery injection</li>
          <li>LDAP injection</li>
          <li>XML injection</li>
          <li>Null byte injection</li>
          <li>Information leak</li>
          <li>Backend error</li>
          <li>Broken robot</li>
          <li>Broken int. link</li>
          <li>Broken ext. link</li>
          <li>Other</li>
          <li>None</li>
          <li>False positive</li>
          <li>Friendly</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>
        <b>Add</b>
      </td>
      <td> </td>
    </tr>
    <tr>
      <td>
        <b>Remove</b>
      </td>
      <td> </td>
    </tr>
    <tr>
      <td>
        <b>Add All</b>
      </td>
      <td> </td>
    </tr>
    <tr>
      <td>
        <b>Rem. All</b>
      </td>
      <td> </td>
    </tr>
  </tbody>
</table>### Policy violations

<colgroup></colgroup>| **              Path unknown            ** | No policy rules allow the path segment of the URL, either because it does not match a positive policy rule or because it matches a negative policy rule - a signature. |
| **              Path denied            ** | The path is explicitly denied by an URL blocking policy rule. |
| **              Query unknown            ** | No positive policy rules match the name of the request parameter. |
| **              Query illegal            ** | No policy rules allow the value of the request parameter, either because it does not match a positive policy rule or because it matches a negative policy rule - a signature. |
| **              Session validation failed            ** | The request session ID is not valid, either because the session token has been tampered with or hijacked. |
| **              Form validation failed            ** | The form submitted cannot be verified as having been issued by the web application in a response to a request from the current user session. This is an indication of a CSRF attack. |
| **              Session expired            ** | The request session has exceeded the idle expiration threshold configured in WAF for the web application. |
| **              Malformed XML            ** | Submitted XML request is malformed and hence cannot be parsed and validated. |
| **              Multiple or %u encoded request            ** | The request contains elements that are encoded more than twice or it contains elements that are encoded using %u-encoding. |
| Illegal or malformed Unicode |  |
| Illegal or malformed %u encoding |  |
| **              Authorization failed            ** | User is not authorized to access requested resource. |
| **              Header unknown            ** | Request header not RFC 2616 compliant. |
| **              Header illegal            ** | Header value failed strict validation. |
| **              Header validation failed            ** | Header value failed pragmatic validation. |
| **              Output illegal            ** | Server response contains illegal string. |
| **              HTTP Protocol version            ** | HTTP protocol version not allowed. |
| **              Method illegal            ** | HTTP method not allowed. |
| **              Missing hostname            ** | Request does not specify host name. |
| **              Invalid hostname            ** | Not website proxy is configured for the requested host name. |
| **              Request line maximum length            ** | Entire request line (URI?query) exceeds allowed maximum length. |
| **              Request path maximum length            ** | Request path exceeds allowed maximum length. |
| **              Query string maximum length            ** | Request query exceeds allowed maximum length. |
| **              Content type not enabled            ** | Request content type is supported but not enabled. |
| **              Header name length            ** | Header name exceeds allowed maximum length. |
| **              Header value length            ** | Header value exceeds allowed maximum length. |
| **              Maximum number of headers            ** | Header number exceeds allowed maximum. |
| **              Upload attempt            ** | Upload attempted but upload not allowed. |
| **              Payload length exceeded            ** | POST payload exceeds allowed maximum size. |
| **              Maximum number of upload files            ** | Number of files to upload in a request exceeds allowed maximum. |
| **              Total upload size            ** | Total size of upload files in request exceeds allowed maximum. |
| **              Maximum file size            ** | Size of a single upload file exceeds allowed maximum. |
| **              Cookie version not allowed            ** | Request cookie version not allowed. |
| **              Maximum number of cookies            ** | Number of cookies in request exceeds allowed maximum. |
| **              Cookie name length            ** | Name of a cookie exceeds allowed maximum length. |
| **              Cookie value length            ** | Value of a cookie exceeds allowed maximum length. |
| **              Maximum number of GET parameters            ** | GET parameter number exceeds allowed maximum. |
| **              GET parameter name length            ** | GET parameter name exceeds allowed maximum length. |
| **              GET parameter value length            ** | GET parameter value exceeds allowed maximum length. |
| **              GET parameter combined length            ** | Combined length of GET parameter name and value exceeds allowed maximum length. |
| **              Maximum number of POST parameters            ** | POST parameter number exceeds allowed maximum. |
| **              POST parameter name length            ** | POST parameter name exceeds allowed maximum length. |
| **              POST parameter value length            ** | POST parameter value exceeds allowed maximum length. |
| **              POST parameter combined length            ** | Combined length of POST parameter name and value exceeds allowed maximum length. |
| **General protocol violation** |  |
| **Backend server error** |  |
| **XML payload illegal** |  |
| **              General request violation            ** | Other generic violations. |
| **Add** |  |
| **Remove** |  |
| **Add All** |  |
| **Rem. All** |  |

### Country

<colgroup></colgroup>| **Add** |  |
| **Remove** |  |
| **Add All** |  |
| **Rem. All** |  |

### Lower button bar for filter criteria 

<colgroup></colgroup>| **              Reset            ** Button | Resets the filter criteria to default values. |
| **              Apply            ** Button | Applies defined filter to deny log database. |
| **              Close            ** Button | Closes the filter section. |

#### Blocked and failed requests

Displays requests for resources for the selected proxy that were blocked by WAF.

HTTP headers, URL, parameters and values (if any) that were blocked in the request are highlighted in red color.

Also failed requests are shown in the deny log allowing for identifying broken internal and external links and broken robots not abiding the 404 not found message.

Total number of log entries matching the current filter criteria (if specified) is displayed as **Query returned #number records**. If the total number of records is larger then the **Entries per page** selection, use navigation arrows to navigate the log record back and forth.

Details are expandable: Click **details icon** in the rightmost column to expand.

<table>
  <colgroup>
    <col></col>
    <col></col>
  </colgroup>
  <tbody>
    <tr>
      <td>Checkbox</td>
      <td>
        <p>Mark log entry for adding to the access policy. </p>
        <p>To allow further requests based on the information in the selected log entry/entries, select them and click on the <b>Add selected to ACL</b> button.                           </p>
        <p>Note: parameters that are defined as <code>regexp</code> in web applications and global policy are not automatically updated to allow new values based on the input from the logged requests. In this case, values need to be updated manually.                           </p>
        <p>If adding is not possible the check box is inactive.</p>
      </td>
    </tr>
    <tr>
      <td>
        <b>              Time            </b>
      </td>
      <td>
        <p>Date and time the request was logged.</p>
      </td>
    </tr>
    <tr>
      <td>
        <b>              Source IP            </b>
      </td>
      <td>
        <p>Source IP the request originated from.</p>
        <p>Click on IP-address to get <em>whois information</em>.                           </p>
      </td>
    </tr>
    <tr>
      <td>
        <b>              Host            </b>
      </td>
      <td>
        <p>Hostname from the original request or none if none was present.</p>
      </td>
    </tr>
    <tr>
      <td>
        <b>              Risk            </b>
      </td>
      <td>
        <p>Risk classification of the log entry. Options are:</p>
        <ul>
          <li>
            <p>Critical</p>
          </li>
          <li>
            <p>High</p>
          </li>
          <li>
            <p>Medium</p>
          </li>
          <li>
            <p>Low</p>
          </li>
          <li>
            <p>None</p>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>
        <b>              Class            </b>
      </td>
      <td>
        <p>Attack classification of the log entry. Options are:</p>
        <ul>
          <li>
            <p>SQL injection</p>
          </li>
          <li>
            <p>XPath injection</p>
          </li>
          <li>
            <p>SSI injection</p>
          </li>
          <li>
            <p>OS commanding</p>
          </li>
          <li>
            <p>XSS (Cross Site Scripting)</p>
          </li>
          <li>
            <p>Path traversal</p>
          </li>
          <li>
            <p>Enumeration</p>
          </li>
          <li>
            <p>Format string</p>
          </li>
          <li>
            <p>Buffer overflow</p>
          </li>
          <li>
            <p>DoS attempt</p>
          </li>
          <li>
            <p>Worm probe</p>
          </li>
          <li>
            <p>Access violation</p>
          </li>
          <li>
            <p>Malformed request</p>
          </li>
          <li>
            <p>HTML tags</p>
          </li>
          <li>
            <p>Session invalid</p>
          </li>
          <li>
            <p>XSRF (Cross Site Request Forgery)</p>
          </li>
          <li>
            <p>Session expired</p>
          </li>
          <li>
            <p>Detection evasion</p>
          </li>
          <li>
            <p>Remote file inclusion</p>
          </li>
          <li>
            <p>Information leak</p>
          </li>
          <li>
            <p>Backend error</p>
          </li>
          <li>
            <p>Broken robot</p>
          </li>
          <li>
            <p>Broken int. link</p>
          </li>
          <li>
            <p>Broken ext. link</p>
          </li>
          <li>
            <p>Other</p>
          </li>
          <li>
            <p>None</p>
          </li>
          <li>
            <p>False positive</p>
          </li>
          <li>
            <p>Friendly</p>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>
        <b>              Action            </b>
      </td>
      <td>
        <p>Block action taken on the request. Options are:</p>
        <dl>
          <dt>                Allow              </dt>
          <dd>
            <p>The request was allowed, either because the current mode and white list configuration or because the requests was allowed according to policy. If the request was allowed by policy the reason for the request being logged in the deny log is typically that the backend server responded with an error. Expand the request to see details.                                    </p>
          </dd>
          <dt>                Block              </dt>
          <dd>
            <p>The request was blocked by WAF.</p>
          </dd>
          <dt>                Block-IP              </dt>
          <dd>
            <p>The request was blocked by WAF and the source IP was blacklisted resulting in further requests from that source being blocked at the network level.                                    </p>
          </dd>
          <dt>                Strip              </dt>
          <dd>
            <p>The offending part of the request was stripped before allowing the request. Used for instance to remove session cookies for expired sessions.                                    </p>
          </dd>
        </dl>
      </td>
    </tr>
    <tr>
      <td>
        <b>Response</b>
      </td>
      <td> </td>
    </tr>
    <tr>
      <td>
        <b>              URL Path            </b>
      </td>
      <td>
        <p>The URL path requested.</p>
      </td>
    </tr>
  </tbody>
</table>
To view all entries in the list expanded click the **Report** button in the lower button bar.

In order not to lock the management interface by returning huge amounts of data a maximum of 500 log entries at a time will be displayed in the interactive log interface.

Use the **XML export **function to download larger lists (or the complete log) for off line analysis and archival purposes.

### Lower button bar

The lower button bar contains the following buttons.

<colgroup></colgroup>| **              Flush log            ** Button | Use with caution! When clicking this button and accepting the confirm pop-up window, all log data for that proxy is deleted. |
| **              Log report            ** Button | Generate a printable report based on defined filter criteria (if any). |
| **              Add selected to ACL            ** Button | Adds selected log records to access policy. |

### Access log

Under Log, click **Access log** to access this page.

When *access logging* is enabled, all requests to the website are logged.

The access log is generated on a per day basis. The current log can be monitored and viewed and closed logs are made available for download.

The fields displayed depends on the selected access log format.

### Access log files

Under Log, click **Access log files** to access this page.

When log files are available for download the file name is an active link. To download an access log file click on the file name.

When remote backup is enabled, the latest access log file made available for download will be compressed (using gzip) and copied to the remote backup destination along with the backup of the system configuration.

Several log file formats are available. A condensed WAF specific and some standardized formats, like NCSA Combined (Apache Combined), suitable for importing into log analysis and report generation tools.

See [Access Log Formats](ref_services_policy.md#ref_access_log_formats) for log format definitions.
