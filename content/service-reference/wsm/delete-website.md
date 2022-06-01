## Delete a Website

Deletes a website.

This API call is not idempotent

<h3 class="Heading3">URL</h3><p class="method1">
  <kbd>/api/v1/website/[website_id]</kbd>
</p>

<h3 class="Heading3">HTTP Method</h3><p class="method1">Delete</p>

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
        <p>Specifies the website ID to delete.</p>
      </td>
    </tr>
  </tbody>
</table><h3 class="Heading3">Response Parameters</h3>
Returns a string indicating success/error.

### Example: Delete website 1

#### Request

<span class="delete">DELETE</span><p class="method">
  <kbd>/api/v1/website/1</kbd>
</p>

<span class="delete">cURL</span><p class="method">
  <kbd>curl -kv <br />-u api_ninja:ninja_password <br />-X DELETE <br />https://172.31.1.172:4849/api/v1/website/1</kbd>
</p>

#### Response

{"result":"success"}
