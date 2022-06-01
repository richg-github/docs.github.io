## Get available websites

Obtains list of available website IDs.

### URL

<p class="method1">/api/v1/website</p>

### HTTP Method

<p class="method1">GET</p>

### URL Parameters

none

<h3>
  <MadCap:annotation MadCap:createDate="2016-11-14T08:11:09.4280617-06:00" MadCap:creator="cmimoso" MadCap:initials="CM" MadCap:comment="not the same as rest of api format - other pages have them in tables" MadCap:editor="cmimoso" MadCap:editDate="2016-11-14T08:12:50.3000887-06:00" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd">Response </MadCap:annotation>Parameters</h3>
Returns an array of website IDs (array of strings containing integers).

### Example: Get available websites

#### Request

<span class="get">GET</span><p class="method">
  <kbd>/api/v1/website</kbd>
</p>

<span class="get">cURL</span><p class="method">
  <kbd>curl -kv             <br />-u api_ninja:ninja_password            <br />-X GET            <br />https://172.31.1.172:4849/api/v1/website</kbd>
</p>

<MadCap:snippetBlock src="../../Resources/Snippets/api/copyPasteApiEx.flsnp" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd"></MadCap:snippetBlock>#### Response

[
    "1",
    "2",
    "3",
    "4",
    "5",
    "6",
    "7"
]
