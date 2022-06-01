## How to implement

<p>In order to use the <MadCap:variable name="ALVariables.WSM_OutBndWaf_2" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> (WSM) REST API, an API user must be created <MadCap:annotation MadCap:createDate="2016-12-09T10:05:20.5135693-06:00" MadCap:creator="cmimoso" MadCap:initials="CM" MadCap:comment="does this mean in the wsm application or wsm appliance?" MadCap:editor="cmimoso" MadCap:editDate="2016-12-09T10:05:32.1840671-06:00" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd">on the WSM</MadCap:annotation>. This user can be created through the REST API itself, the WSM Management UI, or an Amazon CloudFormation template.</p>

### Create an API user via the WSM REST API

An API user can be created during the provisioning process using the WSM REST API. The provisioning API call is the only one which does not require API user credentials, so an API username and password can be supplied along with the WSM license key. See Provision an Appliance for an example.

### Create an API user via the WSM UI

After the WSM appliance has been provisioned, log into the Management UI. Then use the navigation bar on the left to go to the System > Users page. At the bottom of this page are the WSM System Users.

<p>
  <MadCap:annotation MadCap:createDate="2016-12-09T10:10:26.4505037-06:00" MadCap:creator="cmimoso" MadCap:initials="CM" MadCap:comment="create an actual procedure from this..." MadCap:editor="cmimoso" MadCap:editDate="2016-12-09T10:11:39.8211659-06:00" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd">To </MadCap:annotation>create the API user, enter a username, password, and select 'API' from the Type dropdown menu. Click 'Save Changes' and your new API user will be ready for use.</p>

### Create an API user via a CloudFormation template

CloudFormation templates for autoscaling WSM appliances can be modified to automatically create an API user upon spinning up the stack. To do so, find the "UserData" block in the template under "Resources" > "lcMaster" > "UserData":

"UserData": {
    "Fn::Base64": {
        "Fn::Join": ["", ["{\"alertlogic\": {\"wsm\": {\"role\" : \"master\", \"license\" : \"", {
                    "Ref": "wsmLicense"
                }, "\", \"user\" : \"", {
                    "Ref": "wsmUser"
                }, "\", \"password\" : \"", {
                    "Ref": "wsmPassword"
                }, "\", \"S3BucketName\" : \"", {
                    "Ref": "s3Bucket"
                }, "\", \"EbsLogVolume\" : \"", {
                    "Ref": "volumeLog"
                }, "\", \"MasterElbDnsName\" : \"", {
                    "Fn::GetAtt": ["elbMaster" , "DNSName"]
                }, "\", \"WorkerElbDnsName\" : \"", {
                    "Fn::GetAtt": ["elbWorker" , "DNSName"]
                }, "\", \"BackendElbDnsName\" : \"", {
                    "Ref": "elbBackend"
                }, "\"}}}"
            ]
        ]
    }
}
Next, define the API user's username and password within the Fn::Join function as follows:

"UserData": {
    "Fn::Base64": {
        "Fn::Join": ["", ["{\"alertlogic\": {\"wsm\": {\"role\" : \"master\", \"api_user\" : \"api_ninja\", \"api_password\" : \"ninja_password\", \"license\" : \"", {
                    "Ref": "wsmLicense"
                }, "\", \"user\" : \"", {
                    "Ref": "wsmUser"
                }, "\", \"password\" : \"", {
                    "Ref": "wsmPassword"
                }, "\", \"S3BucketName\" : \"", {
                    "Ref": "s3Bucket"
                }, "\", \"EbsLogVolume\" : \"", {
                    "Ref": "volumeLog"
                }, "\", \"MasterElbDnsName\" : \"", {
                    "Fn::GetAtt": ["elbMaster" , "DNSName"]
                }, "\", \"WorkerElbDnsName\" : \"", {
                    "Fn::GetAtt": ["elbWorker" , "DNSName"]
                }, "\", \"BackendElbDnsName\" : \"", {
                    "Ref": "elbBackend"
                }, "\"}}}"
            ]
        ]
    }
}
The API user will now be automatically created when using this CloudFormation template.

<table style="width: 100%;" cellspacing="0">
  <col style="width: 125px;"></col>
  <col style="width: 110px;"></col>
  <col></col>
  <thead>
    <tr>
      <th>Base Path</th>
      <th>HTTP Method</th>
      <th>Links</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td rowspan="4">/website/</td>
      <td>GET</td>
      <td>Get Available Websites<br />Get Website Details<br />Get Website Denylog<br />Test Connectivity of a Website</td>
    </tr>
    <tr>
      <td>POST</td>
      <td>Add a Website</td>
    </tr>
    <tr>
      <td>PUT</td>
      <td>Change Website's Proxy Mode<br />Update a Website's SSL Certificate<br />Import a Proxy Template for a Website</td>
    </tr>
    <tr>
      <td>DELETE</td>
      <td>Delete a Website</td>
    </tr>
    <tr>
      <td rowspan="2">/appliance/</td>
      <td>POST</td>
      <td>Provision an Appliance <br />Set Synchronization Configuration </td>
    </tr>
    <tr>
      <td>GET</td>
      <td>Get Synchronization Configuration</td>
    </tr>
    <tr>
      <td rowspan="3">/interface/</td>
      <td>POST</td>
      <td>Add VRRP Interface</td>
    </tr>
    <tr>
      <td>GET</td>
      <td>Get VRRP Interfaces <br />Get Interfaces</td>
    </tr>
    <tr>
      <td>DELETE</td>
      <td>Delete VRRP Interface</td>
    </tr>
  </tbody>
</table>
