## Provision an Appliance

<p>Provisions a <MadCap:variable name="ALVariables.WSM_OutBndWaf_2" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> (WSM) appliance, and optionally can add a new API user.</p>

<p style="margin-top: 0.700em;margin-bottom: 0.700em;">This API call is the only one which can be called without an API user. All other API calls must authenticate with an API user's credentials.<![CDATA[
            ]]></p>

<h3 class="Heading3">URL</h3><p class="method1">
  <kbd>/api/v1/appliance</kbd>
</p>

<h3 class="Heading3">HTTP Method</h3><p class="method1">POST</p>

<h3 class="Heading3">POST Parameters</h3><table style="margin-left: 0;margin-right: auto;" cellspacing="0">
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
        <p>key</p>
      </td>
      <td>
        <p>true</p>
      </td>
      <td>
        <p>string</p>
      </td>
      <td>
        <p>Specifies the WSM license key to provision the appliance with.</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>public_ip</p>
      </td>
      <td>
        <p>true</p>
      </td>
      <td>
        <p>string</p>
      </td>
      <td>
        <p>Specifies the public IP of the WSM appliance.</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>api_user</p>
      </td>
      <td>
        <p>false</p>
      </td>
      <td>
        <p>string</p>
      </td>
      <td>
        <p>Specifies the username of the API user to be created.</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>api_password</p>
      </td>
      <td>
        <p>false</p>
      </td>
      <td>
        <p>string</p>
      </td>
      <td>
        <p>Specifies the password of the API user to be created.</p>
      </td>
    </tr>
  </tbody>
</table><h3 class="Heading3">Response Parameters</h3><p>Returns a message string indicating whether the <MadCap:variable name="ALVariables.WSM_OutBndWaf_2" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> appliance was successfully provisioned.</p>

### Example: Provision an Appliance

#### Request

<span class="get">POST</span><p class="method">
  <kbd>/api/v1/appliance</kbd>
</p>

<span class="get">cURL</span><p class="method">
  <kbd>curl -kv <br />-X POST <br />-H 'Content-Type: text/json'<br />--data-binary @prov.json<br />https://172.31.1.172:4849/api/v1/appliance</kbd>
</p>

#### POST Parameters

{
        "key": "examplekey947ac79b4a774348debf9fdeba93a4examplekey",
        "public_ip": "5.6.7.8"
}#### Response

"appliance successfully provisioned"

### Example: Provision an Appliance and Create a New API User

#### Request

<span class="post">POST</span><p class="method">
  <kbd>/api/v1/appliance</kbd>
</p>

<span class="post">cURL</span><p class="method">
  <kbd>curl -kv <br />-X POST <br />-H 'Content-Type: text/json' <br />--data-binary @prov.json				<br />https://172.31.1.172:4849/api/v1/appliance</kbd>
</p>

#### POST Parameters

{
        "key": "examplekey947ac79b4a774348debf9fdeba93a4examplekey",
        "public_ip": "5.6.7.8",
        "api_user": "api_ninja",
        "api_password": "ninja_password"
}#### Response

"appliance successfully provisioned"
