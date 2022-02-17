# Search Expert Mode 

The Search experience in the Alert Logic console is intended to allow you to perform basic in Simple mode and advance searches in Expert mode for different  data types.  Simple mode allows you to add or remove conditions and fields, aggregate or add a function to predefined expressions,  and determine sorting and order. For more information about Search Simple Mode, see [Search Simple Mode ](simple-mode.md).

Expert mode allows you to create your own SQL searches and aggregations. You can combine search terms using nested logical expressions. Functions available in expert mode include some of the following:

* Add conditional terms to your search
* Use regular expressions to express complicated matching rules, or to extract custom fields from your data
* Access the Alert Logic asset model to search for data based on where it was collected, for example by AWS tag.
* Extract more security value from your data by apply geo-IP lookup and URL decoding functions

Search supports variety of data sources  that help you uncover  potential threats, discover what data sources are present in an environment, and provide tools for further investigation.

**To access the Search page**:

1. Click the menu icon (![](../../Resources/Images/dashboard/menu-icon.png)), and then click ![](../../Resources/Images/dashboard/investigate-icon.png)**Investigate**.
2. Click **Search**, and then click the **Search** tab.
3. Click the drop-down list, and select **Expert Mode**.

## Search process

The Search page is composed of Simple mode and Expert mode. Simple mode allows you to add or remove conditions and fields, aggregate or add a function to predefined expressions,  and determine sorting and order. Expert mode allows you to create your own SQL searches  and aggregations.  For more information about Search Simple Mode, see [Search Simple Mode ](simple-mode.md).

You can start a complex query in Simple mode, apply filters and grouping, then switch to Expert mode to add more logic or complex functions.

To create a successful search and maximize the use of the Search page in Expert mode, Alert Logic recommends becoming familiar with the following process:

1. Build your query
2. Refine your search
3. Schedule a search
4. Access your search results

For detailed information on how to structure your queries, see the [Structure Query Language guide](../../pdf-files/SQL-dev-guide.pdf).

### Search features in Expert mode

From the Alert Logic console Search page, you can use the following features in both modes:

* Narrow search results by date and time range
* Schedule search notifications
* Save  searches and schedule searches
* Download search results
* Work with log messages
* Help search fields

Other capabilities include that exists include:

* Apply settings to your search, such as selecting a timezone
* Use search tabs to execute and switch between multiple searches.
* Load saved searches into the query and immediately download search results from the Saved Searches side panel

You can execute searches for the following data types in Simple mode:

* Log messages
* File Integrity Monitoring (FIM) data
* IDS messages
* Observations

For an overview of all the Search features, see [Get Started with Search](../../get-started/search-a.md).

## Build your query

For detailed information on how to structure your queries, see the [Structure Query Language guide](../../pdf-files/SQL-dev-guide.pdf). For examples of search queries to find log messages, FIM data, IDS messages, and observations, see [xref example doc].

The expert mode query has five clauses: <kbd>SELECT</kbd>, <kbd>FROM</kbd>, <kbd>WHERE</kbd>, <kbd>ORDER BY</kbd>, and <kbd>LIMIT</kbd>.

* The <kbd>SELECT</kbd> clause describes which fields will be returned with each result, and the order in which they will be returned.
* The <kbd>FROM</kbd> determines what data will be searched, for example <kbd>logmsgs</kbd>, which returns log messages, or <kbd>fimdata</kbd>, which returns  [File Integrity Monitoring ](../../configure/file-integrity-monitoring.md) events.
* The <kbd>WHERE</kbd> clause determines which log messages will be returned.
* The <kbd>ORDER BY</kbd> clause requests for the results to be sorted by the timestamp in descending order (newest to oldest).
* The <kbd>LIMIT</kbd> clause is included, which limits the results to the first 1000 matching records.

For aliases and field names, you must use double quotes, and for a strings, you must use single quotes. Click **SEARCH** to execute your search when you have entered your query.

### Log message example

Below is an example of a search query to find log messages in a specific deployment.

| SELECT time_recv, asset.dict.asset.deployment.name AS "Deployment Name", message |
| FROM logmsgs |
| WHERE message CONTAINS 'admin@example.com' |
| ORDER BY time_recv DESC |
| LIMIT 1000 |

The <kbd>SELECT</kbd> clause in the example has the three following fields that determine what will be returned with each result, and the order in which they will be returned:

* <kbd>time_recv</kbd> — the timestamp of a log message
* <kbd>asset.dict.asset.deployment.name</kbd> — the name of the deployment that collected the log message which is available in the asset dictionary. To make that clearer in the results, the field is described with the alias <kbd>“Deployment Name”</kbd>.
* <kbd>message</kbd> — the log message itself

The <kbd>FROM</kbd> is the <kbd>logmsgs</kbd> type which considers all log messages.

The <kbd>WHERE</kbd> clause determines which log messages will be returned, namely those where the body of the message includes the email address <kbd>admin@example.com</kbd> anywhere.

The <kbd>ORDER BY</kbd> clause requests for the results to be sorted by the timesamp in descending order (newest to oldest).

The <kbd>LIMIT</kbd> clause is included, which limits the results to the first 1000 matching records.

In the example, the alias Deployment Name is specified with double quotes <kbd>("Deployment Name"</kbd>), while the string <kbd>admin@example.com</kbd> is specified with single quotes (<kbd>'admin@example.com'</kbd>).

### FIM data example

Below is an example of a complex search query to find FIM events with specific information such as time, asset name, file path, size, and host.

| SELECT |
| ts AS "Event Time", |
| asset.dict.asset.host.name AS "Asset Name", |
| event_type AS "Event Type", |
| file_type AS "File Type", |
| path AS "File Path", |
| file_name AS "File Name", |
| file_size AS "File Size", |
| sha1_hash AS "SHA1", |
| asset.dict.asset.host.key AS "Asset Key", |
| asset.dict.asset.deployment.name AS "Deployment Name" |
| FROM fimdata |
| WHERE STARTS_WITH(path, '/etc') OR |
| (event_type = 'delete' AND NOT ENDS_WITH(file_name, '.tmp')) |
| -- all changes to files in /etc and all deletions except .tmp files |
| ORDER BY "Event Time" DESC |
|  |

The example query has more terms, but it also includes <kbd>SELECT</kbd>, <kbd>FROM</kbd>, <kbd>WHERE</kbd>, and <kbd>ORDER BY</kbd> clauses as the log search query. The <kbd>fimdata</kbd> data type includes all File Integrity Monitoring events, which collected separately from log messages. The <kbd>WHERE</kbd> clause includes several functions which narrow down the records that will be returned, and a comment (starting with --) which explains what they do.

## Refining your search

From your search results, you can use the [Search Help Query Builder](help.md). Click **Help** to access the Help side panel which provides a library of fields organized by data types  that you can add to the  search query.

You can further add a date and time range filter to any search you create. Select from the following ranges:

* Last hour (default)
* Last 6 hours
* Last 12 hours
* Last 24 hours
* Last 7 days
* Last 30 days

You can also use the calendar to create a custom date and time range.

    The Alert Logic console displays time in your local time zone.     
You are able to refine and execute searches as many times as necessary. You can execute more than one search at the same time when you need to run multiple searches at one time. You can see the tab of your search at the top of the Search page, and switch between search tabs.

You can configure settings to apply to all of your search results. Click **Settings** on the search page. You have the option to automatically transform the timestamps in data sources to your time zone.

## Scheduling a search

After you enter a search, you can save and schedule a search which can serve as template. Click the down arrow (![](../../Resources/Images/Icons/arrow-down-icon.png)), and then click **Save and Schedule Search** to get started. For further instructions on how to save and schedule a search, see [Saved and Scheduled Searches](save-schedule.md#schedule-and-notify).

Click **Saved Searches** to view your recent executed searches and recent schedules searches. From the **Saved Searches** side panel, you can input searches and download search results to a CSV file. To manage your saved searches, click **Managed saved searches** to be redirected to the **Saved Searches** page. To view a list of all your search results from schedules searches, click **See More** to be redirected to the Downloads page.

You can also click the **Saved Searches** tab to view a list of your saved searches, view which scheduled saved searches and saved searches not on a schedule. From the Saved Search tab, you can managed your saved searches, including editing the search query, schedule, tags, and recipients, or adding a schedule to a saved search, and deleting searches. For more information, see [Saved and Scheduled Searches](save-schedule.md).

## Manage your search results

After you perform a search, you can view the details of messages that appear in the search results. Click a message to:

* View a summary of the message
* View the source properties
* Add filters or tokens to the search query  to refine results
* Export the message summary to a CSV file
* Create a manual incident from the message

For more information, see [Manage Search Results Messages](manage-search-results.md).

### Download search results

If you need to download search results from scheduled searches, you can access search results from the Downloads page.

You can also download results from the Search page. Click **Saved Searches**, and then click the recent search for which you want to download search results. To view a list of all your search results from schedules searches, click **See More** to be redirected to the Downloads page. For more information, see [Downloads](downloads.md).
