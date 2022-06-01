# Download a List of Problems for a Group of Hosts​

<p>The <MadCap:variable name="SDKVariables.CLI" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> can be used to retrieve a list of exposures reported against a group of hosts; whether by network, subnet, or deployment (and by extension cloud account).</p>

<MadCap:snippetBlock src="../Resources/Snippets/sub-typess-ess-pro.flsnp" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /><MadCap:snippetBlock src="../Resources/Snippets/req-cli-installed.flsnp" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />## Technical Details

<p>
  <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> reports configuration and security exposures against the assets in a deployment and these exposures are related to the assets they concern in the Assets model.  The <MadCap:variable name="SDKVariables.CLI" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> can utilize these relationships to retrieve exposures for a group of hosts belonging to the same network or to the same deployment (and by extension cloud account).</p>

## Download a list of problems for a group of hosts by cloud account

A cloud account (AWS or Azure) and a deployment have a one-to-one relationship; to retrieve a list of problems for hosts in a given cloud account, restrict the query to the deployment covering that cloud account.

<p>Use the <MadCap:variable name="SDKVariables.CLI" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> to retrieve a list of host vulnerabilities in a given deployment:</p>

```

$ alcli --query 'assets | [:2]' assets_query query_assets --account_id 134235891 --asset_types host,vulnerability --return_types host,vulnerability --filter '{"host.deployment_id": "ABA5D907-1168-417F-B320-2610561677A1"}' --qfields key,name,severity,categories,details,description,cvss_score,private_ipv4_addresses
[
	[
		{
			"deployment_id": "ABA5D907-1168-417F-B320-2610561677A1",
			"key": "/aws/ap-northeast-1/host/i-0d276a2ed22c7f784",
			"name": "az-instance1",
			"private_ipv4_addresses": [
				"10.0.0.38"
			],
			"type": "host"
		},
		{
			"categories": [
				"security"
			],
			"cvss_score": 2.6,
			"deployment_id": "ABA5D907-1168-417F-B320-2610561677A1",
			"description": "Unconfigured EC2 Instance Single-Point-of-Failure and/or Auto Scaling Issue",
			"details": "{standalone_ec2_instance,<<\"/aws/ap-northeast-1/host/i-0d276a2ed22c7f784\">>,\n                         <<\"az-instance1\">>}",
			"key": "/aws/ap-northeast-1/host/i-0d276a2ed22c7f784/vulnerability/faa803430a3b8f888d21f90e5a4fde91",
			"name": "Unconfigured EC2 Instance Single-Point-of-Failure and/or Auto Scaling Issue",
			"severity": "low",
			"type": "vulnerability"
		}
	],
	...
]
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
      <td>the asset types to query for; in this case the asset types of interest are 'vulnerability' and 'host' -- even though only the vulnerabilities are of interest, the host asset type is included here so that only vulnerabilities with relationships to hosts are returned</td>
    </tr>
    <tr>
      <td>
        <kbd>--filter </kbd>
      </td>
      <td>a JSON object representing property names and values to filter with.  Use the 'host.deployment_id' filter to limit the results to those hosts belonging to a given deployment ID.</td>
    </tr>
    <tr>
      <td>
        <kbd>--qfields</kbd>
      </td>
      <td>
        <p> the properties to return in the response. It is often a good idea to restrict the returned data to what is of interest, but this is not required.</p>
      </td>
    </tr>
  </tbody>
</table>## Download a list of problems for a group of hosts by network

To retrieve a list of vulnerabilities for a group of hosts by network, include the <kbd>'network' </kbd>asset type in the command (or <kbd>'vpc'</kbd> -- the former is an alias for the latter).  Filtering can be performed on any of the network asset's properties: for example, filtering by asset key can be achieved with e.g.<kbd> --filter '{"network.key": "/aws/ap-northeast-1/host/i-0d276a2ed22c7f784"}'</kbd>; likewise, filtering by CIDR range (especially useful for DC deployments) can be achieved with e.g. <kbd>--filter '{"network.cidr_ranges": "&amp;gt;&amp;gt;10.22.30.0/24"}'</kbd> which uses the list membership operator <kbd>'&amp;gt;&amp;gt;'</kbd> to check that the provided CIDR range is present in the network asset's list of CIDR ranges.

<p>Use the <MadCap:variable name="SDKVariables.CLI" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> to download a list of problems for hosts in a given network:</p>

```

$ alcli --query 'assets' assets_query query_assets --account_id 134235891 --asset_types network,host,vulnerability --return_types host,vulnerability --filter '{"network.cidr_ranges": ">>172.31.0.0/16"}' --qfields key,name,severity,categories,details,description,cvss_score,private_ipv4_addresses
[
	[
		{
			"deployment_id": "4CC23525-71EB-422C-AEB1-4F57C9B75F15",
			"key": "/aws/ap-northeast-1/host/i-0afea2edef29888e4",
			"name": "shellshock",
			"private_ipv4_addresses": [
				"172.31.26.239"
			],
			"type": "host"
		},
		{
			"categories": [
				"security"
			],
			"cvss_score": 2.6,
			"deployment_id": "4CC23525-71EB-422C-AEB1-4F57C9B75F15",
			"description": "Unconfigured EC2 Instance Single-Point-of-Failure and/or Auto Scaling Issue",
			"details": "{standalone_ec2_instance,<<\"/aws/ap-northeast-1/host/i-0afea2edef29888e4\">>,\n                         <<\"shellshock\">>}",
			"key": "/aws/ap-northeast-1/host/i-0afea2edef29888e4/vulnerability/2362eefffbb7f5003264cff5f27801d2",
			"name": "Unconfigured EC2 Instance Single-Point-of-Failure and/or Auto Scaling Issue",
			"severity": "low",
			"type": "vulnerability"
		}
	],
	...
]
```

The same method can be used to retrieve a list of vulnerabilities for hosts in a given subnet: use the 'subnet' asset type in place of 'network', and filter based on its properties.
