<h1>Download Current Health Check Results for your <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> Security Infrastructure</h1><p>This section describes how to retrieve a summary of health check results for your <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> security infrastructure using the <MadCap:variable name="SDKVariables.CLI" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />.</p>

<MadCap:snippetBlock src="../Resources/Snippets/sub-typess-ess-pro.flsnp" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /><MadCap:snippetBlock src="../Resources/Snippets/req-cli-installed.flsnp" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />## Technical Details

<p>
  <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> reports configuration remediations against a deployment’s assets when the existing configuration affects collection health; these can include (but are not limited to) remediations about agent error states, appliance connectivity, and cross-network protection.</p>

<p>The <MadCap:variable name="SDKVariables.CLI" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> can be used to retrieve a summary of collection health, with the report providing counts of healthy and unhealthy instances for each asset type (agent, appliance, network, and collector), as well as collecting a list of current exposures affecting deployment health.</p>

<h2>Download a collection health summary using the <MadCap:variable name="SDKVariables.CLI" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /></h2><p>This section describes how to download a summary of collection health using the <MadCap:variable name="SDKVariables.CLI" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />.</p>

<p>Use the <MadCap:variable name="SDKVariables.CLI" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> to retrieve a collection health summary from Assets Query, providing the <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> account ID:</p>

```

$ alcli remediations get_collection_health_summary --account_id 134235891
{
	"agents": {
		"coverage": {
			"protected": 0,
			"total": 0
		},
		"health": {
			"scores": [
				{
					"count": 0,
					"health_level": 0,
					"unhealthiness": 0.0
				},
				{
					"count": 0,
					"health_level": 2,
					"unhealthiness": 0.0
				}
			]
		}
	},
	"appliances": {
		"coverage": {
				"total": 0
			},
			"health": {
				"scores": [
					{
						"count": 0,
						"health_level": 0,
						"unhealthiness": 0.0
					},
					{
						"count": 0,
						"health_level": 2,
						"unhealthiness": 0.0
					}
				]
			}
		},
		"collectors": {
			"coverage": {
			"total": 28
		},
		"health": {
			"scores": [
				{
					"count": 5,
					"health_level": 0,
					"unhealthiness": 0.0
				},
				{
					"count": 23,
					"health_level": 2,
					"unhealthiness": 8.0
				}
			]
		}
	},
	"networks": {
		"coverage": {
			"protected": 0,
			"total": 152
		},
		"health": {
			"scores": [
				{
					"count": 0,
					"health_level": 0,
					"unhealthiness": 0.0
				},
				{
					"count": 0,
					"health_level": 2,
					"unhealthiness": 0.0
				}
			]
		}
	}
}
```

You can also use the --query parameter to limit the scope of the results. For example, to fetch a summary only for appliances and agents, use:

```

$ alcli --query '{agents:agents,appliances:appliances}' remediations get_collection_health_summary --account_id 134235891
{
	"agents": {
		"coverage": {
			"protected": 0,
			"total": 4
		},
		"health": {
			"scores": [
				{
					"count": 0,
					"health_level": 0,
					"unhealthiness": 0.0
				},
				{
					"count": 0,
					"health_level": 2,
					"unhealthiness": 0.0
				}
			]
		}
	},
	"appliances": {
		"coverage": {
			"total": 0
		},
		"health": {
			"scores": [
				{
					"count": 0,
					"health_level": 0,
					"unhealthiness": 0.0
				},
				{
					"count": 0,
					"health_level": 2,
					"unhealthiness": 0.0
				}
			]
		}
	}
}
```

<h2>Download current health check results using the <MadCap:variable name="SDKVariables.CLI" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /></h2><p>You can use the <MadCap:variable name="SDKVariables.CLI" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> to retrieve a list of current exposures affecting deployment health. These vulnerabilities are stored in Assets, and retrieved with Assets Query.</p>

<p>Use the <MadCap:variable name="SDKVariables.CLI" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> to download a list of open configuration vulnerabilities along with their associated remediations:</p>

```

$ alcli assets_query query_assets --account_id 134278880 --asset_types 'vulnerability,remediation' --filter '{"vulnerability.categories", ">>configuration"}' --qfields 'name,description,details,remediation_id,vulnerability_id'
{
	"rows": 1,
	"assets": [
		[
			{
				"vulnerability_id": "5fe231de3e31ac7064df974341cb6efc",
				"type": "vulnerability",
				"remediation_id": "ids_missing_appliance_dc",
				"name": "Network Without Alert Logic Appliance",
				"key": "/dc/network/B0A11702-20CA-4948-B4AA-FB9926A290AD/vulnerability/f126e4d15ffb769547bcd26efe8ac785",
				"details": "The network does not have a provisioned IDS appliance present.",
				"description": "Network Without Alert Logic Appliance",
				"deployment_id": "C6189132-5282-4A2D-B915-737862AB05AE",
				"categories": [
					"configuration"
				]
			},
			{
				"type": "remediation",
				"remediation_id": "ids_missing_appliance_dc",
				"name": "Alert Logic recommends that you add an Alert Logic Appliance to this Network.",
				"key": "/al/134278880:C6189132-5282-4A2D-B915-737862AB05AE/remediation/ids_missing_appliance_dc",
				"deployment_id": "C6189132-5282-4A2D-B915-737862AB05AE"
			}
		]
	]
}
```

Note that this request downloads all configuration remediations for the entire account; it is also possible to limit the results to a given deployment using the --deployment_id parameter.

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
      <td> the asset types to query for; in this case, we are querying for vulnerabilities and their associated remediations.</td>
    </tr>
    <tr>
      <td>
        <kbd>--filter</kbd>
      </td>
      <td>
        <p>a JSON object representing property names and values to filter with. <kbd>{"vulnerability.categories": "&amp;gt;&amp;gt;configuration"}</kbd> uses the list membership operator <kbd>&amp;gt;&amp;gt;</kbd> to query for vulnerabilities belonging to the configuration category.</p>
      </td>
    </tr>
    <tr>
      <td>
        <kbd>--qfields</kbd>
      </td>
      <td>
        <p> the properties to return in the response. It is often a good idea (and convenient) to restrict the returned data to what is of interest, but this is not required</p>
      </td>
    </tr>
  </tbody>
</table><h2 MadCap:conditions="Primary.Draft Content" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd">See <MadCap:annotation MadCap:createDate="2021-04-08T10:09:18.3392752-05:00" MadCap:creator="bob.baskin" MadCap:initials="BO" MadCap:comment="Not sure why this topic, alone, has this section." MadCap:editor="bob.baskin" MadCap:editDate="2021-04-08T10:09:26.0998438-05:00">also</MadCap:annotation></h2><ul>
  <li MadCap:conditions="Primary.Draft Content" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd">Download a list of appliances having problems communicating with <MadCap:variable name="SDKVariables.Company" /></li>
  <li MadCap:conditions="Primary.Draft Content" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd">Download a list of agents having problems communicating with <MadCap:variable name="SDKVariables.Company" /></li>
  <li MadCap:conditions="Primary.Draft Content" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd">Download a list of configured AWS or Azure deployments that <MadCap:variable name="SDKVariables.Company" /> cannot access</li>
</ul>
