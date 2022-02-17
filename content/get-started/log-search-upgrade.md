# Log Search Upgrade

Alert Logic now offers an enhanced and improved experience  for  customers  upgrading to the new Search feature. This document is intended to help you adapt from Log Search beta feature to the new Search feature.

The Search experience in the Alert Logic console allows you to perform basic and advanced searches for different data types. The Search feature is flexible for structuring your own search queries or using template, fields, and predefined expressions to help you find and organize  messages most relevant to your investigation. Search also supports variety of data sources required to cover potential threats, discover what log sources are present in an environment, and provide tools for further investigation.

Your new experience includes all of the same capabilities as the current Log Search experience, including new and improved features. To refer to documentation for the current Log Search features and functionality, see [Search: Log Messages](../analyze/log-message-search.md).

## Changes to your Search experience

Alert Logic is now offering two Search mode experiences:    Simple mode and Expert mode. You can alternate between the two modes depending on your needs. Click the drop-down list to alternate between **Expert Mode** and **Simple Mode**.

### Search modes

Simple mode provides a graphical interface that allows you to add or remove conditions and fields, aggregate or add a function to predefined expressions,  and determine sorting and order. Simple mode is optimized for performing common types of search queries. You can  create a query in Simple mode, apply filters and grouping, and then switch to Expert mode to add more logic or complex functions. For more information about Search Simple Mode, see [Search Simple Mode ](../analyze/search/simple-mode.md).

Expert mode allows you to create your own SQL searches  and aggregations. Expert mode allows you create more complex searches, which you can build from Simple mode when you switch. You can also use the Help feature to quickly find and add fields to your query. You can combine search terms using nested logical expressions. You can use many more functions in expert mode such as the following to:

* Add conditional terms to your search
* Use regular expressions to express complicated matching rules, or to extract custom fields from your data
* Access the Alert Logic asset model to search for data based on where it was collected, for example by AWS tag.
* Extract more security value from your data by apply geo-IP lookup and URL decoding functions

You will notice that Expert mode functions and looks similar to the current Log Search experience. For more information about Search Expert Mode, see [Search Expert Mode ](../analyze/search/expert-mode.md).

### Search features

Alert Logic now offers the following new features:

* Schedule search notifications
* Save  searches and schedule searches
* Download search results
* Use search tabs to execute and switch between multiple searches
* Help search fields
* Load saved searches into the query and immediately download search results from the Saved Searches side panel
* Apply settings to your search, such as selecting a timezone
* Support for [File Integrity Monitoring ](../configure/file-integrity-monitoring.md) data

Other capabilities that currently exists and are still supported:

* Narrow search results by date and time range
* Work with messages, including creating manual incidents

For an overview of all the Search features, see [Get Started with Search](search-a.md).

## Search process

You can start a basic query in Simple mode, apply filters and grouping, then switch to Expert mode to add more logic or complex functions.

To create a successful search and maximize the use of the Search page in Simple mode, Alert Logic recommends becoming familiar with the following process:

1. Build your query
2. Refine your search
3. Schedule a search
4. Access your search results

## Build your query

For detailed information on how to structure your queries, see the [Structure Query Language guide](../pdf-files/SQL-dev-guide.pdf). For examples of search queries to find log messages, FIM data, IDS messages, and observations, see [xref example doc].

In Expert mode, the query has five clauses: <kbd>SELECT</kbd>, <kbd>FROM</kbd>, <kbd>WHERE</kbd>, <kbd>ORDER BY</kbd>, and <kbd>LIMIT</kbd>.

* The <kbd>SELECT</kbd> clause describes which fields will be returned with each result, and the order in which they will be returned.
* The <kbd>FROM</kbd> determines what data will be searched, for example <kbd>logmsgs</kbd>, which returns log messages, or <kbd>fimdata</kbd>, which returns  [File Integrity Monitoring ](../configure/file-integrity-monitoring.md) events.
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

From your search results, you can use the [Search Help Query Builder](../analyze/search/help.md). Click **Help** to access the Help side panel which provides a library of fields organized by data types  that you can add to the  search query.

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

After you enter a search, you can save and schedule a search which can serve as template. Click the down arrow (![](../Resources/Images/Icons/arrow-down-icon.png)), and then click **Save and Schedule Search** to get started. For further instructions on how to save and schedule a search, see [Saved and Scheduled Searches](../analyze/search/save-schedule.md#schedule-and-notify).

Click **Saved Searches** to view your recent executed searches and recent schedules searches. From the **Saved Searches** side panel, you can input searches and download search results to a CSV file. To manage your saved searches, click **Managed saved searches** to be redirected to the **Saved Searches** page. To view a list of all your search results from schedules searches, click **See More** to be redirected to the Downloads page.

You can also click the **Saved Searches** tab to view a list of your saved searches, view which scheduled saved searches and saved searches not on a schedule. From the Saved Search tab, you can managed your saved searches, including editing the search query, schedule, tags, and recipients, or adding a schedule to a saved search, and deleting searches. For more information, see [Saved and Scheduled Searches](../analyze/search/save-schedule.md).

## Manage your search results

After you perform a search, you can view the details of messages that appear in the search results. Click a message to:

* View a summary of the message
* View the source properties
* Export the message summary to a CSV file
* Create a manual incident from the message

For more information, see [Manage Search Results Messages](../analyze/search/manage-search-results.md).

### Download search results

If you need to download search results from scheduled searches, you can access search results from the Downloads page.

You can also download results from the Search page. Click **Saved Searches**, and then click the recent search for which you want to download search results. To view a list of all your search results from schedules searches, click **See More** to be redirected to the Downloads page. For more information, see [Downloads](../analyze/search/downloads.md).
