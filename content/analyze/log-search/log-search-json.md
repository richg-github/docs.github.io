# Parsed JSON Log Search and Examples

Alert Logic is offering an improved version of the Log Search feature. To learn more about this feature, see [Get Started with Search](../../get-started/search-a.md).

Parsed JSON searching is built into the Log Search feature and allows you to search on fields from any JSON log. You can use JSONPath queries, parsed token names, or a combination of both to aggregate and filter log messages received in parsed JSON format.

For more detailed information about JSON log parsing and searching, see [JSON Log Parsing](https://support.alertlogic.com/hc/en-us/articles/360027305271-JSON-Log-Parsing).

The following examples illustrate a few common JSON log searches. You can copy the search and projection statements, and then substitute properties and tokens with your own to create searches relevant to your organization and its security goals.

## Use JSONPath queries for log message search and filtering

You can use the <kbd>[parsed.json]</kbd>prefix to create JSONPath queries in the **WHERE** field that aggregate and filter JSON log messages. This section lists a few examples you can customize for your own searches.

### List all JSON log messages

The following query displays all JSON log messages:

**WHERE**<kbd>EXISTS [parsed.json]</kbd>

**SELECT**<kbd>SELECT [Time Received], [Message] ORDER BY [Time Received] DESC</kbd>

### Filter through JSON log messages by property value

The following example demonstrates how to filter the aggregated list from the previous section by a specified user type:

**WHERE**<kbd>[parsed.json.userIdentity.type] = "AssumedRole"</kbd>

**SELECT**<kbd>SELECT [Time Received], [Message] ORDER BY [Time Received] DESC</kbd>

### Display specific JSON object properties in the search result

The following example demonstrates how to display specific JSON object properties in your search results:

**WHERE**<kbd>[parsed.json.requestParameters.tableName] CONTAINS "EC2-Instance-Start-Stop-Scheduler-StateTable"</kbd>

**SELECT**<kbd>SELECT [Time Received], [parsed.json.requestParameters.tableName] AS "Table Name", [Message] ORDER BY [Time Received] DESC</kbd>

### Aggregate based on JSON properties

The following example demonstrates how to create a search that aggregates search results by specified JSON properties:

**WHERE**<kbd>EXISTS [parsed.json.userIdentity.sessionContext.sessionIssuer.userName]</kbd>

**SELECT**<kbd>SELECT [parsed.json.eventSource], [parsed.json.eventName], [parsed.json.userIdentity.sessionContext.sessionIssuer.userName], COUNT([Message]) AS "Messages Count" GROUP BY [parsed.json.eventSource], [parsed.json.eventName], [parsed.json.userIdentity.sessionContext.sessionIssuer.userName] ORDER BY "Messages Count" DESC</kbd>

## Use token names from parsed JSON log messages

Your query can include the token names found in the parsed JSON log messages. This section lists examples you can customize with specified token names for your own searches.

### Filter JSON log messages on specific value of a property

**WHERE**<kbd>[User Type] = "AssumedRole"</kbd>

**SELECT**<kbd>SELECT [Time Received], [Message] ORDER BY [Time Received] DESC</kbd>

### Display specific JSON object properties by token name in the search result 

**WHERE**<kbd>[AWS Event Name] = "DescribeTable" AND [awsRegion] = "us-east-2"</kbd>

**SELECT**<kbd>SELECT [Time Received], [Principal ID] AS "Principal", [ARN] AS "Object ID" ORDER BY [Time Received] DESC</kbd>

### Aggregate search results based on values of specified tokens

**WHERE**<kbd>[AWS Event Name] = "DescribeTable"</kbd>

**SELECT**<kbd>SELECT [awsRegion], COUNT([Message]) AS "Message Count" GROUP BY [awsRegion] ORDER BY [awsRegion] DESC</kbd>

## Use mixed syntax of parsed token names and JSONPath notation in a query

The following example illustrates how to mix syntax within a single Log Search query:

**WHERE**<kbd>[AWS Event Name] = "DescribeTable" and [parsed.json.requestParameters.tableName] CONTAINS "EC2-Instance-Start-Stop-Scheduler-StateTable"</kbd>

**SELECT**<kbd>SELECT [Time Received], [parsed.json.requestParameters.tableName] AS "Table Name", [Message] ORDER BY [Time Received] DESC</kbd>
