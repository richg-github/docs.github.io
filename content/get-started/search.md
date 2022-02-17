# Get Started with Search

The Search experience in the Alert Logic console is intended to allows you to perform basic and advanced searches for different data types. The Search feature is flexible for structuring advanced search queries, and using fields and predefined expressions to help you find and organize  messages most relevant to your investigation. Search now supports a variety of data sources that help you uncover  potential threats, discover what data sources are present in an environment, and provide tools for further investigation further with the provided tools.

For example, you can search for messages that have been parsed as "Windows Login Failed,", and then aggregate the search results by “User Name” and “Src Host” to investigate which users are causing the most failed logins. You can then export and share the results, save and schedule the search, or create an incident  from the selected results in the [Incidents](../incidents.md) page.

To access the  Search page,  click the menu icon (![](../Resources/Images/dashboard/menu-icon.png)), and then click ![](../Resources/Images/dashboard/investigate-icon.png)**Investigate**. Click **Search**, and then click the **Search** tab.

## About Search Modes

You can search in   Simple mode and Expert mode. Click the drop-down list to alternate between **Expert Mode** and **Simple Mode**.

### Simple mode

Simple mode provides a graphical interface that allows you to add or remove conditions and fields, aggregate or add a function to predefined expressions,  and determine sorting and order. Simple mode is optimized for performing common types of search queries. You can  create a query in Simple mode, apply filters and grouping, and then switch to Expert mode to add more logic or complex functions. For more information about Search Simple Mode, see [Search Simple Mode ](../analyze/search/simple-mode.md).

### Expert mode

Expert mode allows you to create your own SQL searches  and aggregations. Expert mode allows you create more complex searches, which you can build from Simple mode when you switch. You can also use the Help feature to quickly find and add fields to your query. You can combine search terms using nested logical expressions. You can use many more functions in expert mode such as the following to:

* Add conditional terms to your search
* Use regular expressions to express complicated matching rules, or to extract custom fields from your data
* Access the Alert Logic asset model to search for data based on where it was collected, for example by AWS tag.
* Extract more security value from your data by apply geo-IP lookup and URL decoding functions

For more information about Search Expert Mode, see [Search Expert Mode ](../analyze/search/expert-mode.md).

## Search data types and examples

You can execute searches for the following data types in both Simple Mmode and Expert Mmode in the Search tab:

* Log messages
* File Integrity Monitoring (FIM) data
* IDS messages
* Observations

For detailed information on how to structure your queries, see the [Structure Query Language guide](../../pdf-files/SQL-dev-guide.pdf). For examples of search queries to find log messages, FIM data, IDS messages, and observations, see [xref example doc].

### Log message example

Below is an example of a search query to find log messages in a specific deployment.

| SELECT time_recv, asset.dict.asset.deployment.name AS "Deployment Name", message |
| FROM logmsgs |
| WHERE message CONTAINS 'admin@example.com' |
| ORDER BY time_recv DESC |
| LIMIT 1000 |

This expert mode query has five clauses: <kbd>SELECT</kbd>, <kbd>FROM</kbd>, <kbd>WHERE</kbd>, <kbd>ORDER BY</kbd>, and <kbd>LIMIT</kbd>.

The <kbd>SELECT</kbd> clause describes which fields will be returned with each result, and the order in which they will be returned. In the example, the three fields are the following:

* <kbd>time_recv</kbd> — the timestamp of a log message
* <kbd>asset.dict.asset.deployment.name</kbd> — the name of the deployment that collected the log message which is available in the asset dictionary. To make that clearer in the results, the field is described with the alias <kbd>“Deployment Name”</kbd>.
* <kbd>message</kbd> — the log message itself

The <kbd>FROM</kbd> determines what data will be searched, and in the example, the <kbd>logmsgs</kbd> type considers all log messages.

The <kbd>WHERE</kbd> clause determines which log messages will be returned, namely those where the body of the message includes the email address <kbd>admin@example.com</kbd> anywhere.

The <kbd>ORDER BY</kbd> clause requests for the results to be sorted by the timesamp in descending order (newest to oldest).

The <kbd>LIMIT</kbd> clause is included, which limits the results to the first 1000 matching records.

You must use double quotes for field names and aliases, and single quotes for strings. In the example, the alias Deployment Name is specified with double quotes <kbd>("Deployment Name"</kbd>), while the string <kbd>admin@example.com</kbd> is specified with single quotes (<kbd>'admin@example.com'</kbd>).

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

### IDS message example

| SELECT ts, ts_us, event_id, sig_id, ip_src, srcport, ip_dst, dstport, ip_proxy, ip_proxy_client, proto, class, priority, payload |
| FROM idsmsgs |
| WHERE EXISTS (ts) |
| ORDER BY ts DESC |
| LIMIT 10000 |

### Observation example

| SELECT ts, start_ts, end_ts, class, subclass, path, severity, keys, properties |
| FROM observation |
| WHERE EXISTS (ts) |
| ORDER BY ts DESC |

## Search Features

From the Alert Logic console Search page, you can use the following features in both modes:

* [Narrow search results by date and time range](#Narrow)
* [Schedule search notifications](#Schedule)
* [Saved  searches and schedule searches](#Saved)
* [Download search results](#Download)
* [Work with messages](#Work)

In Expert mode, you can use the [Help search fields](#Help) to search for fields  that you can add to the search query.

Other capabilities include that exists in both modes include:

* Apply settings to your search, such as selecting a timezone
* Use search tabs to execute and switch between multiple searches.
* Load saved searches into the query and immediately download search results from the Saved Searches side panel

### Narrow search results by date and time range

You can add a date and time range filter to any search you create. Select from the following ranges:

* Last hour (default)
* Last 6 hours
* Last 12 hours
* Last 24 hours
* Last 7 days
* Last 30 days

You can also use the calendar to create a custom date and time range.

    The Alert Logic console displays time in your local time zone.     ### Saved  searches and schedule searches

You can save and schedule your searches  for repeated frequent and later use. After you enter a search, you can save and schedule a search which is shared with others users in your account. Click the down arrow (![](../Resources/Images/Icons/arrow-down-icon.png)), and then click **Save and Schedule Search** to get started. For further instructions on how to save and schedule a search, see [Saved and Scheduled Searches](../analyze/search/save-schedule.md#schedule-and-notify).

Click **Saved Searches** to view your recent executed searches and recent scheduleds searches to access the Saved Searches side panel. From the **Saved Searches** side panel, you can load searches and download search results to a CSV file. To manage your saved searches, click **Managed saved searches** at the bottom of the list. You will be redirected to the **Saved Searches** page. To view a list of all your search results from schedules searches, click **See More** to be redirected to the [Downloads](../analyze/search/downloads.md) page.

You can also click the **Saved Searches** tab to access the Saved Searches page, where you can view a list of your saved searches, scheduled saved searches, and saved searches not on a schedule. From the **Saved Search** tab, you can managed your saved searches, including editing the search query, schedule, tags, and recipients, or adding a schedule to a saved search, and deleting searches. For more information, see [Saved and Scheduled Searches](../analyze/search/save-schedule.md).

#### Schedule search notifications

You can set up notifications to alert you and others, or send an alert to a connector, when a scheduled search is complete. The search and notification can help you keep records and track any changes. For more information, see [Create a search schedule and notification](../analyze/search/save-schedule.md#Create).

### Download search results

You can download search results from completed scheduled searches and recent searches from the Downloads page and from the Search page. Click the **Downloads** tab in the Search page. Click **DOWNLOAD** to export the search results to a CSV file. You can also edit the schedule, and input the scheduled search query for search. Click **SCHEDULE** to edit the search schedule in the Saved Search Schedule form. Click **SEARCH** to input the scheduled search query for search.

You can also download results from the Search page. Click **Saved Searches**, and then click the recent search for which you want to download search results. To view a list of all your search results from schedules searches, click **See More** to be redirected to the Downloads page. For more information, see [Downloads](../analyze/search/downloads.md).

### Help search fields

The **Help** side panel provides a library of fields organized by data types  that you can add to the Expert mode search query. In Search Expert mode, click **Help** to access the Help side panel. The help fields allow you quickly to create effective searches that address the security concerns and goals for your organization. For more information, see [Search Help Query Builder](../analyze/search/help.md).

### Work with messages

After you perform a search, you can view the details of messages that appear in the search results. Click a message to:

* View a summary of the message
* View the source properties
* In Simple mode, add filters or tokens to the search query  to refine results
* Export the message summary to a CSV file
* Create a manual incident from one or more message

For more information, see [Manage Search Results Messages](../analyze/search/manage-search-results.md).

### Other features

You can execute more than one search at the same time when you need to run multiple searches at one time. You can see the tab of your search at the top of the Search page, and switch between search tabs. Search tabs are not stored, and you can  close them when you are done working in them. Your recent executed searches are stored in the Saved Searches side panel.

You can also configure settings to apply to all of your search results. Click **Settings** on the search page. You have the option to automatically transform the timestamps in data sources to your time zone.
