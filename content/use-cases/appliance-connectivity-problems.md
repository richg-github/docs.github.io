```

$ alcli assets_query query_assets --account_id 134278880 --asset_types appliance,host --filter '{"appliance.status": "!!ok", "host.alertlogic_appliance_features": ">>ids"}' --return_types host --qfields name,key,private_ipv4_addresses
{
	"assets": [
		[
			{
				"deployment_id": "9A4A67CF-C2FC-404C-BFC8-FFE78DAC0154",
				"key": "/dc/host/DEADBEEF-7C2F-49AE-8234-DEADBEEF272F",
				"name": "my-appliance",
				"private_ipv4_addresses": [
					"10.10.214.224"
				],
				"type": "host"
			}
		]
	],
	"rows": 1
}
```

Here is a breakdown of this query:

<table style="width: 100%;">
  <col />
  <col />
  <tbody>
    <tr>
      <th>Parameter</th>
      <th>Definition</th>
    </tr>
    <tr>
      <td>
        <kbd>--account_id</kbd>
      </td>
      <td>your <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> account ID</td>
    </tr>
    <tr>
      <td>
        <kbd>--asset_types</kbd>
      </td>
      <td>the asset types to query for; in this case, we are querying for ‘appliance’, which has information about the appliance status, and for ‘host’, which has identifying information about the host (e.g. name and IP addresses)</td>
    </tr>
    <tr>
      <td>
        <kbd>--filter</kbd>
      </td>
      <td>
        <p>a JSON object representing property names and values to filter with.</p>
        <p>
          <kbd>{"appliance.status": "!!ok"}</kbd> means "match any appliance where the status is not <kbd>ok</kbd> or is <kbd>null</kbd> [i.e. status has not yet been reported]". </p>
        <p>
          <kbd>&amp;gt;&amp;gt;</kbd> is the list membership operator, so <kbd>{"host.alertlogic_appliance_features": "&amp;gt;&amp;gt;ids"}</kbd> matches any host with ids in its feature list.</p>
      </td>
    </tr>
    <tr>
      <td>
        <kbd>--return_types</kbd>
      </td>
      <td>the asset types to be retrieved from the Assets model: by default, this will match the asset types provided to <kbd>--asset_types</kbd>, but you should limit the returned assets to the ones that are of interest.</td>
    </tr>
    <tr>
      <td>
        <kbd>--qfields</kbd>
      </td>
      <td>the properties to return in the response. As with <kbd>--return_types</kbd>, you should restrict the returned data to what is of interest, but this is not required.                    </td>
    </tr>
  </tbody>
</table>
You may also use the <kbd>--query</kbd> parameter to <kbd>alcli</kbd> to transform the response into a single list of asset objects:

```

$ alcli --query 'assets[][]' assets_query query_assets --account_id 134278880 --asset_types appliance,host --filter '{"appliance.status": "!!ok", "host.alertlogic_appliance_features": ">>ids"}' --return_types host --qfields name,key,private_ipv4_addresses
[
	{
		"deployment_id": "9A4A67CF-C2FC-404C-BFC8-FFE78DAC0154",
		"key": "/dc/host/3E2B1BE4-7C2F-49AE-8234-E8F7DEBE272F",
		"name": "kontsevoy-siemless-test-2",
		"private_ipv4_addresses": [
			"10.10.214.224"
		],
		"type": "host"
	}
]
```
