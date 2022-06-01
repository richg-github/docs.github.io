## Get Synchronization Configuration

Obtains synchronization configuration.

<h3 class="Heading3">URL</h3><p class="method1">
  <kbd>/api/v1/appliance/syncsettings</kbd>
</p>

<h3 class="Heading3">HTTP Method</h3><p class="method1">GET</p>

<h3 class="Heading3">URL Parameters</h3>
none

<h3 class="Heading3">Response Parameters</h3><table style="margin-left: 0;margin-right: auto;" cellspacing="0">
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
        <p>Synchronization mode</p>
        <p>"0" → Teach<br />"1" → Learn </p>
      </td>
    </tr>
    <tr>
      <td>
        <p>password</p>
      </td>
      <td>
        <p>string</p>
      </td>
      <td>
        <p>Synchronization password</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>peer</p>
      </td>
      <td>
        <p>array of strings containing IP addresses</p>
      </td>
      <td>
        <p>The IP address(es) of the peer(s) to sync with</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>protocol</p>
      </td>
      <td>
        <p>string containing integer</p>
      </td>
      <td>
        <p>Transmission type</p>
        <p>"0" → Unicast<br />"1" → Multicast</p>
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
        <p>Whether proxy settings synchronization is enabled</p>
        <p>"0" → Disabled<br />"1" → Enabled</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>sync_style</p>
      </td>
      <td>
        <p>string containing integer</p>
      </td>
      <td>
        <p>Synchronization type</p>
        <p>"1" → Full Sync<br />"2" → Template </p>
      </td>
    </tr>
  </tbody>
</table>### Example: Get synchronization configuration

#### Request

<span class="get">GET</span><p class="method">
  <kbd>/api/v1/appliance/syncsettings</kbd>
</p>

<span class="get">cURL</span><p class="method">
  <kbd>curl -kv <br />-u api_ninja:ninja_password <br />-X GET 				<br />https://172.31.1.172:4849/api/v1/appliance/syncsettings</kbd>
</p>

#### Response

{
    "mode": "0",
    "password": "ninja_password",
    "peer": [
        "4.3.2.1"
    ],
    "protocol": "0",
    "status": "0",
    "sync_style": "1"
}
