## Get Website Redirects (WSM 4.5.7.0+ only)

Obtains redirects for a given website.

<h3 class="Heading3">URL</h3><p class="method1">
  <kbd>/api/v1/website/[website_id]/redirects</kbd>
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
        <p>Specifies the website ID to return redirects for.</p>
      </td>
    </tr>
  </tbody>
</table>### Response Parameters

Response is an array of redirect_details objects.A redirect_details object contains the following:

| Parameter | Type | Description |
|---|---|---|
| proto | string | The scheme being redirected. "http" → HTTP "https" → HTTPS It is an error to specify http for an https-only website, or https for an http-only website. |
| match_type | string | The type of match to perform. "prefix" → Literal prefix matching path "regex" → Regular expression matching path "vhost regex" → Regular expression matching virtual host |
| match | string | Content to match. |
| rd_exernally_to | string | Full URL to redirect to, including scheme. |

### Example: Get redirects for website 1

#### Request

<span class="delete">GET</span><p class="method">
  <kbd>/api/v1/website/1/redirects</kbd>
</p>

<span class="delete">cURL</span><p class="method">
  <kbd>curl -kv \<br />-u api_ninja:ninja_password \<br />-X GET \            <br />          https://172.31.1.172:4849/api/v1/website/1/redirects</kbd>
</p>

#### Response

[
  {
    "proto": "http",
    "match_type": "prefix",
    "match": "/prefix",
    "rd_externally_to": "http://example.com/prefix/"
  },
  {
    "proto": "https",
    "match_type": "prefix",
    "match": "/https-prefix",
    "rd_externally_to": "http://example.com/prefix/"
  },
  {
    "proto": "http",
    "match_type": "regex",
    "match": "\\d+",
    "rd_externally_to": "http://example.com/number/"
  }
]
