## Get IPs

Obtains IP address details for physical network interfaces.

### URL

<p class="method1">
  <kbd>/api/v1/interface/getips</kbd>
</p>

<h3 class="Heading3">HTTP Method</h3><p class="method1">GET</p>

<h3 class="Heading3">URL Parameters</h3>
none

<h3 class="Heading3">Response Parameters</h3>
Returns an object containing network interfance, ip_details pairs.

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
        <p>&amp;lt;name of network interface&amp;gt;</p>
      </td>
      <td>
        <p style="font-style: italic;">ip_details</p>
      </td>
      <td>
        <p>The IP details for the network interface.</p>
      </td>
    </tr>
  </tbody>
</table>#### ip_details

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
        <p>addr</p>
      </td>
      <td>
        <p>string containing IP address</p>
      </td>
      <td>
        <p>The IP address of the network interface.</p>
      </td>
    </tr>
    <tr>
      <td>netmask</td>
      <td>string containing netmask</td>
      <td>The netmask of the network interface.</td>
    </tr>
  </tbody>
</table>### Example: Get interfaces

#### Request

<span class="get">GET</span><p class="method">
  <kbd>/api/v1/interface/getips</kbd>
</p>

<span class="get">cURL</span><p class="method">
  <kbd>curl -kv <br />-u api_ninja:ninja_password <br />-X GET <br />https://172.31.1.172:4849/api/v1/interface/getips</kbd>
</p>

#### Response

{
    "eth0": {
        "addr": "10.0.2.15",
        "netmask": "255.255.255.0"
    },
    "eth1": {
        "addr": "192.168.33.11",
        "netmask": "255.255.255.0"
    }
}
