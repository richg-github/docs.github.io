```

$ alcli assets_query query_assets --account_id 134278880 --asset_types agent,host --filter '{"agent.status": "!!ok"}' --return_types host --qfields name,key,private_ipv4_addresses
{
	"assets": [
		[
			{
				"deployment_id": "9A4A67CF-C2FC-404C-BFC8-FFE78DAC0154",
				"key": "/dc/host/DEADBEEF-7C2F-49AE-8234-DEADBEEF272F",
				"name": "my-host-with-agent-installed",
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
      <td>the asset types to query for; in this case, we are querying for ‘agent’, which has information about the agent status, and for ‘host’, which has identifying information about the host (e.g. name and IP addresses)</td>
    </tr>
    <tr>
      <td>
        <kbd>--filter</kbd>
      </td>
      <td>
        <p>a JSON object representing property names and values to filter with.</p>
        <p>
          <kbd>{"agent.status": "!!ok"}</kbd> means "match any agent where the status is not <kbd>ok</kbd> or is <kbd>null</kbd> [i.e. status has not yet been reported]". </p>
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
· --filter - a JSON object representing property names and values to filter with. {"agent.status": "!!ok"} means "match any agent where the status is not ok or is null [i.e. status has not yet been reported]".

· --return_types - the asset types to be retrieved from the Assets model: by default, this will match the asset types provided to --asset_types, but it is often a good idea to limit the returned assets to the ones that are of interest

· --qfields - the properties to return in the response. As with --return_types it is often a good idea to restrict the returned data to what is of interest, but this is not required

You can also use the --query parameter to alcli to transform the response into a single list of asset objects:

```

$ alcli --query 'assets[][]' assets_query query_assets --account_id 134278880 --asset_types agent,host --filter '{"agent.status": "!!ok"}' --return_types host --qfields name,key,private_ipv4_addresses
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
