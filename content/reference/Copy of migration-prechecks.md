# Migration Prechecks

Source page: https://alertlogic.atlassian.net/wiki/spaces/PD/pages/1284046849/Migration+Pre-Checks+Explained

I went through and made all the issues into info dev style. The next step is putting the descriptions from the bottom into the relevant checks above (like "Deployments with no credentials"). I delete the ones that are on the AL side only because they won't help the customer prepare.

## Must Resolve Before Migration

These are items that need to be addressed pre-migration.

### Deployments that are not in OK status

This is probably one of the more important items to address pre-migration if possible, as the more the agent/sources/devices are cleaned up the easier the migration process will run, and minimize the post-migration tasks significantly.  This is something that can be worked on by any team, so if a CSM/PM/Support to “clean up” the configuration pages of hosts in new, offline, or error status.

New: The main concern here is any protected host in the new state should be assigned to an appliance before the migration occurs as to not create duplicate networks. This is not a hard requirement but definitely a recommendation.

Offline: If any Appliance, Log Source or Protected Host is offline and not expected to be in use moving forward, the customer should consider archiving and deleting these items respectively before migrating

Error: Investigate why the Log Source or Protected Host is in error and remediate if possible. This can really be done either before or after. But if the host is associated to the incorrect assignment policy, this could cause duplicate networks as well. So if at all possible it is recommended to be managed before the migration.

### Deployments with no credentials

To fix this, you need to update the AWS policy for the deployment. In theAlert Logic console, navigate to the deployment, and click **AWS Instructions** > **Copy Policy** under Step 2e.

### Outdated AWS IAM role

### More than one scan schedule configured OR Scan schedule is not for DC Deployment

### deployments with unassigned agents detected - N/A

### Overlapping network ranges

Need more info on this one to help customers self-serve

### Legacy appliances configured

### TMAppliance provisioning status error

The new pre-check utilises the new IRS endpoint which reports the provisioning status of TMAppliance. So it can be used separately as a TMAppliance provisioning troubleshooting tool

### Invalid CIDRs detected

## Recommended but Not Required to Address Before Migration

These do not necessarily break anything when migrating, but they can and do complicate the network creation and health page unnecessarily. As well they will cause additional unnecessary work post migration to fix for the Implementation Engineer.

### Protected Hosts with status new

### Protected Hosts with status offline

### Log Sources with status offline 

### Threat Appliances with status offline

### Network CIDR intersection 

Make sure that your network ranges do not overlap.

## Resolved During Migration Job*

These items are manipulated during the actual migration process.

### missing_new_incident_console - The Customer gets migrated to new Incident Console during the upgrade

If this item shows up in the pre-check list it means the customer is using the pre-seimless incident console (aka Iris?).  This is something that is a hard stop for migrations as of 05/2020, but is supposed to be resolved by updating the instigator migration code.  If a migration is already on the schedule recommend reaching out to Usage Services in Teams via the Usage Services channel under the Engineering Questions team. They will be able to upgrade the customer to the newer incidents console for individual requests.

### Network CIDR intersection detected - in some cases cidr intersections are addressed*

## Post Migration Resolution

These are all intended to be informational, but do require work from either the customer or the Implementation Engineer post Migration.

### webhook_usage - The Customer has webhooks configured, need to reconfigure for new herald

### Network CIDR intersection detected - duplicate deployments in UK/US dc's and/or merging of networks

## Informational Checks 

These are checks that may or may not require that they be addressed and usually have to be looked at by an engineer to determine if they are something to be addressed.

### collection alerts usage detected - 

Inform the customer that this function was deprecated in the MDR platform. It was replaced with the health summary notification if they would like to set this up after migration.

### cross-network protection configuration detected -

Inform the customer that Cross-Network Protection will automatically be configured for their deployment in the MDR platform, also known as VPC peering in AWS.

### agent_version_outdated - 

### suggestions_analysis_error -                                 

## Deprecated Services or Features

The majority of these are intended to inform the customer of functions that either do not exist in MDR or will not transfer over to MDR.  The customer may have to re-create or re-configure these items post-migration to achieve the same or similar outcomes they had before, if applicable.

For more information, see [Upgrade to Managed Detection and Response](../get-started/upgrade-console.md#Deprecat).

* Saved Views cannot migrate
* Event Alert Rules
* Log Correlation Rules
* agents with no TM source detected - N/A
* Blocking policies
* OOB WAF
* **globalid_scheduled_reports - no personal saved views will be migrated, or ones with missing author
