# File Integrity Monitoring (FIM) Search Examples

The Alert Logic Search experience allows you to search for [File Integrity Monitoring ](../../configure/file-integrity-monitoring.md) events as <kbd>fimdata</kbd> data types. The following examples illustrate a few common searches for File Integrity Monitoring (FIM) data type search. You can copy the search, and then substitute objects with your own to structure query searches relevant to your organization and its security goals.

The following are reminders to successfully execute a search:

* Strings are 'single quoted'
* Field names (and aliases) are "double quoted". Double quoting can be used to access fields with the same name as SQL reserved words, like "count".
* LIMIT and WHERE are optional
* GROUP BY, ORDER BY, and HAVING work as they do in SQL
* Functions like IN take [arrays] of values, for example User IN ['sayler', 'msayler']
* You can't (yet) join multiple data types in a single query
* You can use single-line comments starting with -- to help organize large queries
* Access JSON data using parsed.json.field.subfield syntax
* It's often easiest to start a complex query in Simple mode, apply filters and grouping, then convert to Expert mode to add more logic or complex functions.
* null, true, and false are reserved words, and work as in SQL

For FIM, you can search on any of the following fields:

* ts (type: integer)—Time the FIM event occurred
* ingest_ts  (type: integer)—Time Alert Logic persisted the FIM event
* host_id  (type: string)—Host identifier the where the FIM event occurred
* file_type (type: string)—The file type for the FIM Event, for example file or directory
* file_name (type: string)—The file name for the FIM event, excluding the path or directory
* file_size  (type: integer)—The file size for the FIM event
* file_owner (type: string)—The file owner for the FIM event
* file_group (type: string)—The file group (owner) for the FIM event
* file_permissions (type: integer)—The file permissions for the FIM event
* file_attributes (type: integer)—The file attributes for the FIM event
* file_ctime (type: integer)—The file creation time for the FIM event
* file_atime (type: integer)—The last time the file was accessed for the FIM event
* file_mtime (type: integer)—The last time the file was modified for the FIM event
* sha1_hash (type: string)—The file SHA1 hash for the FIM event
* ingest_id (type: binary)—Unique identifier of the message that you can use in combination with CID to locate message on storage

**Structure**:

* AS
* FROM
* GROUP BY [PERMUTED]
* HAVING
* LIMIT
* ORDER BY
* SELECT
* WHERE
* WITH TAXONOMY

**Transforms**:

* !=
* *
* +
* -
* <
* <=
* =
* >
* >=
* ALL_IN
* AND
* ANY_IN
* ARRAY_ALL
* ARRAY_ANY
* ARRAY_NONE
* AS
* BETWEEN
* CAST
* CHAR_LENGTH
* CIDR_MATCH
* COALESCE
* CONCAT
* CONCAT_WS
* CONTAINS
* CONTAINS_ALL
* CONTAINS_ANY
* DECODE
* DURATION
* ENDS_WITH
* EXISTS
* FROM_EPOCHTIME
* GEOIP
* IF
* IN
* INTERVAL
* ISNULL
* IS_INTERNAL_ADDRESS
* IS_IP_ADDRESS
* IS_NOT_NULL
* IS_NULL
* LENGTH
* LIKE
* LOWER
* NONE_IN
* NOT
* NOW
* OR
* REGEXP_EXTRACT
* REGEXP_MATCH
* SPLIT
* STARTS_WITH
* TAGS:EXISTS
* TAGS:LOOKUP
* TO_EPOCHTIME
* TUNE:THRESHOLD
* URI_PARSE
* WINDOW

**Aggregators**:

* AVG
* COUNT
* LSET
* LUCOUNT
* MAX
* MIN
* SET
* SUM
* UCOUNT
