## Get website denylog

Returns denylog entries for a given website.

### URL

/api/v1/website/[website_id]/denylog

### HTTP Method

<p class="method1">GET</p>

### URL Parameters

<table style="width: 100%;" cellspacing="0">
  <col style="width: 125px;" />
  <col style="width: 110px;" />
  <col style="width: 110px;" />
  <col />
  <thead>
    <tr>
      <th>Parameter</th>
      <th>Required</th>
      <th>Type</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>website_id</td>
      <td>true</td>
      <td>integer</td>
      <td>Specifies the website ID to return denylog entries for.</td>
    </tr>
  </tbody>
</table><h3>
  <MadCap:annotation MadCap:createDate="2016-11-14T08:11:09.4280617-06:00" MadCap:creator="cmimoso" MadCap:initials="CM" MadCap:comment="not the same as rest of api format - other pages have them in tables" MadCap:editor="cmimoso" MadCap:editDate="2016-11-14T08:12:50.3000887-06:00" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd">Response </MadCap:annotation>Parameters</h3>
Returns an array of denylog_entry.

#### denylog_entry

A denylog_entry object is an array containing the following:

<table style="margin-left: 0;margin-right: auto;" cellspacing="0">
  <col style="width: 37pt;" />
  <col style="width: 98pt;" />
  <col style="width: 102pt;" />
  <col style="width: 239pt;" />
  <thead>
    <tr>
      <th>
        <p class="p_1">Index</p>
      </th>
      <th>
        <p class="p_1">Parameter</p>
      </th>
      <th>
        <p class="p_1">Type</p>
      </th>
      <th>
        <p class="p_1">Description</p>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <p>0</p>
      </td>
      <td>
        <p>id</p>
      </td>
      <td>
        <p>string containing integer</p>
      </td>
      <td>
        <p class="NormalWeb">ID of the deny log entry</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>1</p>
      </td>
      <td>
        <p>time</p>
      </td>
      <td>
        <p>string containing integer</p>
      </td>
      <td>
        <p class="NormalWeb">Timestamp of the denied request</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>2</p>
      </td>
      <td>
        <p>source</p>
      </td>
      <td>
        <p>string containing integer</p>
      </td>
      <td>
        <p>The source IP address represented as an integer</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>3</p>
      </td>
      <td>
        <p>host</p>
      </td>
      <td>
        <p>string containing hostname/IP address</p>
      </td>
      <td>
        <p>The target host of the denied request</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>4</p>
      </td>
      <td>
        <p>path</p>
      </td>
      <td>
        <p>string containing URL path</p>
      </td>
      <td>
        <p>The target path of the denied request</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>5</p>
      </td>
      <td>
        <p>violation_id</p>
      </td>
      <td>
        <p>string containing integer</p>
      </td>
      <td>
        <p>ID of the violation that occurred</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>6</p>
      </td>
      <td>
        <p>status</p>
      </td>
      <td>
        <p>string containing integer</p>
      </td>
      <td>
        <p class="NormalWeb">Indicates whether the deny entry has been added to the ACL</p>
        <p class="NormalWeb">"0" → has not been added to ACL<br />"1" → has been added to ACL</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>7</p>
      </td>
      <td>
        <p>attack_class_id</p>
      </td>
      <td>
        <p>string containing integer</p>
      </td>
      <td>
        <p class="NormalWeb">ID of the attack class</p>
        <p class="NormalWeb">"1" → SQL injection<br />"2" → XPath injection<br />"3" → SSI injection<br />"4" → OS commanding<br />"5" → XSS<br />"6" → Path traversal<br />"7" → Enumeration<br />"8" → Format string<br />"9" → Buffer overflow<br />"10" → DoS attempt<br />"11" → Worm probe<br />"12" → Access violation<br />"13" → Malformed request<br />"14" → HTML tags<br />"15" → Session invalid<br />"16" → XSRF<br />"17" → Session expired<br />"18" → Detection evasion<br />"19" → File inclusion<br />"20" → CRLF injection<br />"21" → HTTP request smuggling<br />"22" → XQuery injection<br />"23" → LDAP injection<br />"24" → XML injection<br />"25" → Null byte injection<br />"35" → Information leak<br />"50" → Backend error<br />"51" → Broken robot<br />"52" → Broken int. link<br />"53" → Broken ext. link<br />"54" → Other<br />"60" → None<br />"70" → False positive<br />"99" → Friendly</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>8</p>
      </td>
      <td>
        <p>resp_status</p>
      </td>
      <td>
        <p>string containing integer</p>
      </td>
      <td>
        <p class="NormalWeb">HTTP status code returned by the response</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>9</p>
      </td>
      <td>
        <p>resp_time</p>
      </td>
      <td>
        <p>string containing integer</p>
      </td>
      <td>
        <p class="NormalWeb">The time from when the WSM received the request and forwarded it to the backend server until the response is sent to the client from WSM</p>
        <p class="NormalWeb">Measured in milliseconds</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>10</p>
      </td>
      <td>
        <p>backend_host</p>
      </td>
      <td>
        <p>string containing integer</p>
      </td>
      <td>
        <p>Indicates which backend host received the request (0 for 1st host, 1 for 2nd, etc)</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>11</p>
      </td>
      <td>
        <p>action</p>
      </td>
      <td>
        <p>string containing integer</p>
      </td>
      <td>
        <p class="NormalWeb">Action applied to the request</p>
        <p class="NormalWeb">"-1" → Block IP<br />"0" → Block<br />"1" → Strip<br />"2" → Allow</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>12</p>
      </td>
      <td>
        <p>risk</p>
      </td>
      <td>
        <p>string containing integer</p>
      </td>
      <td>
        <p class="NormalWeb">Indicates risk level associated with the deny entry</p>
        <p class="NormalWeb">"1" → Critical<br />"2" → High<br />"3" → Medium<br />"4" → Low<br />"5" → None</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>13</p>
      </td>
      <td>
        <p>ccode</p>
      </td>
      <td>
        <p>string containing country code</p>
      </td>
      <td>
        <p>Country code for origin of the denied request</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>14</p>
      </td>
      <td>
        <p>proto</p>
      </td>
      <td>
        <p>string containing integer</p>
      </td>
      <td>
        <p class="NormalWeb">Protocol of the request</p>
        <p class="NormalWeb">"1" → http<br />"2" → https</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>15</p>
      </td>
      <td>
        <p>normality_score</p>
      </td>
      <td>
        <p>string containing integer</p>
      </td>
      <td>
        <p class="NormalWeb">Expresses the normality in parts per million</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>16</p>
      </td>
      <td>
        <p>normality_flag</p>
      </td>
      <td>
        <p>string containing integer</p>
      </td>
      <td>
        <p class="NormalWeb">Indicates the normality of the denied request</p>
        <p class="NormalWeb">"0" → Normal<br />less than "0" → Abnormal </p>
      </td>
    </tr>
    <tr>
      <td>
        <p>17</p>
      </td>
      <td>
        <p>compromise_score</p>
      </td>
      <td>
        <p>string containing integer</p>
      </td>
      <td>
        <p class="NormalWeb">Expresses the fidelity of the compromise observation</p>
      </td>
    </tr>
  </tbody>
</table>### Example: Get available websites

#### Request

<span class="get">GET</span><p class="method">
  <kbd>/api/v1/website/1/denylog</kbd>
</p>

<span class="get">cURL</span><p class="method">
  <kbd>curl -kv					<br />-u api_ninja:ninja_password					<br />-X GET				<br />https://172.31.1.172:4849/api/v1/website/1/denylog</kbd>
</p>

#### Response

[
    [
        "10000",
        "1477424180",
        "30348151",
        "www.example.com",
        "/a/path",
        "5",
        "0",
        "99",
        "200",
        "285",
        "0",
        "0",
        "0",
        "CN",
        "1",
        "0",
        "0",
        "0"
    ],
    [
        "9999",
        "1477424180",
        "18663245",
        "www.anotherexample.com",
        "/another/path",
        "8",
        "0",
        "99",
        "200",
        "285",
        "0",
        "0",
        "0",
        "CN",
        "1",
        "0",
        "0",
        "0"
    ]
]
