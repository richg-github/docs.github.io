# Remediations

Remediations has been deprecated and replaced  as part of Dashboards. The information available on the Remediations page is available in [Exposures](exposures.md).

The Remediations page displays the number and types of exposures in the protected deployment, and provides you with information about the exposure, including color-coded threat level, evidence, and recommendations to address the exposure.

The Remediations Summary and the Remediations List, under the Remediations tab in the Alert Logic console provide you with the information you need to analyze and address issues in your environment.

You can check the operational status of the Remediations service in the Service Status page in the Alert Logic console. Alert Logic recommends that you subscribe to the Service Status page and all your Alert Logic components, including Remediations &amp; Automated Scan. For more information about the Service Status page and how to subscribe, see [Service Status](service-status.md).

## About exposure levels

The Remediations page uses colors and icons to help you easily identify the priority levels of remediations and the threat levels of exposures. Alert Logic categorizes remediation priority and threat levels of exposures with the following icons and colors:

* ![](../Resources/Images/Icons/threat_critical_icon.png) High
* ![](../Resources/Images/Icons/threat_high_icon.png) Medium
* ![](../Resources/Images/Icons/threat_medium_icon.png) Low
* ![](../Resources/Images/Icons/threat_info_icon.png) Info

## About remediation types

There are two types of remediations Alert Logic creates, security and configuration remediations.

### Security Remediations

Alert Logic creates security remediations when issues related to vulnerabilities identified in a scan, such as an attack or vulnerability that could lead to a breach if not addressed. The following are some examples why Alert Logic will create a security remediation:

* IAM Access Keys have been unused for 90 days
* Unrestricted outbound access on all ports
* Program is outdated

### Configuration Remediations 

Alert Logic creates configuration remediations when issues related to your deployment  can hinder Alert Logic from delivering service properly, such as no agents or appliance installations, or a misconfiguration where an appliance cannot connect to the backend. The following are some examples why Alert Logic will create a configuration remediation:

* Hosts have not been recently scanned
* Insufficient policy and role privileges
* AWS Config is not enabled in all regions

## Remediations Summary

The Remediations  summary provides a graph of  remediation priorities for the security and configuration exposures discovered in your deployments, virtual networks, or networks.

The graph allows you to display exposures by type of exposure (Security or Configuration) or asset context (Deployment or VPC/Network) and by deployment, or VPCs and networks. The color-coded circles are higher or lower depending on the exposure severity level of the remediations within that deployment, VPC, or network, and  organized from worst to best (left to right). If some items do not fit in the graph view, you can click the arrow on the right of the graph to scroll and view over more items.

To see more details about a remediation, hover over a remediation circle. To see more details about an asset, hover over a deployment, or VPC and network.

Click the remediation circle to open the Remediations List, filtered by that exposure level and the specified deployment, VPC, or network. Click a deployment, or VPC and network on the graph to open the Remediation List, filtered by remediations in that deployment, VPC, or network.

## Open remediations

This List view displays a list of the recommended actions to remediate exposures for the selected deployment. Scroll through the recommended remediations to find and flag the remediation actions to add to your remediation plan, execute the recommended steps, and increase the security of your environment.

To change the remediation list to another deployment, click the deployment name, and then select another deployment.

### Filters and filter sets

By default, the remediation list displays all open remediations, but you can also choose to view the list of remediations that are **Planned** (assigned to you), **Disposed** (removed from the list), or **Completed** (considered to be addressed) by using the left hand navigation filters.

You can select one or more available filters to narrow your list of remediations. The active filter is in bold format. Select one or more of the active filters to remove them. You can also select **CLEAR FILTERS** to remove all the active filters, or select **SAVE FILTER SET** to add the active filter to the list of **your Saved Filter Sets** list.  Filter sets you create on the Remediations page are also available from the summary page.

### Other actions

Other actions you can take on the open list include:

* Select one or more remediations check boxes that you want to add to your plan (![](../Resources/Images/General/Icons/Remediations/plan.png)), dispose (![](../Resources/Images/General/Icons/Remediations/disposed_21x22.png)), or mark as complete (![](../Resources/Images/General/Icons/Remediations/complete_18x18.png)).
* View remediations that are currently open, but in another user’s plan within the open remediations list.
* Click anywhere on the remediation to go to the detail page to see more information about the suggested remediation.
* Click the deployment name to select another deployment for which you want to view results.

## Remediation actions

You can select one or more remediations, and then click the planned icon (![](../Resources/Images/General/Icons/Remediations/plan.png)) to add to your plan, or click the dispose icon (![](../Resources/Images/General/Icons/Remediations/disposed.png)) to dispose the remediation, or click the complete icon (![](../Resources/Images/General/Icons/Remediations/complete.png)) to mark them as complete from the open list. You can also click anywhere on the remediation to view more information about the remediation in its details page.

### Details page

The Detail page displays a description of the suggested remediation, where you can click listed exposures, affected assets, and evidence entries for to read more information about each. You can also add to your plan, dispose of the remediation, or mark it as complete from this page.

### Planned

Your plan list is a customized list of action items, selected from the Open page, that you want to track and address.

You can prioritize remediation date range:

* All
* This Month
* This Week
* Today
* Custom Date Range

Select one or more remediations and then click the complete icon (![](../Resources/Images/General/Icons/Remediations/complete.png)) to mark them as complete, or click the dispose icon (![](../Resources/Images/General/Icons/Remediations/disposed.png)) to dispose them, or click the restore icon (![](../Resources/Images/General/Icons/Remediations/restore.png)) to restore them to the open list.

### Dispose

You can select one or more remediations from the Open or Planned lists, and then click the dispose icon (![](../Resources/Images/General/Icons/Remediations/disposed.png)) to dispose them. You must specify a period of time, and select the exposures as an acceptable risk, a false positive, or have a compensating control in place. After a disposal period expires, Alert Logic no longer ignores the exposures in the remediation, and the remediation appears again in the Open page.

In the Dispose list, you can prioritize remediation date range:

* All
* This Month
* This Week
* Today
* Custom Date Range

You also have the option to review and restore them to your Open list for other users to add to their plans. Select one or more remediations, and then click the restore (![](../Resources/Images/General/Icons/Remediations/restore.png)) icon to move them to the Open list.

If you mark a remediation as disposed, Alert Logic excludes the calculated risk of their vulnerabilities from the overall risk of your deployment.

### Complete

You can mark remediations as complete from the open or planned lists. Select one or more remediations, and then click the complete icon (![](../Resources/Images/General/Icons/Remediations/complete.png)) to move them to the Completed page.

In the Complete list, you can prioritize remediation date range:

* All
* This Month
* This Week
* Today
* Custom Date Range

You also have the option review and restore them to your Open list. Select one or more remediations, and then click the restore icon (![](../Resources/Images/General/Icons/Remediations/restore.png)) to mark them as open again and restore their view in the Open lists.

If you mark the remediation as complete, Alert Logic verifies the exposure no longer exists during the next deployment scan.
