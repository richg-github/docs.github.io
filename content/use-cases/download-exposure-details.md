# Download Security Exposure Details from Scanning and Cloud Configuration Checks​

This section details how to retrieve a list of security and configuration exposures that are affecting your infrastructure.

<MadCap:snippetBlock src="../Resources/Snippets/sub-types-ess-pro-cd-ci.flsnp" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /><MadCap:snippetBlock src="../Resources/Snippets/req-cli-installed.flsnp" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />## Technical details

<p>Security and configuration vulnerabilities are stored in the Assets database in the <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> platform, in a similar fashion to hosts and VPCs. These assets can be retrieved through the <MadCap:variable name="SDKVariables.CLI" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> via the Assets Query web service.</p>

## Retrieve a list of exposures

The query_assets command can be used to retrieve multiple types of assets and has multiple parameters that can be used to query the Assets database. In the scope of this guide however the parameters we need to retrieve exposures are as follows:

<table style="width: 100%;">
  <col />
  <col />
  <col />
  <tbody>
    <tr>
      <th>Parameter</th>
      <th>Type</th>
      <th>Definition</th>
    </tr>
    <tr>
      <td>
        <kbd>account_id</kbd>
      </td>
      <td>string</td>
      <td>
        <p>  the UUID of the <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> account to retrieve incidents from</p>
      </td>
    </tr>
    <tr>
      <td>
        <kbd>deployment_id </kbd>
      </td>
      <td>string</td>
      <td>the UUID of the <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> deployment to retrieve incidents from</td>
    </tr>
    <tr>
      <td>
        <kbd>asset_types </kbd>
      </td>
      <td>string</td>
      <td>the type of assets to retrieve from the Assets database, in our case we should specify vulnerability</td>
    </tr>
  </tbody>
</table>## Retrieve all exposures for a deployment

The following example retrieves a list of vulnerabilities for account with UUID 123456789, from deployment E539FE1F-C764-401C-9EED-DF7A8034BF65:

```

$ alcli assets_query query_assets --account_id 123456789 --deployment_id deployment_id E539FE1F-C764-401C-9EED-DF7A8034BF65 --asset_types vulnerability
```

Response:

```

[
	“assets”: [
		[
			{
				"account_id": "134235158",
				"categories": [
					"configuration"
				],
				"concluded": false,
				"created_on": 1594237139039,
				"cvss_score": 10.0,
				"cvss_vector": "AV:N/AC:L/Au:N/C:C/I:C/A:C/PL:A/EM:A",
				"declared": true,
				"deployment_id": "E539FE1F-C764-401C-9EED-DF7A8034BF65",
				"description": "Host Not Recently Scanned",
				"details": "The host has never been scanned",
				"key": "/aws/us-east-1/host/i-0da4a0dc2d035f9cd/vulnerability/3a4f13698f3549a398d5103cc94009be",
				"name": "Host Not Recently Scanned",
				"refreshed_on": 1594773316542,
				"remediation_id": "scan_verify_deployment_configuration",
				"severity": "high",
				"tag_keys": {},
				"tags": {},
				"threat_level": 3,
				"threat_score": 10.0,
				"threat_vector": "AV:N/AC:L/Au:N/C:C/I:C/A:C/PL:A/EM:A",
				"threatiness": 8.0,
				"type": "vulnerability",
				"version": 2,
				"vulnerability_id": "349da93195201064062e9fcca3d7af49"
			}
		], ...
	]
	"rows": 8
}
```

## Retrieve all exposures affecting UNIX hosts in a deployment

We can filter the list of exposures to just those that are affecting hosts within our deployment by using the asset_type parameter. By specifying both vulnerability and host assets, only vulnerabilities that have a relationship with a host shall be returned. In addition to this, we may also choose to filter those hosts by their operating system by using the filter parameter:

```

$ alcli assets_query query_assets --account_id 134235158 --deployment_id deployment_id E539FE1F-C764-401C-9EED-DF7A8034BF65 --asset_types host,vulnerability --filter host.scope_agent_os_type=unix
```

Response:

```

[
	“assets”: [
		[
			{
				"account_id": "123456789",
				"alertlogic_agent": true,
				"os_type": "unix",
				"private_dns_name": "ip-10-0-0-201.ec2.internal",
				"private_ip_address": "10.0.0.201",
				"state": "running",
				"tag_keys
				"threat_level": 3,
				"threatiness": 32.1406,
				"total_mem_mb": 985,
				"type": "host",
				...
			},
			{
				"account_id": "123456789",
				"categories": [
					"configuration"
				],
				"concluded": false,
				"created_on": 1594237139039,
				"cvss_score": 10.0,
				"name": "Host Not Recently Scanned",
				"native_type": "vulnerability",
				"remediation_id": "scan_verify_deployment_configuration",
				"scope_joey_categories": [
					"configuration"
				],
				"type": "vulnerability",
				"vulnerability_id": "349da93195201064062e9fcca3d7af49"
			}
		],
		...
	],
	"rows": 3
}
```

Note that this returns both host and vulnerability assets with each row. If you want only the vulnerability asset returned, use the return_type parameter and specify that only vulnerability asset types be returned.
