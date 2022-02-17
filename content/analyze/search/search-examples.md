# Search SQL Reference 

The following examples illustrate a few common searches. You can copy the search, and then substitute log message objects with your own to create searches relevant to your organization and its security goals.

In the new Search experience, there some changes to keep in mind to execute successful searched:

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

The follow is the basic **Structure** of the search, but you can remove or add clauses as necessary:

* AS
* FROM
* GROUP BY [PERMUTED]
* HAVING
* LIMIT
* ORDER BY
* SELECT
* WHERE
* WITH TAXONOMY

The following are common symbols and equations you can use that further **Transforms** your search for more precise and specific results:

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

You can add **Aggregators** to set limits of specific items you want to see in the search results:

* AVG
* COUNT
* LSET
* LUCOUNT
* MAX
* MIN
* SET
* SUM
* UCOUNT
