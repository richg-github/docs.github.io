<h1>Download a List of Configured AWS or Azure Deployments that <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> Cannot Access</h1><p>The <MadCap:variable name="SDKVariables.CLI" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> can be used to download a list of AWS or Azure deployments whose credentials are either invalid or insufficient, which prevents <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> from discovering the assets in that deployment and, in the case of AWS deployments, from deploying or managing security infrastructure.</p>

<MadCap:snippetBlock src="../Resources/Snippets/sub-types-ess-pro-cd.flsnp" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />## Requirements

<p>This use case requires that the <MadCap:variable name="SDKVariables.CLI" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> is already <a href="../cli/install.md">installed and configured</a>, and that there are AWS or Azure deployments in the account.</p>

## Technical Details

<p>
  <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> uses the credentials associated with an AWS or Azure deployment to discover the infrastructure present in the accounts held on those platforms; and in the case of AWS deployments, the same credential is used to deploy and/or manage (where applicable) security infrastructure such as scanning appliances or IDS appliances.</p>

<p>Such permissions errors are reported by the Explorer services -- CloudExplorer for AWS deployments, and AzureExplorer for Azure deployments -- which update the deployment status in the Deployments service. The <MadCap:variable name="SDKVariables.CLI" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> can be used to retrieve a list of AWS or Azure deployments reporting permissions errors.</p>

<h2>Download a list of deployments that <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> cannot access</h2><p>Use the <MadCap:variable name="SDKVariables.CLI" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> to query the Deployments service, using the --query parameter to filter the results to only include deployments in error:</p>

```

$ alcli --query "[?status.status=='error']" deployments list_deployments --account_id 134235891
[
	{
		"account_id": "134235891",
		"cloud_defender": {
			"enabled": false
		},
		"created": {
			"at": 1594667725,
			"by": "8593ED9F-2F49-4E57-A45C-652AD4A74D12"
		},
		"credentials": [
			{
				"id": "DEADB33F-E0D7-4B9F-B457-EE9D7D197FFB",
				"purpose": "discover",
				"version": "2019-05-21"
			}
		],
		"discover": true,
		"enabled": true,
		"id": "DEADB33F-9BE0-4756-98E9-F7A2B7FBDAFE",
		"mode": "automatic",
		"modified": {
			"at": 1594667728,
			"by": "8593ED9F-2F49-4E57-A45C-652AD4A74D12"
		},
		"name": "my-deployment",
		"platform": {
			"id": "966236000000",
			"monitor": {
				"ct_install_region": "us-east-1",
				"enabled": true
			},
			"type": "aws"
		},
		"scan": true,
		"scope": {
			"exclude": [],
			"include": []
		},
		"status": {
			"status": "error",
			"message": "permission_error",
			"updated": 1594928988
		},
		"version": 7
	}
]
```

The JMESPath query can be extended to only select deployments of a certain type ('aws' or 'azure'). For example, for AWS, use:

```

$ alcli --query "[?status.status=='error' &amp;&amp; platform.type == 'aws']" deployments list_deployments --account_id 134235891
```

For Azure, use:

```

$ alcli --query "[?status.status=='error' &amp;&amp; platform.type == 'azure']" deployments list_deployments --account_id 134235891
```

Likewise, the JMESPath query can be extended to extract the fields which are of interest:

```

$ alcli --query "[?status.status=='error'].{account_id: account_id, name: name, platform_id: platform.id, deployment_id: id}" deployments list_deployments --account_id 134235891
[
	{
		"account_id": "134235891",
		"name": "my-deployment",
		"platform_id": "966236000000",
		"deployment_id": "DEADB33F-9BE0-4756-98E9-F7A2B7FBDAFE"
	}
]
```
