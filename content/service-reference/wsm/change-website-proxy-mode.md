## Change Website's Proxy Mode

Changes the proxy mode of a website.

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
        <p>Specifies the website ID to change the proxy mode for.</p>
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
        <p>proxy_mode</p>
      </td>
      <td>
        <p>true</p>
      </td>
      <td>
        <p>string containing proxy mode</p>
      </td>
      <td>
        <p>Specifies the proxy mode to change to.</p>
      </td>
      <td>
        <p>"protect"<br />"detect"<br />"pass" </p>
      </td>
    </tr>
  </tbody>
</table><h3 class="Heading3">Response Parameters</h3>
Returns a string indicating success/error.

### Example: Change proxy mode for website 1

#### Request

<span class="put">PUT</span><p class="method">
  <kbd>/api/v1/website/1</kbd>
</p>

<span class="get">cURL</span><p class="method">
  <kbd>curl -kv <br />-u api_ninja:ninja_password <br />-X PUT <br />-H 'Content-Type: text/json' <br />			--data-binary @changeproxymode.json <br />https://172.31.1.172:4849/api/v1/website/1	</kbd>
</p>

#### PUT Parameters

{
"proxy_mode": "protect"
}#### Response

{"result":"success"}
