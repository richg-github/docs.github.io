<h1>Adjust How Frequently <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> Scans Your External Assets Using the <MadCap:variable name="SDKVariables.CLI" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /></h1><p>To ensure that your infrastructure remains secure and no known vulnerabilities are present, <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> periodically performs vulnerability scans against the assets listed in your deployments. External vulnerability scans are conducted against infrastructure that is publicly accessible over the internet. This guide details how to change the frequency of external vulnerability scans to an interval that suits your operational or compliance needs.</p>

<MadCap:snippetBlock src="../Resources/Snippets/sub-typess-ess-pro.flsnp" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />## Requirements

<p>This use case requires that the <MadCap:variable name="SDKVariables.CLI" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> is already <a href="../cli/install.md">installed and configured</a>, and that you have at least one deployment configured.</p>

## Technical details

This example shows you how to tune an Amazon Web Services deployment, though the external scan frequency of any platform type can be modified.

### About scan intervals

When selecting the frequency of your external scans the  options available are:

* Daily (default) – ensures that every public facing asset is scanned at least once per day
* Weekly– ensures that every public facing asset is scanned at least once per week
* Monthly – ensures that every public facing asset is scanned at least once per month

### About OTIS options

<p>Scan intervals are represented as tuning options in the Otis service. These options allow you to customize the behavior of certain features in the <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> platform, in this case external vulnerability scans.</p>

Options can be applied to a variety of scopes, giving fine-grained control over which assets are affected by configured tuning options. The available scopes are as follows:

* deployment_id (string) – by providing the UUID of a deployment, the given option applies to all relevant assets in that deployment
* region_key (string) – by providing the asset key of a region, the option applies to all relevant assets in the region
* vpc_key (string) - by providing the asset key of a region, the option applies to all relevant assets in the region

When an asset is covered by multiple scopes, the option priority in descending order is: vpc_key > region_key > deployment_id

For more information on available tuning options, check the Otis Service API documentation.

## View external scan interval option

Before we start customizing the frequency of our external scans, we can check to see if there are any previous configuration options set for our deployment:

```

$ alcli otis list_options --account_id 134235158
```

Response:

```

[
	{
		"id": "0F1E0621-4A0F-2169-7A19-6B33144797D6",
		"name": "external_scan_frequency",
		"scope": {
			"deployment_id": "E539FE1F-C764-401C-9EED-DF7A8034BF65"
		},
		"value": "daily"
	}
]
```

We can determine from this response that our external scan frequency is set to daily for deployment E539FE1F-C764-401C-9EED-DF7A8034BF65.

## Create external scan interval option

To create a similar option as the one specified above, we can modify the external scan interval at multiple scopes for within our deployment using the create_option command in the otis service:

### Set external scan interval for deployment

To set external scan frequency to daily across our deployment as shown above, we can use the following command:

```

alcli otis create_option --account_id 134235158 --option file://option.json
```

option.json contents:

```

{
	"scope": {
		"deployment_id": "E539FE1F-C764-401C-9EED-DF7A8034BF65"
	},
	"value": "daily",
	"name": "external_scan_frequency"
}
```

Output

```

{
	"id": "0F1E0621-4A0F-2169-7A19-6B33144797D6",
	"name": "external_scan_frequency",
	"scope": {
		"deployment_id": "E539FE1F-C764-401C-9EED-DF7A8034BF65"
	},
	"value": "daily"
}
```

On success we’re returned the created option along with its UUID.

You can configure external scan frequency at the region and VPC level by providing a “region” or “vpc” in the scope object with the corresponding asset key for either asset.

## Remove external scan interval setting

Should you wish to remove an existing option and return to the default automatic behavior:

```

$ alcli otis delete_option --account_id 134235158 --option_id F50DFAB1-C179-3BDD-9EDB-B55B93AD9D3B
```

Response:

```

HTTP Status Code: 204
```

A HTTP 204 status code is returned when the option has been deleted successfully.

## See also

To review what other tuning options are available to you, check the Otis service documentation.

<p>Details on how to set up an <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> Deployment can be found on the docs site</p>
