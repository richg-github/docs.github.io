# Threat Intelligence Center (Beta)

    This document is intended for early-access customers, and it is updated as Threat Intelligence Center features are enhanced.     
The Threat Intelligence Center provides insight into Alert Logic content coverage by displaying  security content details in an interactive table.  Use the Threat Intelligence Center to validate Alert Logic threat coverage, learn about analytics content, investigate content configuration requirements, and source information for automated response.

    Information in the Threat Intelligence Center is not specific to your environment. For real-time threat response in your environment, see [Incidents](../incidents.md). For automating response actions for real-time threats in your environment, see [Automated Response (Beta)](../../respond/automated-response-new.md).    
To access the Threat Intelligence Center, click the menu icon (![](../../Resources/Images/dashboard/menu-icon.png)), and then click ![](../../Resources/Images/dashboard/investigate-icon.png)**Investigate**. Click **Threat Intel Center**.

## About the Threat Intelligence Center

You can use the Threat Intelligence Center to validate threat coverage, learn about analytics content, investigate content configuration requirements, and source information for automated response.

### Validate threat coverage

The Threat Intelligence Center provides details for content covered by Alert Logic, not content that is necessarily covered in your environment. Use the  content table  to validate that specific threats are covered by Alert Logic. For more information about how to control filters and viewing specific threats, see [Threat Intelligence Center Features](#Threat).

### Learn about analytics content

An Alert Logic analytic is a rule-based or machine learning algorithm that helps process activity in your environment. An Alert Logic analytic refers to content  that uses telemetry data to evaluate activity to produce incidents or observations. An analytic can help process one or more specific threats, and threats can require one or more analytic to process. The Threat Intelligence Center provides a tabular list for the properties of each analytic. For more information about property definitions, use cases, and examples, see [About Analytics in the Threat Intelligence Center](about-analytics-content.md#content-analytics).

###  Investigate content configuration requirements

You can  use the Threat Intelligence Center to verify that you have configured the collection sources required to detect specific threats in your deployments. You can find an analytic designed to evaluate a specific type of activity in the Threat Intelligence Center and check the telemetry property to see what data is required by the analytic.

For example, you may find an analytic that uses Log telemetry to evaluate threat activity, which indicates that you need to have the collection configured for specific log sources on your assets for the analytic to evaluate the activity as an incident or observation. For more information on configuring specific log sources, see [Log Sources](../../deploy/log-sources.md) and [Application Registry](../../configure/application-registry.md).### Source information for Automated Response

You can use the Threat Intelligence Center to   source information for [Automated Response (Beta)](../../respond/automated-response-new.md). Use the details provided in the [Possible Response Actions](about-analytics-content.md#possible-response-actions) property of an analytic to determine which response actions can be configured for an incident, when the analytic produces one. Use the details in the [Response Action Parameters ](about-analytics-content.md#response-action-parameters) property to determine which incident objects require response action on.

For example, an analytic may have a possible response action of "Block" and a response action parameter of "attacker." In automated response, you can design a playbook for when the analytic generates an incident. For this incident, a possible [Playbook task](../../respond/automated-response-new.md#Playbooktasks) would be to block the attacker IP.
Use the other content properties to determine analytic incident properties to use as triggers for automated response.   For more information on creating triggers for automated response, see [automated response-create a playbook].

## Threat Intelligence Center Features

You can use filters and search to display specific content. Use the content table and side bar preview to learn about each piece of content.

For information about each content property, see [About Analytics in the Threat Intelligence Center](about-analytics-content.md#content-analytics).

### Search

You can use the search bar to filter the list to include only items that contain specific strings. Searches must only include alphanumeric, forward slash, period, colon, underscore, and hyphen characters.

### Analytics filter panel

By default, no filters are selected. You can apply filters to narrow the content shown in the  table. Use the side bar on the left to choose the filters.

You can only choose one property value for each filter. Click the selected property value again to remove the filter.

You can apply the following filters to the analytics  table:

* Visibility
* Threat Level
* Telemetry
* Possible Response Actions
* Threat Classification
* Log Source
* CVE
* CWE
* MITRE Tactic
* MITRE Technique
* MITRE Sub-Technique
* Added

To hide the panel, click the hide panel button (![](../../Resources/Images/threat-intel-center/hide-show-left-arrow.png)). To show the panel, click the show panel button (![](../../Resources/Images/threat-intel-center/hide-show-right-arrow.png)).

### Content Table

By default, name, summary, threat level,  telemetry, log source, and signatures properties are shown as columns. You can choose which columns are shown, sort by property, and change the column order and width. Columns shown, order, width preferences are preserved in session and across sessions in the same browser.

To choose columns shown:

Click the ![](../../Resources/Images/threat-intel-center/choose-columns.png)**Choose Columns** drop-down menu, and then select the check boxes for the content properties that you would like to show as columns.

You can choose the following columns to be shown:

* CVE
* CWE
* Description
* Log Message Types
* Log Source
* Name
* Recommendations
* Possible Response Actions
* Response Action Parameters
* Signatures
* Summary
* Technology
* Telemetry
* Threat Classification
* Threat Level
* Visibility

You can reset to default columns by clicking the refresh arrow (![](../../Resources/Images/threat-intel-center/refresh-default.png)) next to the ![](../../Resources/Images/threat-intel-center/choose-columns.png)**Choose Columns** drop-down menu.

**To change column order**:

By default, columns are displayed in the order that you chose them. To reorder columns, click the column header and drag it to a new position in the table.

**To change column width**:

To change column width, click between two columns and then drag the columns to the desired width. To change default column width, click ![](../../Resources/Images/threat-intel-center/column-width.png), and drag to the desired width.

**To sort by a property**:

Click the arrow next to the column  heading text to sort the table by a property.

###   Preview panel

Hover over an analytic in the content table to view details about select properties in the right side panel.

Preview panel display properties are:

* Name
* Summary
* Visibility
* Threat Level
* Telemetry
* Log Source
* Log Message Types
* Signatures
* Possible Response Actions
* Response Action Parameters
* Technology
* Confidence
* Log Query
* CVE
* CWE
* MITRE Tactic
* MITRE Technique
* MITRE Sub-Technique
* Threat Classification

To hide the panel, click the hide panel button (![](../../Resources/Images/threat-intel-center/hide-show-left-arrow.png)). To show the panel, click the show panel button (![](../../Resources/Images/threat-intel-center/hide-show-right-arrow.png)).

### Export the content table

You can export the content table with the filters and columns you have set. Click the box next to the analytic(s) you would like to download as a CSV, and then click **Export**.

![](../../Resources/Images/threat-intel-center/export-list-2.gif)

## Analytic Details Page

Click on an a row in the table to view the full details for all properties of the selected analytic.

The Analytic Details page provides full details for every property of an analytic. For more information about each property, see [About Analytics in the Threat Intelligence Center](about-analytics-content.md#content-analytics).
