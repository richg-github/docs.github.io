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
