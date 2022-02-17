# Create Complex Log Searches

Alert Logic is offering an improved version of the Log Search feature. To learn more about this feature, see [Get Started with Search](../../get-started/search-a.md).

The Alert Logic Log Search feature provides **WHERE** and **SELECT** fields that allow you to create SQL-like searches and aggregations to narrow and organize the list of search results. You can use the Search Assistant to choose search and aggregation criteria and their available operators.

## Use the Search Assistant

The Search Assistant, which appears by default, helps you create searches and aggregations by presenting suggestions as you type in the **WHERE** field. Click a value in the **Namespace** column, and then select an available operator for the selected namespace. The Search Assistant provides quotation marks where you must type a search term, or select from a list of suggested search terms. You can click additional namespaces to create <kbd>AND</kbd> statements, and you can use <kbd>OR</kbd> statements to search for multiple criteria.

The Search Assistant lists all saved searches created by users in your customer account. Select a search in the **Saved Searches** column, and then click **ADD TO SEARCH** to populate the search fields. For more information about saved and scheduled searches, see [Create Saved and Scheduled Log Searches](save-schedule.md#save-schedule-search).

## Add search terms from a log message

If you want to perform a log search based on a specific log message in a list of search results, you can click within the log message preview to add criteria to the **WHERE** field and create a more detailed search.

**To add search terms from a log message:**

1. In the list of search results, click a log message from which you want to create a search.
2. Click log message object items in the message, or listed across the bottom of the message, that you want included as a search term.

    Valid search term entries are highlighted when you hover your cursor over them.     
You can  add multiple search terms, and the log search automatically inserts the required <kbd>AND</kbd> between them.

## Aggregate search results with projection statements

The Log Search **SELECT** field allows you to use a SQL-like projection statement to aggregate your search results. You can specify the columns of data to display in the list of search results, and specify how Log Search groups and orders search results.

By default, Alert Logic displays search results in descending order by time received, and displays the full content of the log message (<kbd>SELECT [Time Received], [Message] ORDER BY [Time Received] DESC</kbd>). The **SELECT** field allows you to specify the fields you want to display in the search results. You can add projections to customize the organization of search results.

The following statement returns a list that displays the user name, host name, and the number of log messages that include both. The statement also specifies that the results be listed in descending order by the number of log messages and grouped by user name and host name.
<kbd>SELECT [User Name], [Host Name], COUNT (Message) AS "MessageCount" ORDER BY "MessageCount" DESC GROUP BY [User Name], [Host Name]</kbd>
For more information about projections and the **SELECT** field, see [Search Assistant Projections](../../reference/search-projections.md).

### Clear search statements and reset projections

The Log Search feature includes the following icons that allow you to reset your search criteria to the default settings:

* Click the clear icon (![](../../Resources/Images/Icons/clear-search.png)) to clear the **WHERE** field, and then create a new search statement.
* Click the reload icon (![](../../Resources/Images/Icons/reload-select-field.png)) to reset the **SELECT** field, and the date and time range to their default values.
