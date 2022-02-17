# Incidents Upgrade 

Alert Logic is upgrading customers to the new Alert Logic Incidents page with an enhanced and improved experience   to maximize your ability to manage incidents.  This upgrade enhances your experience, but still offers the same features and capabilities as the existing Incidents page.

The upgraded Incidents page continues to display information about incidents, how to use that information to manage and close incidents, and actionable steps to secure your environments.  If you want a reminder of the existing Incident features, see [Incidents](../analyze/incidents.md).

As you familiarize yourself with the new experience, you can switch between the updated Incidents page and the existing Incidents page by using the toggle icon (![](../Resources/Images/incidents/toggle.png)) on the upper-right side of the page.

## Changes to the Incidents page

Your new experience includes all of the same capabilities as the existing Incidents page, including improved functionality and features. In the new Incidents experience, you can see relevant and important information immediately, at a glance, and with fewer clicks. You can also customize your page view to see information that is important to you and your organization. This flexibility allows you to get to the relevant investigation and security outcome faster and more efficiently.

Refer to the table below for changes and improvements to current features:

| Feature | Change |
| [Incident list](#Incident) | Table-style list that allows you to add, remove, and rearrange columns of information |
| [Incident filters](#Incident2) | Ability to select multiple filters in a filter set |
| [Incident preview](#Incident3) | Options to automatically preview summary information when you hover over an incident or hide the preview |
| [Incident download](#Incident4) | Ability to bulk download 100 incidents at a time to a CSV file |
| [Log Review incident upgrade](#inciden) | Machine-learning enhanced log review incidents |
| [Investigation Report](#investigationReport) | Combined investigation and recommendation view with a topology diagram |
| Playbook | A new feature that allows you to run a playbook on an incident to respond to it automatically |
| [Evidence and grouping ](#Evidence) | A separate Evidence tab that includes groupings of related activity and  an evidence illustration |
| [Activity grouping](#Activity) | Activity, including observations, related to an incident is grouped for an improved view in the Evidence tab |
| [Analytic Details](#AnalyticDetails) | A tab that includes details for the underlying security content logic for defining the activity as an incident. |

## Incident list

The incident list is now formatted as a table-style list that allows you to show several columns of relevant information. You can adjust the column size, remove and add columns, and drag and drop columns into the order you want.  You can also sort some columns by date or alphabetical order. Click the sort icon (![](../Resources/Images/incidents/sort.png)) on the left of the column name. The default columns shown are the following:

* Attacker
* Date
* Deployment
* Incident ID
* Status
* Summary
* Target
* Threat Level

Other columns you can add to your incident list are the following:

* Account
* Classification
* Correlation Name
* Detection Source
* Incident Note Count

You can remove and add columns to show only columns of information that are important to you. Click **Choose Columns** to see all of the available columns, and then select check boxes you want to include in or clear check boxes you want to exclude from your list. Click the reset icon (![](../Resources/Images/incidents/reset.png)) to revert to the default column view, including default columns, sorting, and size.

### Incident filters

You can select multiple filters at a time to create a specific combination to find results unique to your security needs at the time. Selecting multiple filters allows you to see more than one incident status, threat level, incident classification, deployment, and other available criteria.

**To apply multiple filters to the incident list**:

1. Click on a filter group on the left panel. For example, click **Open**, under **Status**.
2. Click **Show More** to see all of the available filters in this filter set.
3. Select all of the filters you want to see, or clear filters you do not want to see.

### Incident preview

You can preview summary information automatically when you hover over an incident or hide the preview for all. The preview panel displays the following information:

* Incident summary
* Date
* Account
* Attacker IP address
* Classification
* Detection source
* Incident ID
* Status
* Target
* Threat level

To hide the preview, click the hide icon (![](../Resources/Images/incidents/arrow_24x28.png)) to collapse the preview panel. If you want to see the preview again, click the show icon (![](../Resources/Images/incidents/arrow-expand_23x27.png)).

### Incident download

You can download incident data to a CSV file. The CSV file contains all of the information in your current incident list view with the applied filters and date range. Multiple options are available to export data to best suit how you want to analyze your incidents. You can download incident data  for all incidents, for only incidents you select, or  for all the incidents mapped in the filters you applied and for the date range you selected.  These options allow you to control how many incidents you want to include and how you want to separate  the data.

**To download data for all incidents that matches the filters you selected**:

1. Click the download icon (![](../Resources/Images/incidents/download-all.png)) at the top of the incident list.
Downloading data for all incidents in your applied filters and date range can return a large number of incident results. This can cause a longer downloading period and a larger CSV file.
2. Click **DOWNLOAD**.
3. Wait for the download to complete.

Your results are downloaded to a compressed folder that contains the zip CSV file.

**To download data for only certain incidents**:

1. Select the check boxes next to the incidents for the data you want to download.
2. In the blue bar at the bottom of the page, click ![](../Resources/Images/incidents/download-all.png)**EXPORT**.

Your results are downloaded to a CSV file.

**To download data for 100 incidents**:

1. Select the check box at the top of the incident list to select all of the incidents visible on the page.
2. To download 100 incidents, click **SELECT 100 INCIDENTS WITH THE APPLIED FILTERS AND DATE RANGE**.
3. In the blue bar at the bottom of the page, click ![](../Resources/Images/incidents/download-all.png)**EXPORT**.
4. Your results are downloaded to a CSV file.

As in the existing experience, the Incidents page continues to support  bulk actions  to update, snooze, or close multiple incidents, alongside exporting them.

## Log Review incident upgrade

An upgrade to Log Review incidents  delivers a higher level of security value to you with new machine learning algorithms, Machine Learning Log Review. The algorithms can automatically detect many log-based anomaly types based on unique patterns and trends learned from your organization and then create an incident. Alert Logic also includes observations in the Evidence tab of the Investigation Report based on the algorithms. For more information, see [Machine Learning Log Review Upgrade](../analyze/log-review-upgrade.md).

## Investigation Report

The Investigation Report consists of the sections Topology, Attack Summary,  and Recommended Course of Action in the **Investigation and Recommendation** tab. To access the **Investigation and Recommendation** tab, click on the incident you want to see from the [Incident list](#Incident). The Evidence details are in a separate tab, the Evidence tab, which includes a table-style list view for evidence. The Audit Log and Notification History are also on this page as in the existing Incidents experience.

For Log Review incidents, the **Investigation and Recommendation** tab also includes the Overview of Log Alerts and Anomalies section. The Overview of Log Alerts and Anomalies section is a briefing of the evidence.  You can review the evidence in more detail from the **Evidence** tab, which includes a table-style list view for evidence.

### Evidence and grouping 

The Evidence tab groups related information, including events, correspondence, and activity that culminated into an incident, into one drop-down section that you can collapse and expand. Click the drop-down arrow (![](../Resources/Images/incidents/drop-down-arrow.png)) to see all of the evidence listed under an event.

If there are more than 100 evidences for an activity related to an incident, the additional evidence will automatically load. After the additional evidence loads, click **REFRESH** to see the new evidence. This will refresh the page to show the following 100 (or remaining) evidence.

You can use the search bar to search for keywords to find specific information. Click **Download All** to download all the evidence for all information in this incident, including events, correspondence and activity.

#### Activity grouping

You can also find other relevant information nested under each activity, and these include log messages for Log Management detection sources and observations for Web Log Analytics (WLA) and Log Review detection sources. Alert Logic notes these anomalies as relevant security information that can demonstrate security value. Click the drop-down arrow (![](../Resources/Images/incidents/drop-down-arrow.png)) next to an anomaly to see more details.

The table-style list that supports the activity under an event functions the same way as the new incident list. You can select which columns to see, adjust the column size, remove and add columns, and drag and drop columns into the order you want. This flexibility allows you to easily navigate through information to determine how to address incidents more quickly.

For Log Review incidents associated with anomaly or rule-based findings, you can download a CSV file of the observations or facts for an event. The aggregator summary section groups observation findings and evidence for different message types which allows you to download evidence for specific aggregator types to a CSV file for compliance needs. The file contains information fields from observations or facts from all of the log messages associated with the anomaly findings.

To download observation findings, click the drop-down arrow (![](../Resources/Images/incidents/drop-down-arrow.png)) next to the event grouping to expand details, and then click **Download Observations**. To download additional data associated with the observations, click **Download Observation Evidence**. The CSV file for observations contains the following fields:

* Summary
* Date
* Description
* Severity
* Customer name
* Caller user
* Log source
* Maximum time
* Message type
* Minimum time
* Terminal time
* Total messages
* Aggregator	entity type
* User

You can investigate further and download the facts of an observation event under the Log Review event grouping. To download facts of an observation event, click the drop-down arrow (![](../Resources/Images/incidents/drop-down-arrow.png)) to expand the details of an observation, and then click **Download Facts**. The CSV file for the observation facts includes the following fields:

* Description
* Date
* Message
* User
* Facility and priority
* Syslog fields PID
* UID
* User name

### Analytic Details

The analytic details tab includes details for the underlying security content logic for defining the activity as an incident. To learn more about analytics, see [About Analytics in the Threat Intelligence Center](../analyze/threat-intel-center/about-analytics-content.md).

### About incident evolution

Incident evolution occurs when Alert Logic receives additional events associated with the incident, and then creates an incident of a higher threat rating. If an incident evolves, the Alert Logic Security Operations Center (SOC) sends a new incident notification.
