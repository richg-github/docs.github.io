## Test Connectivity of a Website

Tests connectivity to a website by issuing a HEAD request.

<h3 class="Heading3">URL</h3><p class="method1">
  <kbd>/api/v1/website/[website_id]/test</kbd>
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
        <p>Specifies the website ID to test.</p>
      </td>
    </tr>
  </tbody>
</table><h3 class="Heading3">Response Parameters</h3>
Returns the HTTP(S) response to the HEAD request. Returns both HTTP and HTTPS responses if protocol for website is set to "both".

### Example: Test connectivity to website 1

#### Request

<span class="get">GET</span><p class="method">
  <kbd>/api/v1/website/1/test</kbd>
</p>

<span class="get">cURL</span><p class="method">
  <kbd>curl -kv <br />-u api_ninja:ninja_password <br />-X GET <br />https://172.31.1.172:4849/api/v1/website/1/test</kbd>
</p>

### Response

"HTTP CONNECT
-------------------------------------------------
HTTP\/1.1 200 OK
Date: Wed, 26 Oct 2016 17:08:53 GMT
Content-Type: text\/html
Content-Length: 1270
Connection: close
Vary: Accept-Encoding
Accept-Ranges: bytes
Cache-Control: max-age=604800
Etag: \"359670651+gzip\"
Expires: Wed, 02 Nov 2016 17:08:53 GMT
Last-Modified: Fri, 09 Aug 2013 23:54:35 GMT
X-Cache: HIT
x-ec-custom-error: 1
Server: ECS
 
"
