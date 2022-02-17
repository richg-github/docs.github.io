# Search: Log Messages

Alert Logic is offering an improved version of the Log Search feature. To learn more about this feature, see [Get Started with Search](../get-started/search-a.md).

The  Log Search feature in the Alert Logic console allows you to create SQL-like searches  and aggregations that can help you find and organize  log messages most relevant to your investigation. For example, to investigate which users are causing the most failed logins, you can search for log messages that have been parsed as "Windows Login Failed" and then aggregate the search results by “User Name” and “Src Host.”

## Access the Log Search feature

To access the Log Search feature, from the navigation menu, click ![](../Resources/Images/dashboard/investigate-icon.png)**Investigate**, and then click **Search**.

## Create the search query statement

The **WHERE** and **SELECT** fields in the Log Search page allow you to type an SQL-like query statement using available fields and operators. If needed, you can add more search fields to create a search that tests for multiple conditions. As you type a search statement, a warning icon (![](../Resources/Images/Icons/warning_icon_sql.png)) appears to the left of the search field until the query contains valid syntax. You cannot submit a search with invalid syntax.

For details about creating a complex log message search, see [Create Complex Log Searches](log-search/complex-log-search.md) and [Examples of Common Log Message Searches](log-search/log-search-examples.md).

## Narrow log search results by date and time range

You can add a date and time range filter to any log search you create. Select from the following ranges:

* Last hour (default)
* Last 6 hours
* Last 12 hours
* Last 24 hours
* Last 7 days
* Last 30 days

You can also use the calendar to create a custom date and time range.

    The Alert Logic console displays time in your local time zone.     ## Search progress and search cancellation

The Log Search feature displays a search progress bar during log searches. You can click **CANCEL** to stop any search in progress.

## Search a parsed JSON log 

Parsed JSON searching is built into the Log Search feature and allows you to search on fields from any JSON log. You can use JSONPath queries, parsed token names, or a combination of both to aggregate and filter log messages received in parsed JSON format.

For more information, see [Parsed JSON Log Search and Examples](log-search/log-search-json.md).

## Save and schedule log searches

You can save and schedule any log search for frequent use. To ensure every saved search runs correctly, the Alert Logic console does not allow you to save a search until you enter at least one valid search statement in the search bar and successfully run the search. The Saved Searches feature lists all saved searches in groups created by users in your customer account, and you can run and edit those searches. You can also view  scheduled search results or export them to a CSV file.

For more information, see [Create Saved and Scheduled Log Searches](log-search/save-schedule.md).

## Import and export a search query

If you need to share search queries with specific users, or store a search query privately for later use, you can use the Import and Export Search Query feature. An exported search query contains query details saved as a JSON file for storage and for ease of sharing electronically.

For more information, see [Import and Export Search Queries](log-search/import-export-search-query.md).

## Create and manage search templates

The Alert Logic console  provides a library of search templates to help you create effective log searches that address the security concerns and goals for your organization. The Alert Logic console allows user accounts with the Administrator role to create and manage search templates to supplement the template libraries for their customer accounts and the customer accounts they manage.

You can create a library of search templates  from effective log searches to help you address specific security concerns and goals for your organization. The Alert Logic console allows user accounts with the Administrator role to create and manage search templates for their customer accounts and the customer accounts they manage.

For more information, see [Create and Manage Search Templates](log-search/templates.md).

## Work with log messages

After you perform a log message search, you can view the details of log messages that appear in the search results. Click a message to:

* View a summary of the log message
* View the log source properties
* Bookmark a message, flagging it for investigation until you run another search
* Add filters or tokens to the query ran previously to refine results
* Export the log message summary to a CSV file
* Create a manual incident from the message

For more information, see [Work with Log Messages](log-search/analyze-log-messages.md).
