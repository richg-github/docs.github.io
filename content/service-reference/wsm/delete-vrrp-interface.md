## Delete VRRP Interface

Deletes a VRRP interface.

<h3 class="Heading3">URL</h3><p class="method1">
  <kbd>/api/v1/interface/virtual/[id]<br />				/api/v1/interface/virtual/[id]/force</kbd>
</p>

<h3 class="Heading3">HTTP Method</h3><p class="method1">DELETE</p>

<h3 class="Heading3">URL Parameters</h3><table style="margin-left: 0;margin-right: auto;" cellspacing="0">
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
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <p>id</p>
      </td>
      <td>
        <p>true</p>
      </td>
      <td>
        <p>integer</p>
      </td>
      <td>
        <p>Specifies the ID of the VRRP interface to delete.</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>force</p>
      </td>
      <td>
        <p>false</p>
      </td>
      <td>
        <p>string</p>
      </td>
      <td>
        <p>Forces deletion of VRRP interface, even if a website is configured to listen on it.</p>
      </td>
    </tr>
  </tbody>
</table><h3 class="Heading3">Response Parameters</h3>
Returns a string indicating success/error.

### Example: Delete VRRP interface

#### Request

<span class="delete">DELETE</span><p class="method">
  <kbd>/api/v1/interface/virtual/carp0</kbd>
</p>

<span class="delete">cURL</span><p class="method">
  <kbd>curl -kv <br />-u api_ninja:ninja_password <br />-X DELETE 									<br />https://172.31.1.172:4849/api/v1/interface/virtual/carp0</kbd>
</p>

#### Response

{"result":"success"}### Example: Force delete VRRP interface

#### Request

<span class="delete">DELETE</span><p class="method">
  <kbd>/api/v1/interface/virtual/carp0/force</kbd>
</p>

<span class="delete">cURL</span><p class="method">
  <kbd>curl -kv <br />-u api_ninja:ninja_password <br />-X DELETE 									<br />https://172.31.1.172:4849/api/v1/interface/virtual/carp0/force</kbd>
</p>

#### Response

{"result":"success"}
