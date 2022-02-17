# Cloud Defender Omnibox Search Upgrade

Alert Logic now offers an enhanced and improved experience  for Cloud Defender customers  upgrading to the new Search feature. This document is intended to help you become familiar from Cloud Defender Omnibox search feature to the new Search feature.

The Search experience in the Alert Logic console allows you to perform basic and advanced searches for different data types. The Search feature is flexible for structuring your own search queries or using template, fields, and predefined expressions to help you find and organize  messages most relevant to your investigation. Search also supports variety of data sources required to cover potential threats, discover what log sources are present in an environment, and provide tools for further investigation.

Your new experience includes all of the same capabilities as the current Omnibox Search experience, including new and improved features. To refer to documentation for the current Omnibox Search features and functionality, see [Log Manager messages](https://legacy.docs.alertlogic.com/userGuides/log-manager-messages.htm).

## Changes to your Search experience

Alert Logic is now offering two Search mode experiences:    Simple mode and Expert mode. You can alternate between the two modes depending on your needs. Click the drop-down list to alternate between **Expert Mode** and **Simple Mode**.

### Search modes

Simple mode provides a graphical interface that allows you to add or remove conditions and fields, aggregate or add a function to predefined expressions,  and determine sorting and order. Simple mode is optimized for performing common types of search queries. You can  create a query in Simple mode, apply filters and grouping, and then switch to Expert mode to add more logic or complex functions. You will notice that Simple mode functions and looks similar to the current Omnibox experience. For more information about Search Simple Mode, see [Search Simple Mode ](../analyze/search/simple-mode.md).

Expert mode allows you to create your own SQL searches  and aggregations. Expert mode allows you create more complex searches, which you can build from Simple mode when you switch. You can also use the Help feature to quickly find and add fields to your query. You can combine search terms using nested logical expressions. You can use many more functions in expert mode such as the following to:

* Add conditional terms to your search
* Use regular expressions to express complicated matching rules, or to extract custom fields from your data
* Access the Alert Logic asset model to search for data based on where it was collected, for example by AWS tag.
* Extract more security value from your data by apply geo-IP lookup and URL decoding functions

For more information about Search Expert Mode, see [Search Expert Mode ](../analyze/search/expert-mode.md).

### Search features

Alert Logic now offers the following new features:

* Schedule search notifications
* Save  searches and schedule searches
* Download search results
* Use search tabs to execute and switch between multiple searches
* Enter message types or tokens into the search query from the search results
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

For detailed information on how to structure your queries, see the [Structure Query Language guide](../pdf-files/SQL-dev-guide.pdf).

## Build your query

In Simple mode, to start your query, in the <kbd>FROM</kbd> field, click the drop-down list to find the data type you need. You can also click the edit icon (![](../Resources/Images/pencil icon.png)) to enter the data type you need. In the <kbd>LIMIT</kbd> field, enter the maximum amount of messages you want returned.

After you have entered a data type and specified your limit, you can then move on to the section under **Where all of the following are true**. In this section, you can modify search terms like the **Time Received** and **Message** fields to filter the results. You can enter more terms using the search bar. Enter a keyword to search for the term you want add, and then choose from the options  that appear. You can also remove terms you do not need. You can apply values, functions, conditions, and aggregations. You can also specify how to group and sort results with the modified fields, show or hide the modified fields, and remove filters.

For example, to modify to the **Time Received** term:

1. Click the add icon (![](../Resources/Images/search/add-icon.png)) to enter a value. To remove a value, click the remove icon (![](../Resources/Images/search/remove-icon.png)). To specify that you do not want this value in your results, click on the value to include **NOT** in front of it.
2. Click the function icon (![](../Resources/Images/search/function-icon.png)) to select an aggregator or  function to apply to the value.
3. Click the show icon (![](../Resources/Images/search/show-icon.png)) to hide column for the search results of this term field. The results for this term field will show by default.
4. Click the sorting icon (![](../Resources/Images/search/sorting-arrow.png)) to sort the field by descending or ascending order.

You can also drag and drop terms in the order you want to see them organized as columns in the search results. Click **SEARCH** to execute your search.

## Refining your search

From your search results, you can also enter message types or tokens. Click on the message type or token from the search results lists to add it to the search query.

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

After you execute a search, you can view the details of messages that appear in the search results. Click a message to:

* View a summary of the message
* View the source properties
* Add filters or tokens to the search query  to refine results
* Export the message summary to a CSV file
* Create a manual incident from the message

For more information, see [Manage Search Results Messages](../analyze/search/manage-search-results.md).

### Download search results

If you need to download search results from scheduled searches, you can access search results from the Downloads page.

You can also download results from the Search page. Click **Saved Searches**, and then click the recent search for which you want to download search results. To view a list of all your search results from schedules searches, click **See More** to be redirected to the Downloads page. For more information, see [Downloads](../analyze/search/downloads.md).
