## Add a Website

Adds a website for WSM to monitor/protect.

<h3 class="Heading3">URL</h3><p class="method1">
  <kbd>/api/v1/website</kbd>
</p>

<h3 class="Heading3">HTTP Method</h3><p class="method1">POST</p>

<h3 class="Heading3">POST Parameters</h3><table style="margin-left: 0;margin-right: auto;" cellspacing="0">
  <col />
  <col />
  <col />
  <col />
  <col />
  <thead>
    <tr>
      <th>
        <p>Parameter</p>
      </th>
      <th>
        <p>Required</p>
      </th>
      <th>
        <p>Type</p>
      </th>
      <th>
        <p>Description</p>
      </th>
      <th>
        <p>Acceptable Values</p>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <p>deployment</p>
      </td>
      <td>
        <p>true</p>
      </td>
      <td>
        <p>string containing integer</p>
      </td>
      <td>
        <p>Specifies the Deployment Mode.</p>
        <p>For Routing Proxy, IP Forwarding must be enabled.</p>
      </td>
      <td>
        <p>"1" → Reverse Proxy<br />"2" → Routing Proxy </p>
      </td>
    </tr>
    <tr>
      <td>
        <p>enable_hcd</p>
      </td>
      <td>
        <p>false</p>
      </td>
      <td>
        <p>string containing integer</p>
      </td>
      <td>
        <p>Specifies whether to enable health checking.</p>
      </td>
      <td>
        <p>"0" → False<br />"1" → True </p>
      </td>
    </tr>
    <tr>
      <td>
        <p>init_conf</p>
      </td>
      <td>
        <p>true</p>
      </td>
      <td>
        <p>string</p>
      </td>
      <td>
        <p>Specifies the initial configuration to apply. If set to "template", a valid template filename must be provided in the template parameter.</p>
      </td>
      <td>
        <p>"waf_default"<br />"lb_default"<br />"template" </p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ip</p>
      </td>
      <td>
        <p>true</p>
      </td>
      <td>
        <p>string containing ip or "*"</p>
      </td>
      <td>
        <p>Specifies the listen IP. If running in AWS or Azure, this must be set to "*" if present.</p>
      </td>
      <td>
        <p>"&amp;lt;ip address&amp;gt;"<br />"*" </p>
      </td>
    </tr>
    <tr>
      <td>
        <p>preserve_client_ip</p>
      </td>
      <td>
        <p>false</p>
      </td>
      <td>
        <p>string containing integer</p>
      </td>
      <td>
        <p>Specifies whether to configure as a Transparent Proxy (preserve's the client's IP)</p>
        <p>This is not available when running in AWS or Azure.<br />IP Forwarding must be enabled.<br />Real Server Keepalive must be disabled.</p>
      </td>
      <td>
        <p>"0" → False<br />"1" → True</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>rhost</p>
      </td>
      <td>
        <p>true</p>
      </td>
      <td>
        <p>array of strings containing ip addresses or public domain names</p>
      </td>
      <td>
        <p>Specifies the IP address(es) and hostname(s) of the web-server(s) to proxy traffic to.</p>
        <p>Cannot bind to a loopback address (127.*.*.*)</p>
      </td>
      <td>
        <p>["&amp;lt;ip address&amp;gt;", "&amp;lt;ip address&amp;gt;", ...]<br />["&amp;lt;hostname&amp;gt;", "&amp;lt;hostname&amp;gt;", ...]<br />["&amp;lt;ip address&amp;gt;", "&amp;lt;hostname&amp;gt;", ...]</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>rhost_alt_port</p>
      </td>
      <td>
        <p>false</p>
      </td>
      <td>
        <p>array of strings containing integers</p>
      </td>
      <td>
        <p>Specifies alternate port(s) to use when reaching the protected web-servers(s).</p>
        <p>Only required when rhost_proto is set to "both".</p>
      </td>
      <td>
        <p>["&amp;lt;port num&amp;gt;", "&amp;lt;port num&amp;gt;", ...]</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>rhost_port</p>
      </td>
      <td>
        <p>true</p>
      </td>
      <td>
        <p>array of strings containing integers</p>
      </td>
      <td>
        <p>Specifies the port(s) to use when reaching the protected web-server(s).</p>
      </td>
      <td>
        <p>["&amp;lt;port num&amp;gt;", "&amp;lt;port num&amp;gt;", ...]</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>rhost_proto</p>
      </td>
      <td>
        <p>true</p>
      </td>
      <td>
        <p>string</p>
      </td>
      <td>
        <p>Specifies the protocol to use when reaching the protected web-server(s).</p>
        <p>When set to "both", rhost_alt_port is required.</p>
      </td>
      <td>
        <p>"http"<br />"https"<br />"both" </p>
      </td>
    </tr>
    <tr>
      <td>
        <p>rhost_role</p>
      </td>
      <td>
        <p>true</p>
      </td>
      <td>
        <p>array of strings containing integers</p>
      </td>
      <td>
        <p>Specifies the role of the protected web-server(s).</p>
        <p>Active means that requests will be forwarded to the server. When Backup is selected the server will only be used if no Active servers are in operation. Down means that the server should not be used - for instance if it is down for maintenance.</p>
      </td>
      <td>
        <p>"1" → Active<br />"2" → Backup<br />"3" → Down</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>template</p>
      </td>
      <td>
        <p>true</p>
      </td>
      <td>
        <p>string containing template filename</p>
      </td>
      <td>
        <p>Specifies the filename of the template to use. The file must exist if init_conf is set to "template". Otherwise this parameter is not used (convention is to supply "0" if not used).</p>
      </td>
      <td>
        <p>"&amp;lt;filename&amp;gt;"</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>vhost</p>
      </td>
      <td>
        <p>true</p>
      </td>
      <td>
        <p>string containing ip address</p>
      </td>
      <td>
        <p>Specifies the hostname of the Virtual Web Server.</p>
        <p>Cannot bind to a loopback address (127.*.*.*)</p>
      </td>
      <td>
        <p>"&amp;lt;ip address&amp;gt;"</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>vhost_alt_port</p>
      </td>
      <td>
        <p>false</p>
      </td>
      <td>
        <p>string containing integer</p>
      </td>
      <td>
        <p>Specifies the alternate port to listen on for the Virtual Web Server.</p>
        <p>Only required when vhost_proto is set to "both". Represents the HTTP listen port.</p>
      </td>
      <td>
        <p>"&amp;lt;port num&amp;gt;"</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>vhost_port</p>
      </td>
      <td>
        <p>true</p>
      </td>
      <td>
        <p>string containing integer</p>
      </td>
      <td>
        <p>Specifies the port to listen on for the Virtual Web Server.</p>
        <p>Represents the HTTPS listen port when vhost_proto is set to "both".</p>
        <p>Cannot be set to 4849 (reserved for the management UI)</p>
      </td>
      <td>
        <p>"&amp;lt;port num&amp;gt;"</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>vhost_proto</p>
      </td>
      <td>
        <p>true</p>
      </td>
      <td>
        <p>string</p>
      </td>
      <td>
        <p>Specifies the protocol to use for the Virtual Web Server.</p>
        <p>When set to "both", vhost_alt_port is required.</p>
        <p>Cannot be set to 4849 (reserved for the management UI) or equal to vhost_port.</p>
        <p>Must be set to "https" or "both" if rhost_proto is set to "https" or "both".</p>
      </td>
      <td>
        <p>"http"<br />"https"<br />"both" </p>
      </td>
    </tr>
  </tbody>
</table><h3 class="Heading3">Response Parameters</h3><table style="margin-left: 0;margin-right: auto;" cellspacing="0">
  <col />
  <col />
  <col />
  <thead>
    <tr>
      <th>
        <p>Parameter</p>
      </th>
      <th>
        <p>Type</p>
      </th>
      <th>
        <p>Description</p>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <p>mode</p>
      </td>
      <td>
        <p>string containing integer</p>
      </td>
      <td>
        <p>The proxy mode of the website</p>
        <p>"0" → Pass Mode<br />"1" → Protect Mode<br />"3" → Detect Mode</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>status</p>
      </td>
      <td>
        <p>string containing integer</p>
      </td>
      <td>
        <p>The status of the website</p>
        <p>"0" → Disabled<br />"1" → Enabled</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>name</p>
      </td>
      <td>
        <p>string</p>
      </td>
      <td>
        <p>Proxy name</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>rhost</p>
      </td>
      <td>
        <p>array of rhost_details</p>
      </td>
      <td>
        <p>Details about the ip address(es)/hostname(s) of the protected web-server(s)</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>bind</p>
      </td>
      <td>
        <p>array of strings containing ip or "*"</p>
      </td>
      <td>
        <p>The listen IP (corresponds with "ip" above)</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>mirror_of</p>
      </td>
      <td>
        <p>string containing integer</p>
      </td>
      <td>
        <p>Indicates which Proxy ID that the Policy is mirrored from. A value of "0" indicates no mirroring is enabled.</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>sec</p>
      </td>
      <td>
        <p>security_policy</p>
      </td>
      <td>
        <p>Details regarding the policy</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>vhost</p>
      </td>
      <td>
        <p>vhost_details</p>
      </td>
      <td>
        <p>Details about the Virtual Web Server</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>deployment</p>
      </td>
      <td>
        <p>string containing integer</p>
      </td>
      <td>
        <p>The Deployment Mode</p>
        <p>"1" → Reverse Proxy<br />"2" → Routing Proxy</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>id</p>
      </td>
      <td>
        <p>string containing integer</p>
      </td>
      <td>
        <p>Proxy ID</p>
      </td>
    </tr>
  </tbody>
</table>#### rhost_details

An rhost_details object is an array containing the following

<table style="margin-left: 0;margin-right: auto;" cellspacing="0">
  <col />
  <col />
  <col />
  <col />
  <thead>
    <tr>
      <th>
        <p>Index</p>
      </th>
      <th>
        <p>Parameter</p>
      </th>
      <th>
        <p>Type</p>
      </th>
      <th>
        <p>Description</p>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <p>0</p>
      </td>
      <td>
        <p>rhost_proto</p>
      </td>
      <td>
        <p>string</p>
      </td>
      <td>
        <p>The protocol used when reaching the protected web-server</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>1</p>
      </td>
      <td>
        <p>rhost</p>
      </td>
      <td>
        <p>string containing IP address or hostname</p>
      </td>
      <td>
        <p>The IP address or hostname of the web-server to proxy traffic to</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>2</p>
      </td>
      <td>
        <p>rhost_port</p>
      </td>
      <td>
        <p>string containing integer</p>
      </td>
      <td>
        <p>The port to use when reaching the protected web-server</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>3</p>
      </td>
      <td>
        <p>rhost_role</p>
      </td>
      <td>
        <p>string containing integer</p>
      </td>
      <td>
        <p>The role of the protected web-server</p>
        <p>
          <br />"1" → Active<br />"2" → Backup<br />"3" → Down</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>4</p>
      </td>
      <td>
        <p>rhost_status</p>
      </td>
      <td>
        <p>string containing integer</p>
      </td>
      <td>
        <p>The status of the protected web-server</p>
        <p>"0" → ERROR<br />"1" → OK</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>5</p>
      </td>
      <td>
        <p>rhost_alt_port</p>
      </td>
      <td>
        <p>string containing integer</p>
      </td>
      <td>
        <p>The alternate port to use when reaching the protected web-server</p>
      </td>
    </tr>
  </tbody>
</table>#### security_policy

<table style="margin-left: 0;margin-right: auto;" cellspacing="0">
  <col />
  <col />
  <col />
  <thead>
    <tr>
      <th>
        <p>Parameter</p>
      </th>
      <th>
        <p>Type</p>
      </th>
      <th>
        <p>Description</p>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <p>ts</p>
      </td>
      <td>
        <p>string containing integer</p>
      </td>
      <td>
        <p>The tuning status of the proxy</p>
        <p>"0" → Working<br />"1" → Tuned</p>
      </td>
    </tr>
  </tbody>
</table>#### vhost_details

<table style="margin-left: 0;margin-right: auto;" cellspacing="0">
  <col />
  <col />
  <col />
  <thead>
    <tr>
      <th>
        <p>Parameter</p>
      </th>
      <th>
        <p>Type</p>
      </th>
      <th>
        <p>Description</p>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <p>proto</p>
      </td>
      <td>
        <p>string</p>
      </td>
      <td>
        <p>The protocol of the Virtual Web Server</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>port2</p>
      </td>
      <td>
        <p>string containing integer</p>
      </td>
      <td>
        <p>The HTTP listen port of the Virtual Web Server when proto is set to "both"</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>as</p>
      </td>
      <td>
        <p>--</p>
      </td>
      <td>
        <p>Depcrecated</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>proxy_protocol_enabled</p>
      </td>
      <td>
        <p>string containing integer</p>
      </td>
      <td>
        <p>Indicates whether proxy protocol is enabled</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>name</p>
      </td>
      <td>
        <p>string</p>
      </td>
      <td>
        <p>The name of the Virtual Web Server</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>port</p>
      </td>
      <td>
        <p>string containing integer</p>
      </td>
      <td>
        <p>The primary listen port of the Virtual Web Server. Represents the HTTPS listen port when proto is set to "both"</p>
      </td>
    </tr>
  </tbody>
</table>### Example: Add an HTTP website

#### Request

<span class="post">POST</span><p class="method">
  <kbd>/api/v1/website</kbd>
</p>

<span class="post">cURL</span><p class="method">
  <kbd>curl -kv <br />-u api_ninja:ninja_password <br />-X POST <br />-H 'Content-Type: text/json' <br />				--data-binary @addsite.json <br />					https://172.31.1.172:4849/api/v1/website</kbd>
</p>

### POST Parameters

{
    "deployment": "1",
    "enable_hcd": "0",
    "init_conf": "waf_default",
    "ip": "*",
    "rhost": [ "192.168.100.5" ],
    "rhost_alt_port": [],
    "rhost_port": [ "80" ],
    "rhost_proto": "http",
    "rhost_role": [ "1" ],
    "template": "0",
    "vhost": "restful.demo.ba",
    "vhost_alt_port": "",
    "vhost_port": "80",
    "vhost_proto": "http"
}### Response

{
"mode": "3",
"status": "1",
"name": "example",
"rhost": [
["http", "192.168.100.5", "80", "1", "1", "443"]
],
"bind": ["*"],
"mirror_of": "0",
"sec": {
"ts": "0"
},
"vhost": {
"proto": "http",
"port2": "",
"as": "",
"proxy_protocol_enabled": "0",
"name": "example.one.com",
"port": "80"
},
"deployment": "1",
"id": "5"
}### Example: Add a website which uses HTTP and HTTPS on non-standard ports, with 2 backend servers (one active, one backup)

#### Request

<span class="post">POST</span><p class="method">
  <kbd>/api/v1/website</kbd>
</p>

<span class="get">cURL</span><p class="method">
  <kbd>curl -Kv <br />-u api_ninja:ninja_password <br />-X POST <br />-H 'Content-Type: text/json' <br />				--data-binary @addsite2.json <br />https://172.31.1.172:4849/api/v1/website</kbd>
</p>

### POST Parameters

{
    "deployment": "1",
    "enable_hcd": "0",
    "init_conf": "waf_default",
    "ip": "*",
    "rhost": [ "www.example.com", "1.2.3.4" ],
    "rhost_alt_port": [ "4433", "4433" ],
    "rhost_port": [ "8080", "8080" ],
    "rhost_proto": "both",
    "rhost_role": [ "1", "2"],
    "template": "0",
    "vhost": "example.two.com",
    "vhost_alt_port": "8080",
    "vhost_port": "4433",
    "vhost_proto": "both"
}### Response

{
"mode": "3",
"status": "1",
"name": "example",
"rhost": [
["both", "www.example.com", "8080", "1", "1", "4433"],
["both", "1.2.3.4", "8080", "2", "1", "4433"]
],
"bind": ["*"],
"mirror_of": "0",
"sec": {
"ts": "0"
},
"vhost": {
"proto": "both",
"port2": "8080",
"as": "",
"proxy_protocol_enabled": "0",
"name": "example.two.com",
"port": "4433"
},
"deployment": "1",
"id": "6"
}
