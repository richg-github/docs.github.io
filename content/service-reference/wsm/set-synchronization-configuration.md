## Set Synchronization Configuration

Sets configuration for proxy settings synchronization.

<p style="margin-top: 0.700em;margin-bottom: 0.700em;">Not available in <MadCap:variable name="ALVariables.AWS" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> Auto Scaling appliances.            </p>

<h3 class="Heading3">URL</h3><p class="method1">
  <kbd>/api/v1/appliance</kbd>
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
      <th class="TableStyle-al_tablestyle-HeadE-Column1-Header1">
        <p>Parameter</p>
      </th>
      <th class="TableStyle-al_tablestyle-HeadE-Column1-Header1">
        <p>Required</p>
      </th>
      <th class="TableStyle-al_tablestyle-HeadE-Column1-Header1">
        <p>Type</p>
      </th>
      <th class="TableStyle-al_tablestyle-HeadE-Column1-Header1">
        <p>Description</p>
      </th>
      <th class="TableStyle-al_tablestyle-HeadD-Column1-Header1">
        <p>Acceptable Values</p>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr class="TableStyle-al_tablestyle-Body-Body1">
      <td>
        <p>mode</p>
      </td>
      <td>
        <p>false</p>
      </td>
      <td>
        <p>string</p>
      </td>
      <td>
        <p>Specifies the synchronization mode.</p>
        <p>Defaults to "learn"</p>
      </td>
      <td>
        <p>"teach"<br />"learn" </p>
      </td>
    </tr>
    <tr class="TableStyle-al_tablestyle-Body-Body1">
      <td>
        <p>password</p>
      </td>
      <td>
        <p>true</p>
      </td>
      <td>
        <p>string</p>
      </td>
      <td>
        <p>Specifies whether to enable health checking.</p>
      </td>
      <td>
        <p>alphanumeric, space, dash, slash, underscore, period and parentheses.<br />8-32 characters</p>
      </td>
    </tr>
    <tr class="TableStyle-al_tablestyle-Body-Body1">
      <td>
        <p>peer</p>
      </td>
      <td>
        <p>false</p>
      </td>
      <td>
        <p>string containing IP address, or array of strings containing IP addresses</p>
      </td>
      <td>
        <p>Specifies the IP address(es) of the peer(s) to sync with.</p>
        <p>Required when protocol is set to "unicast". Parameter is ignored for "multicast".</p>
      </td>
      <td>
        <p>"&amp;lt;ip address&amp;gt;"<br />["&amp;lt;ip address&amp;gt;", "&amp;lt;ip address&amp;gt;", ...]</p>
      </td>
    </tr>
    <tr class="TableStyle-al_tablestyle-Body-Body1">
      <td>
        <p>protocol</p>
      </td>
      <td>
        <p>true</p>
      </td>
      <td>
        <p>string</p>
      </td>
      <td>
        <p>Specifies the transmission protocol.</p>
        <p>Only "unicast" is supported in AWS or Azure.</p>
      </td>
      <td>
        <p>"unicast"<br />"multicast" </p>
      </td>
    </tr>
    <tr class="TableStyle-al_tablestyle-Body-Body1">
      <td>
        <p>status</p>
      </td>
      <td>
        <p>false</p>
      </td>
      <td>
        <p>string containing integer</p>
      </td>
      <td>
        <p>Specifies whether proxy settings synchronization is enabled.</p>
        <p>Defaults to "0".</p>
      </td>
      <td>
        <p>"0" → Disabled<br />"1" → Enabled</p>
      </td>
    </tr>
    <tr class="TableStyle-al_tablestyle-Body-Body1">
      <td>
        <p>sync_style</p>
      </td>
      <td>
        <p>true</p>
      </td>
      <td>
        <p>string</p>
      </td>
      <td>
        <p>Specifies the what to sync among the cluster.</p>
        <p>If set to "full" and appliance is configured for multiple SSL proxies, the Listen IP of each proxy must be set to "*" (All Inbound).</p>
      </td>
      <td>
        <p>"full"<br />"template" </p>
      </td>
    </tr>
    <tr class="TableStyle-al_tablestyle-Body-Body1">
      <td>
        <p>interface</p>
      </td>
      <td>
        <p>false</p>
      </td>
      <td>
        <p>array of strings containing integers</p>
      </td>
      <td>
        <p>Enables synchronization on the specified interface if provided.</p>
        <p>Parameter not usable if a different interface is already configured for synchronization.</p>
      </td>
      <td class="TableStyle-al_tablestyle-BodyA-Column1-Body1">
        <p>Name of interface (list of interfaces can be obtained with Get Interfaces)</p>
      </td>
    </tr>
  </tbody>
</table><h3 class="Heading3">Response Parameters</h3>
Returns a string indicating success/error.

### Example: Configure appliance sync config as a unicast learner with a single peer

#### Request

<span class="post">POST</span><p class="method">
  <kbd>/api/v1/appliance</kbd>
</p>

<span class="get">cURL</span><p class="method">
  <kbd>curl -kv <br />-u api_ninja:ninja_password <br />-X POST <br />-H 'Content-Type: text/json'<br />				--data-binary @setsync.json<br />https://172.31.1.172:4849/api/v1/appliance</kbd>
</p>

### POST Parameters

{
"mode": "learn",
"password": "ninja_password",
"peer": "1.2.3.4",
"protocol": "unicast",
"status": "1",
"sync_style": "full"
}### Response

{"result":"success"}### Example: Configure appliance sync settings as a multicast teacher

#### Request

<span class="post">POST</span><p class="method">
  <kbd>/api/v1/website</kbd>
</p>

<span class="get">cURL</span><p class="method">
  <kbd>curl -kv <br />-u api_ninja:ninja_password <br />-X POST <br />-H 'Content-Type: text/json'<br />				--data-binary @setsync.json<br />https://172.31.1.172:4849/api/v1/appliance</kbd>
</p>

#### POST Parameters

{
"mode": "teach",
"password": "ninja_password",
"protocol": "multicast",
"status": "1",
"sync_style": "full"
}#### Response

{"result":"success"}### Example: Configure appliance sync settings as a unicast teacher with multiple peers, and also enable synchronization on eth1

#### Request

<span class="post">POST</span><p class="method">
  <kbd>/api/v1/appliance</kbd>
</p>

<span class="get">cURL</span><p class="method">
  <kbd>curl -kv <br />-u api_ninja:ninja_password <br />-X POST <br />-H 'Content-Type: text/json'<br />				--data-binary @setsync.json<br />https://172.31.1.172:4849/api/v1/appliance</kbd>
</p>

#### POST Parameters

{
"mode": "teach",
"password": "ninja_password",
"peer": [
"4.3.2.1",
"5.4.3.2"
],
"protocol": "unicast",
"status": "1",
"sync_style": "template",
"interface": "eth1"
}
#### Response

{"result":"success"}
