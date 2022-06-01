## Add VRRP Interface

Adds a VRRP interface.

### URL

<p class="method1">
  <kbd>/api/v1/interface</kbd>
</p>

### HTTP Method

<p class="method1">POST</p>

POST Parameters

<table style="margin-left: 0;margin-right: auto;" cellspacing="0">
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
        <p>vip</p>
      </td>
      <td>
        <p>true</p>
      </td>
      <td>
        <p>string containing ip address</p>
      </td>
      <td>
        <p>Specifies the virtual IP address shared by the nodes of the cluster.</p>
      </td>
      <td>
        <p>"&amp;lt;ip address&amp;gt;" </p>
      </td>
    </tr>
    <tr>
      <td>
        <p>netmask</p>
      </td>
      <td>
        <p>true</p>
      </td>
      <td>
        <p>string containing netmask</p>
      </td>
      <td>
        <p>Specifies the netmask of the VRRP interface.</p>
      </td>
      <td>
        <p>"&amp;lt;netmask&amp;gt;"</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>interface</p>
      </td>
      <td>
        <p>true</p>
      </td>
      <td>
        <p>string containing interface</p>
      </td>
      <td>
        <p>Specifies the physical network interface that the VRRP interface will be bound to.</p>
        <p> </p>
      </td>
      <td>
        <p>"&amp;lt;network interface&amp;gt;"</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>type</p>
      </td>
      <td>
        <p>true</p>
      </td>
      <td>
        <p>string</p>
      </td>
      <td>
        <p>Specifies the VRRP interface type.</p>
      </td>
      <td>
        <p>"master"<br />"backup" </p>
      </td>
    </tr>
  </tbody>
</table>### Response Parameters

Returns a string indicating success/error.

### Example: Set VRRP interface

#### Request

<span class="post">POST</span><p class="method">
  <kbd>/api/v1/interface</kbd>
</p>

<span class="get">cURL</span><p class="method">
  <kbd>curl -kv <br />-u api_ninja:ninja_password <br />-X POST 				<br />-H 'Content-Type: text/json'					<br />--data-binary @setsync.json					<br />https://172.31.1.172:4849/api/v1/appliance</kbd>
</p>

#### POST Parameters

{
"vip": "200.0.0.1",
"netmask": "255.255.255.0",
"interface": "eth1",
"type": "master"
}
#### Response

{"result":"success"}
