# Asset Groups (Beta)

    This document is intended for early-access customers, and it is updated as Asset Group features are enhanced.     
The Asset Groups page, listed under ![](../Resources/Images/dashboard/configure-icon.png)**Configure** in the Alert Logic console, offers a consolidated view of  all asset groups created in your account. You can create and manage  asset groups from this page. An asset group is a user-defined set of assets that you want Alert Logic to act on in some way to increase the security of your environment. For example, after you create an asset group, it becomes available as an Asset Group filter on the [Health](../analyze/health.md) page,  which you can then use to view the connection status for any assets that are members of the group.  by selecting it as a filter You can also configure an automated response playbook to run on a specific asset group. Your assets can belong to more than one group.

You can also create a linked group that includes multiple asset groups. For example, you can create several asset groups related to compliance and then link them together in a Compliance group.

## Create an asset group

To create an asset group, you enter details about the group and then configure it. For more information about the tabs on the Configuration page that appear after you enter the asset group details, see [Asset group configuration](#Assetgroupconfiguration).

**To enter details about the asset group:**

1. In the Alert Logic console, click the navigation menu icon (![](../Resources/Images/dashboard/menu-icon.png)), click ![](../Resources/Images/dashboard/configure-icon.png)**Configure**, and then click **Asset Groups**.
2. On the Asset Groups page, click the add icon (![](../Resources/Images/Icons/cdAddPlus.png)), and then click **Asset Group**.
3. Type a descriptive name that easily identifies this asset group in a list—for example, "HIPAA."
4. (Optional) Select a criticality rating between 0 and 10 for your asset group. 
The value indicates how important it is to protect assets belonging to the group. Alert Logic multiplies the value by the [Threat Risk Index (TRI)](../analyze/TRI-score-factors.md) to obtain a weighted score that accounts for your scale.Suppose the criticality ratings in your organization are Info, Low, Medium, and High. Your team decides to assign values of 0 to 3 to your asset groups to account for this scale. To indicate  an asset group has a Medium criticality in this scenario, your team selects **2**.
5. Type a detailed description for your asset group to help you identify the asset group later.
6. Click **SAVE AND CONTINUE**.

**To select assets to include in or exclude from the group:**

1. In the **Assets** tab on the Configuration page, expand  the list of assets until you find the asset of interest, and then click the asset. 
For information about how to filter the asset list and select other asset types to view in the list, see [Assets tab](#Assetstab).
2. In the asset details that appear on the right, click the include icon  (![](../Resources/Images/asset-groups/icon-check-box.png)) next to the asset name at the top of the list (this is the asset key value) or one or more asset properties that you want to include. To include a specific subnet, for example, select the name of the subnet in the asset list and then include the subnet key value. To include any subnet in the deployment with a specific name such as "Alert Logic Security Subnet," include the Subnet Name property instead. In that scenario, the asset group includes any subnet with that name across the entire deployment.
3. (Optional) To exclude an asset or one or more of its properties, click the exclude icon (![](../Resources/Images/asset-groups/icon-check-box-x.png)) next to it. You cannot exclude an asset unless you include a parent of the asset. You cannot exclude an asset property unless you include the asset or one of its parents.For example, if you select a VPC that includes three subnets, you can exclude one of the subnets from your asset group. You cannot exclude a subnet until the parent VPC (or other ancestor  in the deployment) is included.

**To select assets to include in or exclude from the group with tags:**

1. On the Configuration page, click the **Tags** tab, find the asset tag of interest, and then click the asset tag. 
To filter the list, you can search for characters in your asset tag names. For more information about the Tags tab, see [Tags tab](#Tagstab).
2. In the asset tag properties that appear on the right, click the include icon  (![](../Resources/Images/asset-groups/icon-check-box.png)) next to the tag key value at the top of the list or one or more tag properties that you want to include. 
 For example, if you select a tag and include the key value, the asset group includes only assets that have a tag with that name and value. If you include the tag name, the asset group includes any asset with that tag name, regardless of the value. Similarly, you can include a value to include assets with tags that have that value, regardless of the tag name.
3. (Optional) To exclude a tag or one or more of its properties, click the exclude icon  (![](../Resources/Images/asset-groups/icon-check-box-x.png)) next to it. You cannot exclude a tag unless you include an asset with that tag or its parent. You cannot exclude a tag property unless you include the tag, an asset with the tag, or a parent of an asset with the tag.

To view, edit, or create the asset group expression:

1. On the Configuration page, click the **Expression** tab. If you selected assets to include and exclude on the Assets or Tags tabs, they appear in the Expression Editor. 
For more information about the Expression tab, see [Expression tab](#Expressiontab).
2. (Optional) To edit or create the expression manually, click the **EDIT** icon. A red bar next to a line indicates a syntax error. Code with errors is underlined with a jagged red line. You can hover the pointer over the underlined code to view a tip about the error.
For more information, see [Asset Groups (Beta) Expression Reference](asset-groups/schema.md).
3. When you finish editing, click **UPDATE** to apply your changes, or click **CANCEL** to discard your edits. 
Selections on the Assets tab and the Tags tab refresh when you update the expression.
4. When you finish configuring your asset group, click **ADD**.

### Asset group configuration

To configure your asset group, you can choose assets and asset tags that you want to include in or exclude from your group. As you configure the group in the Asset tab and Tags tab, Alert Logic creates an expression that you can view and edit in the Expression tab.

#### Assets tab

The Assets tab includes the asset topology in your account and the accounts you manage. The asset topology is a list of your deployments and the interconnected assets in the deployments. The asset filters selected determine which asset types appear in the list. If you want a different view of your assets, you can select other filters. By default, the top level of the hierarchical list is your deployments, followed by their regions, networks, subnets, and hosts, if present. The number of each of these assets in the deployment appears next to the deployment name. A search bar allows you to search for characters in your asset names to filter the list.  Only the items that include the characters, plus their parent assets, appear in a searched asset list.

After you filter the list as needed, you can click an asset type in the list to view its properties. The asset key value is at the top, followed by the asset properties. Next to the key value and each property is an include icon ( ![](../Resources/Images/asset-groups/icon-check-box.png)) and an exclude icon ( ![](../Resources/Images/asset-groups/icon-check-box-x.png)) that you can click to include it in or exclude it from the group. You cannot exclude an asset unless you include a parent of the asset. You cannot exclude an asset property unless you include the asset or one of its parents.

When you include or exclude assets, icons appear in the asset list that indicate the following:

| ![](../Resources/Images/asset-groups/icon-green-solid-check.png) | The group includes this asset. |
| ![](../Resources/Images/asset-groups/icon-green-faded-check.png) | The group includes this asset because a parent asset is selected for inclusion. |
| ![](../Resources/Images/asset-groups/icon-green-check.png) | This asset contains other assets that are included in the group. In other words, the asset group does not include this asset, but it does include one or more of its child assets. |
| ![](../Resources/Images/asset-groups/icon-red-x.png) | The group excludes this asset. |
| ![](../Resources/Images/asset-groups/icon-red-faded-x_25x26.png) | The group excludes this asset because a parent asset is selected for exclusion. |

#### Tags tab

Another useful way to include assets in your group is with tags. The Tags tab includes a list of asset tags in your deployments. A search bar allows you to search for characters in your asset tag names to filter the list.  Only the tags that include the characters appear in a searched tags list.

You can click a tag to view its properties. The tag key value is at the top, followed by the tag properties. Next to the key value and each property is an include icon  (![](../Resources/Images/asset-groups/icon-check-box.png)) and an exclude icon  (![](../Resources/Images/asset-groups/icon-check-box-x.png)) that you can click to include it in, or exclude it from, the group.  You cannot exclude a tag unless you include an asset with that tag or its parent. You cannot exclude a tag property unless you include the tag, an asset with the tag, or a parent of an asset with the tag.

When you include or exclude asset tags, icons appear in the asset list that indicate the following:

| ![](../Resources/Images/asset-groups/icon-green-solid-check.png) | The group includes assets with this tag. |
| ![](../Resources/Images/asset-groups/icon-red-x.png) | The group excludes assets with this tag. |

In the Tagged Assets section of the property details, a list of assets with that tag appears and includes the number of assets with the tag.

#### Expression tab

The Expression tab displays the JSON expression that Alert Logic creates as you select assets to include in and exclude from your asset group. The tab includes a summary of supported JSON fields and an Expression Editor. Operations professionals can click **EDIT** to edit the expression or create the entire expression manually. The Expression Editor validates your JSON as you type. For more information about available fields, see [Asset Groups (Beta) Expression Reference](asset-groups/schema.md), which includes field descriptions and examples.

## Add a linked asset group

A linked asset group contains two or more asset groups. To add a linked asset group, you enter details about the group, and then you select the asset groups to include.

If you have asset groups for PCI and HIPAA compliance, you might want to create a linked group named Compliance that includes your PCI and HIPAA asset groups.
A linked group updates automatically when assets are added to or removed from a member group.

**To enter details about the asset group:**

1. On the Asset Groups page, click the add icon (![](../Resources/Images/Icons/cdAddPlus.png)), and then click **Linked Asset Group**.
2. Type a descriptive name that easily identifies this asset group in a list—for example, "Compliance."
3. (Optional) Select a criticality rating between 0 and 10 for your linked asset group. 
The value indicates how important it is to protect assets belonging to the group. Alert Logic multiplies the value by the [Threat Risk Index (TRI)](../analyze/TRI-score-factors.md) to obtain a weighted score that accounts for your scale.Suppose the criticality ratings in your organization are Info, Low, Medium, and High. Your team decides to assign values of 0 to 3 to your asset groups to account for this scale. To indicate  an asset group has a Medium criticality in this scenario, your team selects **2**.
4. Type a detailed description for your linked asset group to help you identify it later.
5. Click **SAVE AND CONTINUE**.

**To select assets groups to add to the linked group:**

1. On the Configuration page, select the asset groups that you want to include in your new linked group. You can use the search bar to help you find asset groups.
2. Click the matching rule you want to use for including assets in your linked group:
   * **All Assets in Selected Groups**—Includes every asset that exists in any of the selected asset groups in your linked group
   * **Overlapping Assets Only**—Includes only assets that exist in all of the selected asset groups in your linked group
4. Click **ADD**.

## Manage asset groups

On the Asset Groups page, you can search for, view details about, edit, and delete asset groups.

### Search

You can use the search bar to filter the list of asset groups to include only items that contain specific words or partial words in the asset group name.

### View details

In the list of asset groups, find the asset group whose details you want to view, and then click **View**. Details include the description and criticality rating. You can edit or delete an asset group from the detail view.

### Edit an asset group

You can change the details and configuration for an existing asset group or linked asset group.

To edit  an asset group:

1. In the list of asset groups, find the asset group or linked asset group that you want to edit, click **View**, and then click the **EDIT** icon.
2. Change any of the available settings, and then click **SAVE AND CONTINUE**.
3. Change the asset group configuration as needed, and then click **UPDATE**.

### Delete an asset group

In the list of asset groups, find the asset group or linked asset group that you want to delete, click **View**, and then click the **DELETE** icon.

If you try to delete a group that belongs to one or more linked asset groups, a message indicates the names of the linked groups. If you confirm the deletion, Alert Logic removes the group from the linked groups.

Before you delete a group, be aware that a configuration elsewhere in the Alert Logic console might also use it. Deleting a group can cause a configured asset group such as in an automated response playbook to stop working.
