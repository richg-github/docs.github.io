## Get Interfaces

Obtains list of physical network interfaces.

### URL

<p class="method1">
  <kbd>/api/v1/interface/physical</kbd>
</p>

<h3 class="Heading3">HTTP Method</h3><p class="method1">GET</p>

<h3 class="Heading3">URL Parameters</h3>
none

<h3 class="Heading3">Response Parameters</h3>
Returns an array of strings containing interfaces.

### Example: Get interfaces

#### Request

<span class="get">GET</span><p class="method">
  <kbd>/api/v1/interface/physical</kbd>
</p>

<span class="get">cURL</span><p class="method">
  <kbd>curl -kv <br />-u api_ninja:ninja_password <br />-X GET <br />https://172.31.1.172:4849/api/v1/interface/physical</kbd>
</p>

#### Response

[
    "eth0",
    "eth1"
]
