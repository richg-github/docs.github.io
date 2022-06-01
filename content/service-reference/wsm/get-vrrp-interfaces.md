## Get VRRP Interfaces

Obtains list of VRRP interfaces.

<h3 class="Heading3">URL</h3><p class="method1">
  <kbd>/api/v1/interface/virtual</kbd>
</p>

<h3 class="Heading3">HTTP Method</h3><p class="method1">GET</p>

<h3 class="Heading3">URL Parameters</h3>
none

<h3 class="Heading3">Response Parameters</h3>
Returns a JSON structure containing zero or more vrrp_details objects

#### vrrp_details

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
        <p>advskew</p>
      </td>
      <td>
        <p>string containing integer</p>
      </td>
      <td>
        <p>The VRRP advertising skew.</p>
        <p>priority is an abstraction of this value, and adheres to the following relation:</p>
        <p>advskew = 254 - priority</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>alias</p>
      </td>
      <td>
        <p>array of strings containing IP addresses</p>
      </td>
      <td>
        <p>List of IP aliases associated with this VRRP interface</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>carppeer</p>
      </td>
      <td>
        <p>string containing IP address</p>
      </td>
      <td>
        <p>The IP address of the other node in the cluster to sync with.</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>if</p>
      </td>
      <td>
        <p>string containing network interface</p>
      </td>
      <td>
        <p>The physical network interface that the VRRP interface is bound to</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>netmask</p>
      </td>
      <td>
        <p>string containing netmask</p>
      </td>
      <td>
        <p>The netmask of the VRRP interface</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>priority</p>
      </td>
      <td>
        <p>string containing integer</p>
      </td>
      <td>
        <p>The priority of the interface in the VRRP group.</p>
        <p>This is an abstraction of the advskew value, and adheres to the following relation:</p>
        <p>advskew = 254 - priority</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>state_current</p>
      </td>
      <td>
        <p>string</p>
      </td>
      <td>
        <p>State of the VRRP interface, which can be either "MASTER" or "BACKUP"</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>type</p>
      </td>
      <td>
        <p>string containing integer</p>
      </td>
      <td>
        <p>The type of the VRRP interface</p>
        <p>"1" → FAILOVER MASTER<br />"2" → FAILOVER BACKUP</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>vhid</p>
      </td>
      <td>
        <p>string containing integer</p>
      </td>
      <td>
        <p>The virtual host identifier number of the VRRP group</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>vip</p>
      </td>
      <td>
        <p>string containing IP address</p>
      </td>
      <td>
        <p>The virtual IP address shared by the nodes of the cluster</p>
      </td>
    </tr>
  </tbody>
</table>### Example: Get VRRP interfaces

#### Request

<span class="get">GET</span><p class="method">
  <kbd>/api/v1/interface/virtual</kbd>
</p>

<span class="get">cURL</span><p class="method">
  <kbd>curl -kv <br />-u api_ninja:ninja_password <br />-X GET <br />https://172.31.1.172:4849/api/v1/interface/virtual</kbd>
</p>

#### Response

{
    "carp0": {
        "advskew": "50",
        "alias": [
            "123.123.123.1",
            "123.123.123.2",
            "123.123.123.3",
            "123.123.123.4",
            "123.123.123.5",
            "123.123.123.6",
            "123.123.123.7",
            "123.123.123.8",
            "123.123.123.9",
            "123.123.123.10",
            "123.123.123.11",
            "123.123.123.12",
            "123.123.123.13",
            "123.123.123.14",
            "123.123.123.15",
            "123.123.123.16",
            "123.123.123.17",
            "123.123.123.18",
            "123.123.123.19"
        ],
        "carppeer": "224.0.0.18",
        "if": "eth1",
        "netmask": "255.255.255.0",
        "priority": "204",
        "state_current": "MASTER",
        "type": "1",
        "vhid": "2",
        "vip": "123.123.123.123"
    },
    "carp1": {
        "advskew": "100",
        "alias": [],
        "carppeer": "224.0.0.18",
        "if": "eth1",
        "netmask": "255.255.255.0",
        "priority": "154",
        "state_current": "BACKUP",
        "type": "2",
        "vhid": "4",
        "vip": "221.221.221.221"
    }
}
