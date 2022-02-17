# Log Search

This document is intended for early-access customers and is continually being updated as the Log Search feature is finalized.

The new Log Search experience in the Alert Logic console is intended to allow you to perform basic and advance searches for different log messages data types that can help you find and organize  messages most relevant to your investigation. The Log Search page is composed of Simple Mode and Expert Mode.

Simple Mode allows you to add or remove conditions and fields, aggregate or add a function to predefined expressions,  and determine sorting and order. For more information about Search Simple Mode, see

Expert Mode allows you to create your own SQL searches  and aggregations. For example, to investigate which users are causing the most failed logins, you can search for log messages that have been parsed as "Windows Login Failed" and then aggregate the search results by “User Name” and “Src Host.” For more information about Search Expert Mode, see

For detailed information on the Structure Query Language, see

The new Log Search experience also allows you to run more than one search at a time, download search results, save and schedule a search, and has help fields that allow you to add and build your query.

To access the Log Search page,  click the menu icon (![](../../Resources/Images/dashboard/menu-icon.png)), and then click ![](../../Resources/Images/dashboard/investigate-icon.png)**Investigate**. Click **Search**.

## Log search data types

You can execute searches for the following data types:

* Log messages
* File Integrity Monitoring (FIM) data
* IDS messages
* Observations

## Create the search query statement

The **WHERE** and **SELECT** fields in the Log Search page allow you to type an SQL-like query statement using available fields and operators. If needed, you can add more search fields to create a search that tests for multiple conditions. As you type a search statement, a warning icon (![](../../Resources/Images/Icons/warning_icon_sql.png)) appears to the left of the search field until the query contains valid syntax. You cannot submit a search with invalid syntax.

For details about creating a complex log message search, see [Create Complex Log Searches](../log-search/complex-log-search.md) and [Examples of Common Log Message Searches](../log-search/log-search-examples.md).

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

For more information, see [Parsed JSON Log Search and Examples](../log-search/log-search-json.md).

## Save  searches

Alert Logic saves your recent executed log searches and allows you to save and schedule any log search for frequent use. You must successfully run the search to be able to save and schedule a search. The Saved Searches feature lists all recent executed searches, and recent scheduled searches. You can also view  scheduled search results or export them to a CSV file. For more information, see [Saved and Schedule Searches](save-schedule.md).

## Download a search query

If you need to share search queries with specific users, or store a search query privately for later use, you can download the search results directly from the Log Search page, from the recent executed search list, or from the Downloads page. A download search query contains query details saved as a JSON file for storage and for ease of sharing electronically.

## Help search fields and templates

The Alert Logic console provides a library of search templates and fields to help you create effective log searches that address the security concerns and goals for your organization. You can then save your searches for later use with the Save Search feature. For more information, see [Search Help Templates](templates.md).

## Schedule search notifications

You can schedule a weekly or monthly log searches for your different data types, and be notified when the search is complete. The search and notification can help you keep records and track any changes. For more information, see [ Schedule Search Notification](schedule-searches.md).

## Work with log messages

After you perform a log message search, you can view the details of log messages that appear in the search results. Click a message to:

* View a summary of the log message
* View the log source properties
* Bookmark a message, flagging it for investigation until you run another search
* Add filters or tokens to the query ran previously to refine results
* Export the log message summary to a CSV file
* Create a manual incident from the message

For more information, see [Work with Log Messages](../log-search/analyze-log-messages.md).
