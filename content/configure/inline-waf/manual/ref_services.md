# Websites

The Service Websites page includes the following sections. Click on the link to go to the corresponding section to learn more:

<!--<MadCap:menuProxy mc-linked-toc="$topicHeadings" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />-->
To go to the documentation for the previous section of the manual, see [Dashboards](ch_dashboards.md). To go to  the documentation for next subsection in the Services section, see [Global](ref_services_http_global.md).

To manage website security profiles, under Services  on the left panel, click **Websites**to go to the Website Overview page.

To save configuration changes or edits you make to any features and options, you must click **Save** on the lower-right of the section or page where you are making changes. Click **apply changes** on the upper-left corner of the page, and then click **OK**. Your changes will not be stored if you do not properly save your changes.

The Website menu gives access to all configuration options related to website security profile, management, ACL administration, security logging, and settings.

### Website lists

#### Defined websites

Displays the list of configured website security profiles in the system. The list shows the `ID`, `Name`, <kbd>Deploy</kbd>, `Virtual web server`, which IP it <kbd>Listens to</kbd>, `Real web server`, <kbd>Status</kbd> and current running `Mode` for each configured proxy.

#### Selecting a website proxy for management

To manage a configured proxy, click on it in the defined proxies list.

#### Changing operating mode

In the list of configured website proxies, select an operating mode from the **Mode** drop-down menu for the website proxy to be changed.

### Adding a website

To add a website, under Services on the left panel, click **Websites**, and then click **Add Website**.

#### Virtual web server

<colgroup></colgroup>| **                Deployment              ** Drop-down list | The proxy deployment mode.<dl><dt>                Valid input              </dt><dd>Select option from list</dd><dt>                Default value              </dt><dd>Reverse Proxy</dd></dl> For a description of the deployment options, see . |
| **                Web server protocol              ** Drop-down list | Select the web server protocol.<dl><dt>                HTTP              </dt><dd>Standard non-encrypted HTTP site.</dd><dt>                HTTPS              </dt><dd>SSL/TLS HTTPS website</dd><dt>                Both              </dt><dd>Create a website that responds to both HTTP and HTTPS requests.</dd></dl> Depending on the deployment architecture, HTTP and Both may not be available in cloud environments. |
| **                Web server domain name              ** Input field | The public address of the web server you want to add a proxy for.<dl><dt>                Valid input              </dt><dd>A fully qualified domain name
For SSL proxies the string can be no longer than 64 characters due to a limitation in the OpenSSL library when generating the initial self signed certificate.</dd><dt>                Input example              </dt><dd>www.mydomain.com</dd><dt>                Default value              </dt><dd>`none`</dd></dl> For SSL websites that require the domain name to be longer than 64 characters, you can initially use a shorter domain name and then add the real domain name as a virtual host alias when the website is created. |
| **                Listen IP              ** Select combo | The IP address the virtual host is bound to. Select an IP address, and then click **Add** or **Remove** to change the IP address configuration.<dl><dt>                Valid input              </dt><dd>One or more IP addresses in the select list to the left.</dd><dt>                Default value              </dt><dd>The IP address(es) configured when creating the website proxy.</dd></dl> |
| **                HTTP listen port              ** Input field | The port number the virtual HTTP host is listening to.<dl><dt>                Valid input              </dt><dd>A valid TCP/IP Port number</dd><dt>                Input example              </dt><dd>`80`</dd><dt>                Default value              </dt><dd>The port number set for the server when created.</dd></dl> |
| **                HTTPS listen port              ** Input field | The port number the virtual HTTPS host is listening to.<dl><dt>                Valid input              </dt><dd>A valid TCP/IP Port number</dd><dt>                Input example              </dt><dd>`443`</dd><dt>                Default value              </dt><dd>The port number set for the server when created.</dd></dl> |

#### Real web servers                     

<table>
  <colgroup>
    <col />
    <col />
  </colgroup>
  <tbody>
    <tr>
      <td>
        <b>                Real server protocol              </b>
        <p>Drop-down list</p>
      </td>
      <td>
        <p>HTTP or HTTPS</p>
        <dl>
          <dt>                Valid input              </dt>
          <dd>
            <p>Options from the drop down list</p>
            <p>
              <code>HTTP</code> or <code>HTTPS</code></p>
            <p>HTTPS is only available if website virtual host is SSL-enabled.</p>
          </dd>
          <dt>                Default value              </dt>
          <dd>
            <p>The protocol initially set when the website proxy was created.</p>
          </dd>
        </dl>
      </td>
    </tr>
    <tr>
      <td>
        <b>                Validate real servers              </b>
        <p>Check box</p>
      </td>
      <td>
        <p>When enabled, Alert Logic Managed Web Application Firewall (WAF):</p>
        <ol>
          <li>
            <p>Verifies that the real servers entered respond to requests</p>
          </li>
          <li>
            <p>Enables health checking with an initial simple configuration</p>
          </li>
        </ol>
        <p>If one or more of the real servers are not reachable WAF returns an error. To disable real server validation, clear this option.                           </p>
        <p>Default: <code>&amp;lt;disabled&amp;gt;</code></p>
      </td>
    </tr>
    <tr>
      <td>
        <b>                Real server IP              </b>
        <p>Input field</p>
      </td>
      <td>
        <p>Hostname or IP address of the web-server(s) WAF is proxying requests for.</p>
        <dl>
          <dt>                Valid input              </dt>
          <dd>
            <p>Fully qualified hostname (FQDN) or IP address. </p>
          </dd>
          <dt>                Input example              </dt>
          <dd>
            <p>
              <code>web1.mycompany.com</code>
            </p>
            <p>
              <code>10.10.10.10</code>
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
        <b>                Port              </b>
        <p>Input</p>
      </td>
      <td>
        <p>The port number the real server is listening to.</p>
        <dl>
          <dt>                Valid input              </dt>
          <dd>
            <p>A valid TCP/IP Port number</p>
          </dd>
          <dt>                Default value              </dt>
          <dd>
            <p>
              <code>80</code>
            </p>
          </dd>
        </dl>
      </td>
    </tr>
    <tr>
      <td>
        <p>
          <b>Alt Port</b>
        </p>
        <p>Input</p>
      </td>
      <td> </td>
    </tr>
    <!--Need Information for Alt Port -->
    <tr>
      <td>
        <b>                Role              </b>
        <p>Drop-down list</p>
      </td>
      <td>
        <p>Define the servers role in the load balancing set.</p>
        <dl>
          <dt>                Active              </dt>
          <dd>
            <p>The server is operative and accepts requests.</p>
          </dd>
          <dt>                Backup              </dt>
          <dd>
            <p>The server is operative but should only be sent requests if none of the other servers in the load balancing set are available.</p>
          </dd>
          <dt>                Down              </dt>
          <dd>
            <p>The server is nor operative and will not respond to requests.</p>
          </dd>
        </dl>
      </td>
    </tr>
  </tbody>
</table>### Initial configuration

<!--Need information on the Initial configuration options -->
### Default proxy

When enabled, the proxy is used as the default host for requests for the IP address the proxy is configured to listen to. The default proxy responds to all requests for virtual hosts that are not configured as primary host name or as a virtual host for other proxies listening to the same IP address. This way it is possible to configure a single proxy that serves requests for several host names that are served by the same backend web server without having to add all the virtual host names in WAF.

### Initial operating mode

Set the initial operating mode for the website proxy. Operating modes are sets of configurations defining what violations to block and what violations to just log. Two configurable and one non-configurable presets are available.

#### Protect

The Protect mode preset by default blocks and logs all violations according to the access policy.

#### Detect

In the default Detect mode, preset only logging occurs and no blocking protection is activated. Blocking protection that would occur in Protect is logged and available for review in the deny log. Operating in the default Detect preset is similar to an intrusion detection system, which detects and logs activities, but does not protect or prevent policy violations.

#### Pass

In Pass mode, all requests are passed through the website proxy. No requests are blocked and no logging is performed. No filters are active in Pass mode, and is not configurable.

Initial operating mode selection is only available in WAF licenses. For load balancer licenses, the operating mode is Pass.

### Removing a proxy

In the website overview, click the delete icon (![](../../../Resources/Images/Icons/delete.png)) on the right of the website proxy you want to remove.
