## Add Website Aliases (WSM 4.5.7.0+ only)

Adds aliases to a given website, ignoring any pre-existing aliases.

<h3 class="Heading3">URL</h3><p class="method1">
  <kbd>/api/v1/website/[website_id]/aliases</kbd>
</p>

<h3 class="Heading3">HTTP Method</h3><p class="method1">POST</p>

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
        <p>Specifies the website ID to add aliases to.</p>
      </td>
    </tr>
  </tbody>
</table><h3 class="Heading3">POST Parameters</h3>
POST takes a JSON array of strings containing new aliases. An empty array will do nothing successfully. Aliases which already exist for the given website will be ignored.

<h3 class="Heading3">Response Parameters</h3>
Returns a string indicating success/error.

### Example: Set Website Aliases

#### Request

<span class="delete">PUT</span><p class="method">
  <kbd>/api/v1/website/[website_id]/aliases</kbd>
</p>

<span class="delete">cURL</span><p class="method">
  <kbd>curl -kv \<br />-u api_ninja:ninja_password \<br />-X PUT \            <br />          -H 'Content-Type: application/json' \<br />         -d '[ "www.example.com", "another.example.com" ]' \<br />          https://172.31.1.172:4849/api/v1/website/1/aliases</kbd>
</p>

#### Response

{"result":"success"}
