# Search Assistant Projections

Projections combine with your search statements to specify which columns display your search results, and how your search results appear in the list. By default, Alert Logic displays search results in descending order by time received and log message. The Search Assistant helps you create projections by providing suggestions as you type.

## SELECT

Every projection statement must start with <kbd>SELECT</kbd>, which specifies the data field names that appear as columns in the search results list. The order of the <kbd>SELECT</kbd> fields in the projection determines the order, from left to right, of the columns in the results list. You can combine this projection clause with others to further customize the display of your results.

    The default projection appears as: 
<kbd>SELECT [Time Received], [Message] ORDER BY [Time Received] DESC</kbd>## AS

Use <kbd>AS</kbd> to create an alias for a field name. The alias ensures the search result displays a cryptic field name as a column name with a more readable, descriptive name. You must type the alias between quotation marks.

## ORDER BY

Use <kbd>ORDER BY</kbd> in a projection to specify the <kbd>SELECT</kbd> data field by which to sort search results. You must follow the <kbd>ORDER BY</kbd> clause with either <kbd>DESC</kbd> or <kbd>ASC</kbd> to specify descending or ascending order. If you want to order the results by a column that you named using <kbd>AS</kbd>, you must use the alias value you created, including the quotation marks.

## GROUP BY

Use <kbd>GROUP BY</kbd> in the projection to specify a data field by which to group search results. If you want to group the results by a column that you named using <kbd>AS</kbd>, you must use the alias value you created, including the quotation marks.

## GROUP BY PERMUTED

Use <kbd>GROUP BY PERMUTED</kbd> if you want to group search results by all the values in a specified data field.  This projection statement provides more flexibility than GROUP BY, because it allows you to group results by all tokens in a log message, regardless of whether they are parent or child tokens.

## COUNT

Use <kbd>COUNT</kbd> to display the total number of results that match one or more of the SELECT fields.

    The following projection returns a list that shows the user name, the number of log messages that include the user name, and also orders the list by the number of messages, and groups the results by host name:
<kbd>SELECT [User Name], COUNT (Message) AS "MessageCount" ORDER BY "MessageCount" DESC GROUP BY [Host Name]</kbd>## HAVING

Use <kbd>HAVING</kbd> to specify that the statement you create displays search results where aggregated values meet the conditions determined by the field you specify.

## SUM

Use <kbd>SUM</kbd> to return the total from a specified numeric column in the results.

## AVG

Use <kbd>AVG</kbd> to return the average value of the specified numeric column.

## MIN

Use <kbd>MIN</kbd> to return the smallest value of the specified numeric column.

## MAX

Use <kbd>MAX</kbd> to return the largest value of the specified numeric column.
