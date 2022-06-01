## About the Web Security Manager API

<p>The Alert Logic <MadCap:variable name="ALVariables.WSM_OutBndWaf_2" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> (WSM) REST API provides query and configuration functionality for Web Security Manager appliances.</p>

### Appliance

<table style="width: 100%;" cellspacing="0">
  <col style="width: 65px;" />
  <col style="width: 250px;" />
  <col />
  <thead>
    <tr>
      <th MadCap:conditions="Primary.Draft Content" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd">Method</th>
      <th MadCap:conditions="Primary.Draft Content" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd">Resource</th>
      <th MadCap:conditions="Primary.Draft Content" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd">Description  </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td MadCap:conditions="Primary.Draft Content" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd">POST</td>
      <td MadCap:conditions="Primary.Draft Content" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd">/api/v1/appliance</td>
      <td MadCap:conditions="Primary.Draft Content" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd">Provisions a WSM, and optionally can add a new API user.<![CDATA[
]]></td>
    </tr>
    <tr>
      <td MadCap:conditions="Primary.Draft Content" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd">POST</td>
      <td MadCap:conditions="Primary.Draft Content" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd">/api/v1/appliance</td>
      <td MadCap:conditions="Primary.Draft Content" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd">Sets configuration for proxy settings synchronization.<![CDATA[
]]></td>
    </tr>
    <tr>
      <td MadCap:conditions="Primary.Draft Content" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd">GET</td>
      <td MadCap:conditions="Primary.Draft Content" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd">/api/v1/appliance</td>
      <td MadCap:conditions="Primary.Draft Content" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd">Obtains synchronization configuration.</td>
    </tr>
  </tbody>
</table>### Websites

<table style="width: 100%;" cellspacing="0">
  <col style="width: 65px;" />
  <col style="width: 250px;" />
  <col />
  <thead>
    <tr>
      <th MadCap:conditions="Primary.Draft Content" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd">Method</th>
      <th MadCap:conditions="Primary.Draft Content" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd">Resource</th>
      <th MadCap:conditions="Primary.Draft Content" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd">Description  </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td MadCap:conditions="Primary.Draft Content" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd">POST</td>
      <td MadCap:conditions="Primary.Draft Content" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd">/api/v1/website</td>
      <td MadCap:conditions="Primary.Draft Content" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd">Adds a website for WSM to monitor/protect.</td>
    </tr>
    <tr>
      <td MadCap:conditions="Primary.Draft Content" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd">GET</td>
      <td MadCap:conditions="Primary.Draft Content" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd">/api/v1/website</td>
      <td MadCap:conditions="Primary.Draft Content" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd">Obtains list of available website IDs.</td>
    </tr>
    <tr>
      <td MadCap:conditions="Primary.Draft Content" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd">GET</td>
      <td MadCap:conditions="Primary.Draft Content" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd">/api/v1/website/[website_id]</td>
      <td MadCap:conditions="Primary.Draft Content" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd">Obtains configuration details for a given website.</td>
    </tr>
    <tr>
      <td MadCap:conditions="Primary.Draft Content" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd">GET</td>
      <td MadCap:conditions="Primary.Draft Content" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd">/api/v1/website/[website_id]/denylog</td>
      <td MadCap:conditions="Primary.Draft Content" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd">Returns denylog entries for a given website.</td>
    </tr>
    <tr>
      <td MadCap:conditions="Primary.Draft Content" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd">GET</td>
      <td MadCap:conditions="Primary.Draft Content" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd">/api/v1/website/[website_id]/test</td>
      <td MadCap:conditions="Primary.Draft Content" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd">Tests connectivity to a website by issuing a HEAD request.</td>
    </tr>
    <tr>
      <td MadCap:conditions="Primary.Draft Content" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd">PUT</td>
      <td MadCap:conditions="Primary.Draft Content" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd">/api/v1/website/[website_id]</td>
      <td MadCap:conditions="Primary.Draft Content" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd">Changes the proxy mode of a website.</td>
    </tr>
    <tr>
      <td MadCap:conditions="Primary.Draft Content" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd">PUT</td>
      <td MadCap:conditions="Primary.Draft Content" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd">/api/v1/website/[website_id]</td>
      <td MadCap:conditions="Primary.Draft Content" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd">Updates the SSL certificate for a website.</td>
    </tr>
    <tr>
      <td MadCap:conditions="Primary.Draft Content" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd">PUT</td>
      <td MadCap:conditions="Primary.Draft Content" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd">/api/v1/website/[website_id]</td>
      <td MadCap:conditions="Primary.Draft Content" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd">Imports a proxy template for a website.</td>
    </tr>
    <tr>
      <td MadCap:conditions="Primary.Draft Content" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd">DELETE</td>
      <td MadCap:conditions="Primary.Draft Content" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd">/api/v1/website/[website_id]</td>
      <td MadCap:conditions="Primary.Draft Content" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd">Deletes a website.</td>
    </tr>
  </tbody>
</table>### Interfaces

<table style="width: 100%;" cellspacing="0">
  <col style="width: 65px;" />
  <col style="width: 250px;" />
  <col />
  <thead>
    <tr>
      <th MadCap:conditions="Primary.Draft Content" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd">Method</th>
      <th MadCap:conditions="Primary.Draft Content" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd">Resource</th>
      <th MadCap:conditions="Primary.Draft Content" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd">Description  </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td MadCap:conditions="Primary.Draft Content" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd">GET</td>
      <td MadCap:conditions="Primary.Draft Content" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd">/api/v1/interface/physical</td>
      <td MadCap:conditions="Primary.Draft Content" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd">Obtains list of physical network interfaces.</td>
    </tr>
    <tr>
      <td MadCap:conditions="Primary.Draft Content" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd">GET</td>
      <td MadCap:conditions="Primary.Draft Content" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd">/api/v1/interface/virtual</td>
      <td MadCap:conditions="Primary.Draft Content" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd">Obtains list of VRRP interfaces.</td>
    </tr>
    <tr>
      <td MadCap:conditions="Primary.Draft Content" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd">POST</td>
      <td MadCap:conditions="Primary.Draft Content" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd">/api/v1/interface</td>
      <td MadCap:conditions="Primary.Draft Content" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd">Adds a VRRP interface.</td>
    </tr>
    <tr>
      <td MadCap:conditions="Primary.Draft Content" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd">DELETE</td>
      <td MadCap:conditions="Primary.Draft Content" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd">/api/v1/interface/virtual/[id]<br />/api/v1/interface/virtual/[id]/force</td>
      <td MadCap:conditions="Primary.Draft Content" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd">Deletes a VRRP interface.</td>
    </tr>
  </tbody>
</table>
