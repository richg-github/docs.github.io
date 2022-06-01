## Get website details

Obtains configuration details for a given website.

### URL

/api/v1/website/[website_id]

### HTTP Method

<p class="method1">GET</p>

### URL Parameters

<table style="width: 100%;" cellspacing="0">
  <col style="width: 125px;" />
  <col style="width: 110px;" />
  <col style="width: 110px;" />
  <col />
  <thead>
    <tr>
      <th>Parameter</th>
      <th>Required</th>
      <th>Type</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>website_id</td>
      <td>true</td>
      <td>integer</td>
      <td>Specifies the website ID to return detail for.</td>
    </tr>
  </tbody>
</table>### Response Parameters

<table style="width: 100%;" cellspacing="0">
  <col style="width: 125px;" />
  <col style="width: 110px;" />
  <col />
  <thead>
    <tr>
      <th>Parameter</th>
      <th>Type</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>mode</td>
      <td>string containing integer	</td>
      <td>
        <p>The proxy mode of the website</p>
        <p>"0" → Pass Mode</p>
        <p>"1" → Protect Mode</p>
        <p>"3" → Detect Mode</p>
      </td>
    </tr>
    <tr>
      <td>status</td>
      <td>string containing integer	</td>
      <td>
        <p>The status of the website</p>
        <p>"0" → Disabled</p>
        <p>"1" → Enabled</p>
      </td>
    </tr>
    <tr>
      <td>name</td>
      <td>string</td>
      <td>Proxy name</td>
    </tr>
    <tr>
      <td>rhost</td>
      <td>array of <b style="font-style: italic;">rhost_details</b></td>
      <td>Details about the ip address(es)/hostname(s) of the protected web-server(s)</td>
    </tr>
    <tr>
      <td>bind</td>
      <td>array of strings containing ip or "*"</td>
      <td>The listen IP (corresponds with "ip" above)</td>
    </tr>
    <tr>
      <td>mirror_of</td>
      <td>string containing integer</td>
      <td>Indicates which Proxy ID that the Policy is mirrored from. A value of "0" indicates no mirroring is enabled.</td>
    </tr>
    <tr>
      <td>sec</td>
      <td>
        <b style="font-style: italic;">policy_ details</b>
      </td>
      <td>Details regarding security settings</td>
    </tr>
    <tr>
      <td>vhost</td>
      <td>
        <b style="font-style: italic;">vhost_details</b>
      </td>
      <td>Details about the Virtual Web Server</td>
    </tr>
    <tr>
      <td>deployment</td>
      <td>string containing integer</td>
      <td>
        <p>The Deployment Mode</p>
        <p>"1" → Reverse Proxy</p>
        <p>"2" → Routing Proxy</p>
      </td>
    </tr>
    <tr>
      <td>id</td>
      <td>string containing integer</td>
      <td>Proxy ID</td>
    </tr>
  </tbody>
</table><p style="font-weight: bold;font-style: italic;">rhost_details</p>

<table style="width: 100%;" cellspacing="0">
  <col style="width: 125px;" />
  <col style="width: 110px;" />
  <col style="width: 110px;" />
  <col />
  <thead>
    <tr>
      <th>Index</th>
      <th>Parameter</th>
      <th>Type</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>0</td>
      <td>rhost_proto</td>
      <td>string</td>
      <td>The protocol used when reaching the protected web-server</td>
    </tr>
    <tr>
      <td>1</td>
      <td>rhost</td>
      <td>string containing IP address or hostname</td>
      <td>The IP address or hostname of the web-server to proxy traffic to</td>
    </tr>
    <tr>
      <td>2</td>
      <td>rhost_port</td>
      <td>string containing integer</td>
      <td>The port to use when reaching the protected web-server</td>
    </tr>
    <tr>
      <td>3</td>
      <td>rhost_role</td>
      <td>string containing integer</td>
      <td>
        <p>The role of the protected web-server</p>
        <p>"1" → Active</p>
        <p>"2" → Backup</p>
        <p>"3" → Down</p>
      </td>
    </tr>
    <tr>
      <td>4</td>
      <td>rhost_status</td>
      <td>string containing integer</td>
      <td>
        <p>The status of the protected web-server</p>
        <p>"0" → ERROR</p>
        <p>"1" → OK</p>
      </td>
    </tr>
    <tr>
      <td>5</td>
      <td>rhost_alt_port</td>
      <td>string containing integer</td>
      <td>The alternate port to use when reaching the protected web-server</td>
    </tr>
  </tbody>
</table><p style="font-weight: bold;font-style: italic;">policy_details</p>

<table style="width: 100%;" cellspacing="0">
  <col style="width: 110px;" />
  <col style="width: 110px;" />
  <col />
  <thead>
    <tr>
      <th>Parameter</th>
      <th>Type</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>ts</td>
      <td>string containing integer</td>
      <td>
        <p>The tuning status of the proxy</p>
        <p>"0" → Working</p>
        <p>"1" → Tuned</p>
      </td>
    </tr>
  </tbody>
</table><p style="font-weight: bold;font-style: italic;">vhost_details</p>

<table style="width: 100%;" cellspacing="0">
  <col style="width: 110px;" />
  <col style="width: 110px;" />
  <col />
  <thead>
    <tr>
      <th>Parameter</th>
      <th>Type</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>proto</td>
      <td>string</td>
      <td>The protocol of the Virtual Web Server</td>
    </tr>
    <tr>
      <td>port2</td>
      <td>string containing integer</td>
      <td>The HTTP listen port of the Virtual Web Server when proto is set to "both"</td>
    </tr>
    <tr>
      <td>as</td>
      <td>--</td>
      <td>
        <i>Deprecated</i>
      </td>
    </tr>
    <tr>
      <td>proxy_protocol_enabled</td>
      <td>string containing integer</td>
      <td>
        <p>Indicates whether proxy protocol is enabled</p>
      </td>
    </tr>
    <tr>
      <td>name</td>
      <td>string</td>
      <td>
        <p>The name of the Virtual Web Server</p>
      </td>
    </tr>
    <tr>
      <td>port</td>
      <td>string containing integer</td>
      <td>The primary listen port of the Virtual Web Server. Represents the HTTPS listen port when <b>proto</b> is set to "both"</td>
    </tr>
  </tbody>
</table>### Example: Get available websites

#### Request

<span class="get">GET</span><p class="method">
  <kbd>/api/v1/website</kbd>
</p>

<span class="get">cURL</span><p class="method">
  <kbd>curl -kv             <br />-u api_ninja:ninja_password            <br />-X GET            <br />https://172.31.1.172:4849/api/v1/website</kbd>
</p>

<MadCap:snippetBlock src="../../Resources/Snippets/api/copyPasteApiEx.flsnp" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd"></MadCap:snippetBlock>#### Response

{

<p style="text-indent: 0.5in;">"bind": [</p>

<p style="text-indent: 1in;">"*"</p>

<p style="text-indent: 0.5in;">],</p>

<p style="text-indent: 0.5in;">"deployment": "1",</p>

<p style="text-indent: 0.5in;">"id": "1",</p>

<p style="text-indent: 0.5in;">"mirror_of": "0",</p>

<p style="text-indent: 0.5in;">"mode": "3",</p>

<p style="text-indent: 0.5in;">"name": "example",</p>

<p style="text-indent: 0.5in;">"rhost": [</p>

<p style="text-indent: 1in;">[</p>

<p style="text-indent: 1.5in;">"http",</p>

<p style="text-indent: 1.5in;">"1.2.3.4",</p>

<p style="text-indent: 1.5in;">"80",</p>

<p style="text-indent: 1.5in;">"1",</p>

<p style="text-indent: 1.5in;">"1",</p>

<p style="text-indent: 1.5in;">"443"</p>

<p style="text-indent: 1in;">],</p>

<p style="text-indent: 1in;">[</p>

<p style="text-indent: 1.5in;">"http",</p>

<p style="text-indent: 1.5in;">"2.3.4.5",</p>

<p style="text-indent: 1.5in;">"80",</p>

<p style="text-indent: 1.5in;">"2",</p>

<p style="text-indent: 1.5in;">"1",</p>

<p style="text-indent: 1.5in;">"443"</p>

<p style="text-indent: 1in;">],</p>

<p style="text-indent: 1in;">[</p>

<p style="text-indent: 1.5in;">"http",</p>

<p style="text-indent: 1.5in;">"3.4.5.6",</p>

<p style="text-indent: 1.5in;">"80",</p>

<p style="text-indent: 1.5in;">"3",</p>

<p style="text-indent: 1.5in;">"1",</p>

<p style="text-indent: 1.5in;">"443"</p>

<p style="text-indent: 1in;">]</p>

<p style="text-indent: 0.5in;">],</p>

<p style="text-indent: 0.5in;">"sec": {</p>

<p style="text-indent: 0.5in;">"ts": "0"</p>

<p style="text-indent: 0.5in;">},</p>

<p style="text-indent: 0.5in;">"status": "1",</p>

<p style="text-indent: 0.5in;">"vhost": {</p>

<p style="text-indent: 1in;">"as": "",</p>

<p style="text-indent: 1in;">"name": "example.rhostroles.com",</p>

<p style="text-indent: 1in;">"port": "80",</p>

<p style="text-indent: 1in;">"port2": "",</p>

<p style="text-indent: 1in;">"proto": "http",</p>

<p style="text-indent: 1in;">"proxy_protocol_enabled": "1"</p>

<p style="text-indent: 0.5in;">}</p>

}
