# Work with Log Messages

Alert Logic is offering an improved version of the Log Search feature. To learn more about this feature, see [Get Started with Search](../../get-started/search-a.md).

After you perform a log message search, you can view the details of log messages that appear in the search results. Click a message to:

* View a summary of the log message
* View the log source properties
* Bookmark a message, flagging it for investigation until you run another search
* Add filters or tokens to the query ran previously to refine results
* Export the log message summary to a CSV file
* Create a manual incident from the message

## Open a log message

Select a log message, and then click **Open** to view the details of the selected log message in a separate browser tab. The details page for a selected log message displays additional information about the log message, log source properties, and message fields. You can use this information to further refine your log search, export the information about this log message to a CSV file, or create an incident.

## Export log messages

Multiple views within log search allow you to export either a list of search results, or details of a specific search to a CSV file.

* If you select one or more search results in the list, you can click the export icon (![](../../Resources/Images/Icons/download.png)) in the blue bar on the lower right of your screen to export selected log search results to a .CSV file.
* If you select the **Select All** check box, and then click the export icon (![](../../Resources/Images/Icons/download.png)), the Alert Logic console prompts you to create a saved, scheduled search.
* If you open a log message to view details in a separate browser tab,  you can click the export icon (![](../../Resources/Images/Icons/download.png)) to export selected log search details to a .CSV file.

## Create an incident

The Log Search page allows you to create a manual incident from log messages from either the list of search results or from an open log message.

**To create an incident from the search results:**

1. If you select one or more search results in the list, you can click the create incident icon ( ![](../../Resources/Images/Icons/incident-create.png)) in the blue bar on the lower right of your screen to manually create an incident from the selected log messages.
2. In the Create Incident slideout panel, provide the requested information.
3. Click **CREATE**.

**To create an incident from an open log message:**

1. From the list of search results, select a log message.
2. Click **Open** to open the log message in a separate tab.
3. In the upper right of the open log message, click the create incident icon ( ![](../../Resources/Images/Icons/incident-create.png)).
4. In the Create Incident slideout panel, provide the requested information.
5. Click **CREATE**.

## Bookmark log messages

The bookmark feature allows you to specify one or more log messages you want to investigate, and then display only those log messages in the list of search results.

    Bookmarks appear only for the current search.     
To bookmark a single log message entry:

1. Click **Open**.
2. Click the bookmark icon (![](../../Resources/Images/Icons/bookmark.png)).

**To bookmark multiple log message entries:**

1. Select the check box to the left of each log message you want to bookmark.
2. In the blue bar on the lower right of your screen, click the bookmark icon (![](../../Resources/Images/Icons/bookmark.png)).

After you bookmark log messages, you can click the bookmark icon (![](../../Resources/Images/Icons/bookmark.png)) above the search results to display only bookmarked log messages in the results list.
