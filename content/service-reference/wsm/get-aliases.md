## Get Website Aliases (WSM 4.5.7.0+ only)

Obtains aliases for a given website.

<h3 class="Heading3">URL</h3><p class="method1">
  <kbd>/api/v1/website/[website_id]/aliases</kbd>
</p>

<h3 class="Heading3">HTTP Method</h3><p class="method1">GET</p>

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
        <p>Specifies the website ID to return aliases for.</p>
      </td>
    </tr>
  </tbody>
</table><h3 class="Heading3">Response Parameters</h3>
Returns an array of strings containing aliases. An empty array will be returned if no aliases exist.

### Example: Get Website Aliases

#### Request

<span class="delete">GET</span><p class="method">
  <kbd>/api/v1/website/[website_id]/aliases</kbd>
</p>

<span class="delete">cURL</span><p class="method">
  <kbd>curl -kv \<br />-u api_ninja:ninja_password \<br />-X GET \<br />https://172.31.1.172:4849/api/v1/website/1/aliases</kbd>
</p>

#### Response

["www.example.com","another.example.com"]
