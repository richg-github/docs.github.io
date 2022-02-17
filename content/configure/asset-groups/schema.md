# Asset Groups (Beta) Expression Reference

    This document is intended for early-access customers, and it is updated as Asset Group features are enhanced.     
If you want to create or edit your asset group manually with the Expression Editor (available from the [Asset Groups](../asset-groups.md) page), you can refer to the asset groups expression schema, JSON field definitions, and list of eligible assets. Expression samples are also provided to help you get started.

For more information, see:

* [JSON schema](#JSONschema)
* [Field definitions](#Fielddefinitions)
* [Eligible assets](#Eligibleassets)
* [Sample asset group expressions](#Sampleassetgroupexpressions)

To learn how to create or edit the expression by choosing assets and tags in the Configuration page instead, see [Asset Groups (Beta)](../asset-groups.md).

## JSON schema

{
  "scopes": [
    {
      "include": [],
      "exclude": [],
      "asset_types": []
    }
  ]
}
## Field definitions

* **scopes** (*object array*) – [Required] An array of scope objects that define the asset membership in the group. Each scope object represents distinct, independent criteria for group inclusion. If an asset meets the criteria defined in any scope, the group includes it. At least one object is required.
   * **include** (*array*) – [Required] An array of topological constraints on assets that define the asset membership in the group. The group includes any [eligible asset](#Eligibleassets) that meets the constraints on it (and whose topological ancestor assets meet the constraints on them).
   * **exclude** (*array*) – [Optional] An array of topological constraints on assets that define the asset membership in the group. The group excludes any [eligible asset](#Eligibleassets) that meets the constraints on it (and whose topological ancestor assets meet the constraints on them), even if the asset meets the includes criteria.
   * **asset_types** (*array*) – [Optional] An array of asset types strings that define what type(s) of assets can be in the group. If set, the group includes only assets of the given type(s). If not set, all eligible asset types can be included in the group. For the list of asset types, see  [Asset Type Key Name](#AssetTypeKeyName).

## Eligible assets

The following table lists asset types eligible for inclusion in, or exclusion from, an asset group and any additional supported asset properties.

To include or exclude a listed asset type,  type its key name and value in the expression using the following format:

<<kbd>asset_type_key_name</kbd>><kbd>:</kbd><<kbd>asset_key_value</kbd>>

For example: `“deployment:/al/134249236/deployment/aws/9969EC98-F3DD-4040-86C5-6A9019E2F07E”`
To include or exclude a listed asset property, type the key name, property name, and value in the expression using the following format:

“<<kbd>asset_type_key_name</kbd>><kbd>.</kbd><<kbd>asset_type_property_name</kbd>>:<`asset_type_property_value`>”

For example: <kbd>“deployment.type:aws”</kbd>
To restrict an asset group to specific asset types, you can list any of the  asset types in the Asset Type Key Name column as members of the `asset_types` array.

<table>
  <col />
  <col />
  <col />
  <col />
  <thead>
    <tr>
      <th>Asset Type</th>
      <th>Asset Type Key Name<a></a></th>
      <th>Asset Type Property: Friendly Name</th>
      <th>Asset Type Property Name</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Access Control List</td>
      <td>acl</td>
      <td>Not applicable</td>
      <td>Not applicable</td>
    </tr>
    <tr>
      <td>AKS Cluster</td>
      <td>aks-cluster</td>
      <td>Not applicable</td>
      <td>Not applicable</td>
    </tr>
    <tr>
      <td>Auto Scaling Group</td>
      <td>auto-scaling-group</td>
      <td>Not applicable</td>
      <td>Not applicable</td>
    </tr>
    <tr>
      <td>Blob Container</td>
      <td>blob-container</td>
      <td>Not applicable</td>
      <td>Not applicable</td>
    </tr>
    <tr>
      <td>CloudTrail</td>
      <td>cloud-trail</td>
      <td>Not applicable</td>
      <td>Not applicable</td>
    </tr>
    <tr>
      <td>Collector</td>
      <td>collector</td>
      <td>
        <ul>
          <li>Collector UUID</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>collector_uuid</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td> </td>
      <td> </td>
      <td>
        <ul>
          <li> Collector Type</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>collector_type</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td> </td>
      <td> </td>
      <td>
        <ul>
          <li>Collector Data Type</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>collector_datatype</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td> </td>
      <td> </td>
      <td>
        <ul>
          <li>Collector Platform</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>collector_platform</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td> </td>
      <td> </td>
      <td>
        <ul>
          <li>Collector Platform ID</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>collector_platform_id</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td> </td>
      <td> </td>
      <td>
        <ul>
          <li>Collector Region</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>collector_region</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td> </td>
      <td> </td>
      <td>
        <ul>
          <li>Collector Name</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>collector_name</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td> </td>
      <td> </td>
      <td>
        <ul>
          <li>Collector Full Name</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>collector_fullname</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td> </td>
      <td> </td>
      <td>
        <ul>
          <li>Application</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>application</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td> </td>
      <td> </td>
      <td>
        <ul>
          <li>Application ID</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>application_id</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td> </td>
      <td> </td>
      <td>
        <ul>
          <li>Native ID</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>native_id</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td> </td>
      <td> </td>
      <td>
        <ul>
          <li>Status</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>status</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td> </td>
      <td> </td>
      <td>
        <ul>
          <li>Status Updated</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>status_updated</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>DB Instance</td>
      <td>db-instance</td>
      <td>
        <ul>
          <li>DB Instance Class</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>db_instance_class</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td> </td>
      <td> </td>
      <td>
        <ul>
          <li>DB Name</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>db_name</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td> </td>
      <td> </td>
      <td>
        <ul>
          <li>Endpoint Address</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>endpoint_address</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td> </td>
      <td> </td>
      <td>
        <ul>
          <li>Endpoint Port</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>endpoint_port</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td> </td>
      <td> </td>
      <td>
        <ul>
          <li>Publicly Accessible</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>publicly_accessible </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td> </td>
      <td> </td>
      <td>
        <ul>
          <li>Storage Encrypted</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>storage_encrypted</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>Deployment</td>
      <td>deployment</td>
      <td>
        <ul>
          <li>Deployment Name</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>deployment_name</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td> </td>
      <td> </td>
      <td>
        <ul>
          <li>Deployment Type</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>deployment_type</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td> </td>
      <td> </td>
      <td>
        <ul>
          <li>Deployment ID</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>deployment_id</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td> </td>
      <td> </td>
      <td>
        <ul>
          <li>Last Scan Time</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>last_scan_time</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td> </td>
      <td> </td>
      <td>
        <ul>
          <li>Native Account ID</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>native_account_id</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>DNS Zone</td>
      <td>dns-zone</td>
      <td>
        <ul>
          <li> Zone Name</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>zone_name</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td> </td>
      <td> </td>
      <td>
        <ul>
          <li>Zone ID</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>zone_id</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>Host</td>
      <td>host</td>
      <td>
        <ul>
          <li>Alert Logic Appliance</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>alertlogic_appliance</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td> </td>
      <td> </td>
      <td>
        <ul>
          <li>Alert Logic Appliance Features</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>alertlogic_appliance_features</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td> </td>
      <td> </td>
      <td>
        <ul>
          <li>Architecture</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>architecture</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td> </td>
      <td> </td>
      <td>
        <ul>
          <li>Availability Zone</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>availability_zone</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td> </td>
      <td> </td>
      <td>
        <ul>
          <li>DNS Name</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>dns_name</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td> </td>
      <td> </td>
      <td>
        <ul>
          <li>Host UUID</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>host_uuid</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td> </td>
      <td> </td>
      <td>
        <ul>
          <li>Instance ID</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>instance_id</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td> </td>
      <td> </td>
      <td>
        <ul>
          <li>Instance Name</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>instance_name</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td> </td>
      <td> </td>
      <td>
        <ul>
          <li>Instance Type</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>instance_type</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td> </td>
      <td> </td>
      <td>
        <ul>
          <li>IP Address</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>ip_address</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td> </td>
      <td> </td>
      <td>
        <ul>
          <li>Last Discovery Time Stamp</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>last_discovery_ts</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td> </td>
      <td> </td>
      <td>
        <ul>
          <li>Last Scan Time</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>last_scan_time</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td> </td>
      <td> </td>
      <td>
        <ul>
          <li>Launch Time</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>launch_time</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td> </td>
      <td> </td>
      <td>
        <ul>
          <li>Local Host Name</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>local_hostname</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td> </td>
      <td> </td>
      <td>
        <ul>
          <li>Local IPv4</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>local_ipv4</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td> </td>
      <td> </td>
      <td>
        <ul>
          <li>Local IPv6</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>local_ipv6</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td> </td>
      <td> </td>
      <td>
        <ul>
          <li>Operating System Details</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>os_details</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td> </td>
      <td> </td>
      <td>
        <ul>
          <li>Operating System Type</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>os_type</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td> </td>
      <td> </td>
      <td>
        <ul>
          <li>Private DNS Name</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>private_dns_name</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td> </td>
      <td> </td>
      <td>
        <ul>
          <li>Private IP Address</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>private_ip_address</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td> </td>
      <td> </td>
      <td>
        <ul>
          <li>Private IP Addresses</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>private_ip_addresses</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td> </td>
      <td> </td>
      <td>
        <ul>
          <li>Private IPv4 Addresses</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>private_ipv4_addresses</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td> </td>
      <td> </td>
      <td>
        <ul>
          <li>Private IPv6 Addresses</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>private_ipv6_addresses</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td> </td>
      <td> </td>
      <td>
        <ul>
          <li>Public DNS Name</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>public_dns_name</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td> </td>
      <td> </td>
      <td>
        <ul>
          <li>Public IP Address</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>public_ip_address</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td> </td>
      <td> </td>
      <td>
        <ul>
          <li>Public IP Addresses</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>public_ip_addresses</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td> </td>
      <td> </td>
      <td>
        <ul>
          <li>Public IPv4</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>public_ipv4</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td> </td>
      <td> </td>
      <td>
        <ul>
          <li>Public IPv4 Addresses</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>public_ipv4_addresses</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td> </td>
      <td> </td>
      <td>
        <ul>
          <li>Public IPv6</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>public_ipv6</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td> </td>
      <td> </td>
      <td>
        <ul>
          <li>Public IPv6 Addresses</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>public_ipv6_addresses</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td> </td>
      <td> </td>
      <td>
        <ul>
          <li>State</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>state</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>Internet Gateway</td>
      <td>igw</td>
      <td>Not applicable</td>
      <td>Not applicable</td>
    </tr>
    <tr>
      <td>Image</td>
      <td>image</td>
      <td>•	Image ID</td>
      <td>•	image_id</td>
    </tr>
    <tr>
      <td>Instance Profile</td>
      <td>instance-profile</td>
      <td>Not applicable</td>
      <td>Not applicable</td>
    </tr>
    <tr>
      <td>Key Vault</td>
      <td>key-vault</td>
      <td>
        <ul>
          <li>Key Vault ID</li>
        </ul>
      </td>
      <td>•	key_vault_id</td>
    </tr>
    <tr>
      <td>Key Vault Key</td>
      <td>key-vault-key</td>
      <td>Not applicable</td>
      <td>Not applicable</td>
    </tr>
    <tr>
      <td>Key Vault Secret</td>
      <td>key-vault-secret</td>
      <td>Not applicable</td>
      <td>Not applicable</td>
    </tr>
    <tr>
      <td>KMS Key</td>
      <td>kms-key</td>
      <td>Not applicable</td>
      <td>Not applicable</td>
    </tr>
    <tr>
      <td>Load Balancer</td>
      <td>load-balancer</td>
      <td>
        <ul>
          <li>Name</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>name</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td> </td>
      <td> </td>
      <td>
        <ul>
          <li>Scheme</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>scheme</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td> </td>
      <td> </td>
      <td>
        <ul>
          <li>DNS Name</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>dns_name</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>Log Profile</td>
      <td>log-profile</td>
      <td>Not applicable</td>
      <td>Not applicable</td>
    </tr>
    <tr>
      <td>Network Security Group</td>
      <td>nsg</td>
      <td>Not applicable</td>
      <td>Not applicable</td>
    </tr>
    <tr>
      <td>Redshift Cluster</td>
      <td>redshift-cluster</td>
      <td>
        <ul>
          <li>Cluster Identifier</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>cluster_identifier</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>Region</td>
      <td>region</td>
      <td>
        <ul>
          <li>Region Name</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>region_name</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>Resource Group</td>
      <td>resource-group</td>
      <td>Not applicable</td>
      <td>Not applicable</td>
    </tr>
    <tr>
      <td>Role</td>
      <td>role</td>
      <td>Not applicable</td>
      <td>Not applicable</td>
    </tr>
    <tr>
      <td>Route</td>
      <td>route</td>
      <td>Not applicable</td>
      <td>Not applicable</td>
    </tr>
    <tr>
      <td>S3 Bucket</td>
      <td>s3-bucket</td>
      <td>
        <ul>
          <li>Bucket Name</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>bucket_name</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td> </td>
      <td> </td>
      <td>
        <ul>
          <li>Bucket Owner</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>bucket_owner</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>Security Group</td>
      <td>security-group</td>
      <td>
        <ul>
          <li>Group Name</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>group_name</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td> </td>
      <td> </td>
      <td>
        <ul>
          <li>Group ID</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>group_id</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>Storage Account</td>
      <td>storage-account</td>
      <td>Not applicable</td>
      <td>Not applicable</td>
    </tr>
    <tr>
      <td>Subnet</td>
      <td>subnet</td>
      <td>
        <ul>
          <li>Alert Logic Security</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>alertlogic_security</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td> </td>
      <td> </td>
      <td>
        <ul>
          <li>CIDR Block</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>cidr_block</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td> </td>
      <td> </td>
      <td>
        <ul>
          <li>State</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>state</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td> </td>
      <td> </td>
      <td>
        <ul>
          <li>Subnet ID</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>subnet_id</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td> </td>
      <td> </td>
      <td>
        <ul>
          <li>Subnet UUID</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>subnet_uuid</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td> </td>
      <td> </td>
      <td>
        <ul>
          <li>Subnet Name</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>subnet_name</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>User</td>
      <td>user</td>
      <td>
        <ul>
          <li>User FQDN</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>user_fqdn</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td> </td>
      <td> </td>
      <td>
        <ul>
          <li>User ID</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>user_id</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td> </td>
      <td> </td>
      <td>
        <ul>
          <li>User Type</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>user_type</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>Volume</td>
      <td>volume</td>
      <td>
        <ul>
          <li>Volume ID</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>volume_id</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>VPC/VNet/Network</td>
      <td>vpc</td>
      <td>
        <ul>
          <li>CIDR Ranges</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>cidr_ranges</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td> </td>
      <td> </td>
      <td>
        <ul>
          <li>Network UUID</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>network_uuid</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td> </td>
      <td> </td>
      <td>
        <ul>
          <li>VPC ID</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>vpc_id</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td> </td>
      <td> </td>
      <td>
        <ul>
          <li>VPC Name</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>vpc_name</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td> </td>
      <td> </td>
      <td>
        <ul>
          <li>State</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>state</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>Web Application</td>
      <td>webapp</td>
      <td>
        <ul>
          <li>HTTPS Only</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>https_only</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td> </td>
      <td> </td>
      <td>
        <ul>
          <li>Client Certificate Enabled</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>client_cert_enabled</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td> </td>
      <td> </td>
      <td>
        <ul>
          <li>Platform Type</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>platform_type</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td> </td>
      <td> </td>
      <td>
        <ul>
          <li>Web Application Type</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>webapp_type</li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>## Sample asset group expressions

The following examples cover useful ways to define asset groups. You can use these examples as a guide when  you create asset groups relevant to your organization and its security goals.

### All assets in a region of a specific deployment

Suppose that you want an asset group to include all the assets in just one of your AWS deployments and only in one region (us-east-1). To do this, you need two `include` expressions. The resulting asset group contains all eligible assets (region, vpc, subnet, host, and so on) in the us-east-1 region of the specified AWS deployment.

{
  "scopes": [
    {
      "include": [
        "deployment:/deployment/aws/876AE14C-2F77-45E5-8E32-4B0A09894E72",
        "region:/aws/us-east-1"
     ]
    }
  ]
}
### All hosts in a region of a specific deployment

Suppose that you want to include the hosts in just one of your AWS deployments and only in one region (us-east-1), but you do not want to include the other assets (VPCs, load balancers, auto scaling groups, images, and so on) in the group (for example, you only want to receive escalations for host resources in the deployment). You can use the same constraints as in the example [All assets in a region of a specific deployment](#Allassetsinaregionofaspecificdeployment), but with the `asset_types` array to ensure that the group includes only the assets of the type you want.

{
  "scopes": [
    {
      "include": [
        "deployment:/deployment/aws/876AE14C-2F77-45E5-8E32-4B0A09894E72",
        "region:/aws/us-east-1"
      ]
    }
  ],
  "asset_types": ["host"]
}
### All assets in a region of a specific deployment, except for a subnet with a specific name

Suppose that you want to include all the assets in just one of your AWS deployments and only in one region (us-east-1), but you want to exclude the "AlertLogic Security Subnet" hosts from the group. You want to exclude subnets with that name because the assets in those subnets are part of the Alert Logic infrastructure, not yours. You use an `exclude` in this case and reference the subnet by name rather than key or ID. Many subnets named "AlertLogic Security Subnet" might be in a single region, and the key or ID  property excludes a specific AlertLogic Security Subnet instead of all subnets in the region with that name.

{
  "scopes": [
    {
      "include": [
        "deployment:/deployment/aws/876AE14C-2F77-45E5-8E32-4B0A09894E72",
        "region:/aws/us-east-1"
      ],
      "exclude": [
        "subnet.subnet_name:AlertLogic Security Subnet"
      ]
    }
  ]
}
### All hosts in a specific Data Center deployment, except hosts in 10.0.1.0/24

Suppose that you have a Data Center production deployment that is very big, and you have not yet organized your subnets to classify your network assets. Still, you want to include all the hosts in the deployment in your “production” group, except the hosts in the 10.0.1.0/24 CIDR range, because those hosts are not used for production purposes and are safely isolated from network access to the rest of the deployment. You can use the `:cidr_match:` operation to exclude hosts that include an IP address in that CIDR range in their private_ip_addresses field, like this:

{
  "scopes": [
    {
      "include": [
        "deployment:/deployment/F00FECFC-3378-486A-ACD3-4160DBF1F40D"
      ],
      "exclude": [
        "host.private_ip_addresses::cidr_match:10.0.1.0/24"
      ],
      "asset_types": ["host"]
    }
  ] 
}### All assets with a specific tag

Suppose that you want to add all assets with a specific tag to a group, so that you can mark all the tagged assets (and their topological successor assets) across all your deployments as being in the asset group to escalate to the platform-services team when an incident is raised on them. In that case, you can use the "tag" on the `include`, and the resulting asset group includes any eligible asset that has that tag, along with any of its topological successor assets.

For example, if a VPC is tagged with mgr:some-manager, all of the subnets, hosts, load balancers, and so on that are in that VPC are part of the group, even if those individual assets are not specifically tagged with the mgr tag.

{
  "scopes": [
    {
      "include": [ 
        "tag:/tag/key/mgr/value/some-manager"
      ]
    }
  ]
}
