## Update a Website's SSL Certificate

Updates the SSL certificate for a website.

<h3 class="Heading3">URL</h3><p class="method1">
  <kbd>/api/v1/website/[website_id]</kbd>
</p>

<h3 class="Heading3">HTTP Method</h3><p class="method1">PUT</p>

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
        <p>website_id</p>
      </td>
      <td>
        <p>true</p>
      </td>
      <td>
        <p>integer</p>
      </td>
      <td>
        <p>Specifies the website ID to update the certificate for.</p>
      </td>
    </tr>
  </tbody>
</table><h3 class="Heading3">PUT Parameters</h3><table style="margin-left: 0;margin-right: auto;" cellspacing="0">
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
        <p>key_pem</p>
      </td>
      <td>
        <p>true</p>
      </td>
      <td>
        <p>string containing PEM encoded cert with proper newlines</p>
      </td>
      <td>
        <p>SSL private key </p>
      </td>
      <td>
        <p> </p>
      </td>
    </tr>
    <tr>
      <td>
        <p>cert_pem</p>
      </td>
      <td>
        <p>true</p>
      </td>
      <td>
        <p>string containing PEM encoded cert with proper newlines</p>
      </td>
      <td>
        <p>SSL public key/certificate</p>
      </td>
      <td>
        <p> </p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ca_pem</p>
      </td>
      <td>
        <p>false</p>
      </td>
      <td>
        <p>string containing PEM encoded cert with proper newlines</p>
      </td>
      <td>
        <p>SSL authority certificate(s) chain</p>
      </td>
      <td>
        <p> </p>
        <p> </p>
      </td>
    </tr>
    <tr>
      <td>
        <p>passphrase</p>
      </td>
      <td>
        <p>false</p>
      </td>
      <td>
        <p>string</p>
      </td>
      <td>
        <p>Passphrase</p>
      </td>
      <td>
        <p> </p>
      </td>
    </tr>
    <tr>
      <td>
        <p>validate_chain</p>
      </td>
      <td>
        <p>false</p>
      </td>
      <td>
        <p>string containing integer</p>
      </td>
      <td>
        <p>Whether to validate the chain.</p>
      </td>
      <td>
        <p>"0" → Don't validate<br />"1" → Validate</p>
      </td>
    </tr>
  </tbody>
</table><h3 class="Heading3">Response Parameters</h3>
Returns a string indicating success/error.

### Example: Update SSL certificate for website 1

#### Request

<span class="put">PUT</span><p class="method">
  <kbd>/api/v1/website</kbd>
</p>

<span class="get">cURL</span><p class="method">
  <kbd>curl -kv <br />-u api_ninja:ninja_password <br />-X PUT <br />-H 'Content-Type: text/json'<br />				--data-binary @updateSSLcert.json<br />					https://172.31.1.172:4849/api/v1/website/1</kbd>
</p>

### PUT Parameters

{
    "key_pem": "-----BEGIN RSA PRIVATE KEY-----\nMIIEowIBA  . . .  wBygvM0FOokt\n-----END RSA PRIVATE KEY-----",
    "cert_pem": "-----BEGIN CERTIFICATE-----\nMIID+j   . . .  otyBZ0ags=\n-----END CERTIFICATE-----",
    "passphrase": "optional_key_passphrase",
    "validate_chain": "0"
}### Response

{"result":"success"}### Example: Update SSL certificate for website 1 with SSL authority certificate chain, and validate the chain

#### Request

<span class="put">PUT</span><p class="method">
  <kbd>/api/v1/website</kbd>
</p>

<span class="get">cURL</span><p class="method">
  <kbd>curl -kv <br />-u api_ninja:ninja_password <br />-X PUT <br />-H 'Content-Type: text/json'<br />						https://172.31.1.172:4849/api/v1/website/1</kbd>
</p>

### PUT Parameters

{
    "key_pem": "-----BEGIN RSA PRIVATE KEY-----\nMIIEowIBA  . . .  wBygvM0FOokt\n-----END RSA PRIVATE KEY-----",
    "cert_pem": "-----BEGIN CERTIFICATE-----\nMIID+j   . . .  otyBZ0ags=\n-----END CERTIFICATE-----",
    "passphrase": "optional_key_passphrase",
    "ca_pem": "-----BEGIN CERTIFICATE-----\nMIIaowIBA  . . .  wBygvMkFOokt\n-----END CERTIFICATE-----",
    "validate_chain": "1"
}### Response

{"result":"success"}
