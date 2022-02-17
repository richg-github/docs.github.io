# Examples of Common Log Message Searches

Alert Logic is offering an improved version of the Log Search feature. To learn more about this feature, see [Get Started with Search](../../get-started/search-a.md).

The following examples illustrate a few common log searches. You can copy the search and projection statements, and then substitute log message objects with your own to create searches relevant to your organization and its security goals.

## Aggregate search results by log message type

The following search and projection returns a list of all log message types, grouped by message type, and listed in descending order:

**WHERE:**<kbd>EXISTS [Message Type]</kbd>

**SELECT:**<kbd>SELECT [Message Type], COUNT( [Message] ) AS "MessageCount" GROUP BY [Message Type] ORDER BY "MessageCount" DESC</kbd>

## Aggregate search results by log message type for log messages that contain a specified word

The following search and projection returns a list of log messages that contain "Windows." The search results are grouped by message type, and listed in descending order.

**WHERE:**<kbd>[Message] Contains "Windows"</kbd>

**SELECT:**<kbd>SELECT [Message Type], COUNT( [Message] ) AS "MessageCount" GROUP BY [Message Type] ORDER BY "MessageCount" DESC</kbd>

## Search for message types that indicate changes to Windows user accounts

The following search returns a list of log messages of specified message types that reveal changes to Windows accounts. The search results are grouped in descending order by time received.

**WHERE:**<kbd>[Message Type] IN ("Windows User Account Changed","Windows User Account Deleted","Windows User Account Disabled","Windows User Account Enabled","Windows User Account Created")</kbd>

**SELECT:**<kbd>SELECT [Time Received], [Message] ORDER BY [Time Received] DESC</kbd>

## Aggregate search results by message type, caller security ID, and user security ID

The following search and projection returns a list of log messages that reveal actions that one user made to another Windows user's account. The search results are grouped by message type, caller security ID, and user security ID, and listed in descending order.

**WHERE:**<kbd>[Message Type] IN ("Windows User Account Changed","Windows User Account Deleted","Windows User Account Disabled","Windows User Account Enabled","Windows User Account Created")</kbd>

**SELECT:**<kbd>SELECT [Message Type], [Caller Security ID], [User Security ID], COUNT( [Message] ) AS "MessageCount" GROUP BY  [Message Type], [Caller Security ID], [User Security ID] ORDER BY "MessageCount" DESC</kbd>

## Discover all changes made to a specified Windows user account

The following search and projection returns a list of users that made  changes to a specified user (“Travis1”), including the type of actions taken. The search results are grouped by message type and listed in descending order by number of message type.

**WHERE:**<kbd>[Message Type] IN ("Windows User Account Changed","Windows User Account Deleted","Windows User Account Disabled","Windows User Account Enabled","Windows User Account Created") AND [User Security ID] = “Travis1”</kbd>

**SELECT:**<kbd>SELECT [Message Type], [Caller Security ID], [User Security ID], COUNT( [Message] ) AS "MessageCount" GROUP BY [Message Type], [Caller Security ID], [User Security ID] ORDER BY "MessageCount" DESC</kbd>

## Search all Windows failed logins using a specified event ID and logon substatus and aggregate by a specified user name.

The following search returns a list of failed logins for Windows Event ID 4625, with a logon substatus of 0xC000006A. The search results are grouped by user name and listed in descending order by number of failed logins.

**WHERE:**<kbd>[Windows Event ID] CONTAINS "4625" AND [Logon Substatus] CONTAINS "0xC000006A"</kbd>

**SELECT:**<kbd>SELECT [User Name], COUNT( [Message] ) AS "Failed Count" GROUP BY [User Name] ORDER BY "Failed Count" DESC</kbd>
