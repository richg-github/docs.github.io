Update a protected host

Threat Manager allows you to update your protected hosts.

To update a protected host:

<ol style="list-style-type: decimal;margin-left: 0pt;" start="1">
  <li>At the top of the Alert Logic user interface (UI), from the drop-down menu, select Threat Manager.</li>
  <li>In the left navigation pane, under Detection, click Protected Hosts.</li>
  <li>In the table of protected hosts, select the protected host you want to update, and then click the pencil icon ( <img src="../../../../../../Documents/My Projects/infodev/oneOffs/wordImportMain/Content/Resources/Images/addVRRPinterface/Update a protected host.png" style="width: 30px;height: 30px;" /> ).</li>
  <li>Fill in the form and click Update. See the table below for field definitions.</li>
</ol>

Update a protected host form

<table>
  <thead>
    <tr>
      <th>
        <p>Field/Option</p>
      </th>
      <th>
        <p>Description</p>
      </th>
      <th>
        <p>Sample Value</p>
      </th>
      <th>
        <p>Visible</p>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <p>Source Name</p>
      </td>
      <td>
        <p>Name of this source. It will show on the display list and other areas of this product.</p>
      </td>
      <td>
        <p>server-tmdocs</p>
      </td>
      <td>
        <p>always</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>Use an existing Assignment Policy</p>
      </td>
      <td>
        <p>Select this option to choose a policy from the Existing Assignment Policy list.</p>
      </td>
      <td>
        <p>na</p>
      </td>
      <td>
        <p>always</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>Create a new assignment policy</p>
      </td>
      <td>
        <p>Select this option to open the Create a new assignment policy section.</p>
      </td>
      <td>
        <p>na</p>
      </td>
      <td>
        <p>always</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>Existing Assignment Policy list</p>
      </td>
      <td>
        <p>select a policy from this list to assign it to the protected host.</p>
      </td>
      <td>
        <p>cali-ngtm-01 Assignment</p>
      </td>
      <td>
        <p>visible when Use an existing Assignment Policy is selected</p>
      </td>
    </tr>
    <tr>
      <td colspan="4">
        <p>Create new Assignment Policy mini-form</p>
        <p>visible when you select Create new Assignment Policy</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>Field/Option</p>
      </td>
      <td>
        <p>Description</p>
      </td>
      <td>
        <p>Sample Value</p>
      </td>
      <td>
        <p>Visible</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>Appliance Assignment Policy Name</p>
      </td>
      <td>
        <p>Policy name. This name will be added to the Existing Assignment Policy list.</p>
      </td>
      <td>
        <p>cali-ngtm-01 Assignment</p>
      </td>
      <td>
        <p>visible when Create a new assignment policy is selected.</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>Appliances</p>
      </td>
      <td>
        <p>An appliance on your network.</p>
      </td>
      <td>
        <p>i-27273bcb</p>
      </td>
      <td>
        <p>visible when Create a new assignment policy is selected.</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>Restrict Network</p>
      </td>
      <td>
        <p>???</p>
      </td>
      <td>
        <p> </p>
      </td>
      <td>
        <p> </p>
      </td>
    </tr>
    <tr>
      <td>
        <p>Netmask</p>
      </td>
      <td>
        <p>One CIDR address.</p>
      </td>
      <td>
        <p>10.0.0.0/16; partial address specifications are not acceptable.</p>
      </td>
      <td>
        <p>visible when Create a new assignment policy is selected.</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>Use existing Whitelist Policies</p>
      </td>
      <td>
        <p>Select this option to choose a policy from the Existing Whitelist Policy list.</p>
      </td>
      <td>
        <p>na</p>
      </td>
      <td>
        <p>visible when Create a new assignment policy is selected.</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>Create a new Whitelist Policy</p>
      </td>
      <td>
        <p>Select this option to open the Create a new Whitelist Policy section.</p>
      </td>
      <td>
        <p>na</p>
      </td>
      <td>
        <p>visible when Create a new assignment policy is selected.</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>Existing Whitelist Policy list</p>
      </td>
      <td>
        <p>select a policy from this list to assign it to the protected host.</p>
      </td>
      <td>
        <p> SF01183529 Pentest</p>
      </td>
      <td>
        <p>visible when Create a new assignment policy and Use existing Whitelist Policies is selected.</p>
      </td>
    </tr>
    <tr>
      <td colspan="4">
        <p>Create new Whitelist Policy mini-form</p>
        <p>visible when you select Create new Assignment Policy and Create a new Whitelist Policy.</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>Field/Option</p>
      </td>
      <td>
        <p>Description</p>
      </td>
      <td>
        <p>Sample Value</p>
      </td>
      <td>
        <p>Visible</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>Name</p>
      </td>
      <td>
        <p>Policy name. This name will be added to the Existing Whitelist Policy list.</p>
      </td>
      <td>
        <p> SF01183529 Pentest</p>
      </td>
      <td>
        <p>visible when you select Create new Assignment Policyand Create a new Whitelist Policy.</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>Enabled</p>
      </td>
      <td>
        <p>Select this option to activate the policy.</p>
      </td>
      <td>
        <p>na</p>
      </td>
      <td>
        <p>visible when you select Create new Assignment Policyand Create a new Whitelist Policy.</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>Rules</p>
      </td>
      <td>
        <p>Click <img src="../../../../../../Documents/My Projects/infodev/oneOffs/wordImportMain/Content/Resources/Images/addVRRPinterface/Update a protected host_1.png" style="width: 23px;height: 22px;" /> to add rules to the Whitelist Policy. This includes: Protocol, CIDR, and Port.</p>
      </td>
      <td>
        <p>na</p>
      </td>
      <td>
        <p>visible when you select Create new Assignment Policyand Create a new Whitelist Policy.</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>Protocol</p>
      </td>
      <td>
        <p>Select the internet protocol for the current rule.</p>
      </td>
      <td>
        <p>tcp</p>
      </td>
      <td>
        <p>visible when you select Create new Assignment Policyand Create a new Whitelist Policy.</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CIDR</p>
      </td>
      <td>
        <p>Type the Classless Inter-Domain Routing address for the current rule.</p>
      </td>
      <td>
        <p>10.0.0.0/16</p>
      </td>
      <td>
        <p>visible when you select Create new Assignment Policyand Create a new Whitelist Policy.</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>Port</p>
      </td>
      <td>
        <p>Type the port for the current rule.</p>
      </td>
      <td>
        <p>22</p>
      </td>
      <td>
        <p>visible when you select Create new Assignment Policyand Create a new Whitelist Policy.</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>Field/Option</p>
      </td>
      <td>
        <p>Description</p>
      </td>
      <td>
        <p>Sample Value</p>
      </td>
      <td>
        <p>Visible</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>Use existing Host Policies</p>
      </td>
      <td>
        <p>Select this option to choose a policy from the Existing Host Policy list.</p>
      </td>
      <td>
        <p>na</p>
      </td>
      <td>
        <p>always</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>Create new Host Policy</p>
      </td>
      <td>
        <p>Select this option to open the Create a new Host Policy section.</p>
      </td>
      <td>
        <p>na</p>
      </td>
      <td>
        <p>always</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>Existing Host Policy list</p>
      </td>
      <td>
        <p>select a policy from this list to assign it to the protected host.</p>
      </td>
      <td>
        <p>Default-test</p>
      </td>
      <td>
        <p>visible when Use existing Host Policies is selected.</p>
      </td>
    </tr>
    <tr>
      <td colspan="4">
        <p>Create new Host Policy mini-form</p>
        <p>visible when you select Create new Host Policy.</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>Field/Option</p>
      </td>
      <td>
        <p>Description</p>
      </td>
      <td>
        <p>Sample Value</p>
      </td>
      <td>
        <p>Visible</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>Name</p>
      </td>
      <td>
        <p>Policy name. This name will be added to the Existing Host Policy list.</p>
      </td>
      <td>
        <p>Default-test</p>
      </td>
      <td>
        <p>visible when you select Create new Host Policy.</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>Encrypt</p>
      </td>
      <td>
        <p>???</p>
      </td>
      <td>
        <p>na</p>
      </td>
      <td>
        <p>visible when you select Create new Host Policy.</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>Tags</p>
      </td>
      <td>
        <p>A tag is a customer defined identifier that can be assigned to one or more sources. A customer can use tags to organize or search for specific types of sources.</p>
      </td>
      <td>
        <p>High usage</p>
      </td>
      <td>
        <p>always</p>
      </td>
    </tr>
  </tbody>
</table>
