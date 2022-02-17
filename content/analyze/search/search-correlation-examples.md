#  Examples of Search Correlation Queries

The improved correlation experience allows you to create powerful custom rules with  similar syntax structure as Search queries in the Search page of the Alert Logic console.  When you create a correlations rule, Alert Logic examines data as it is collected for matching patterns based on the correlation alert you created and will trigger an incident or an alert. For more information on Search Correlations, see [Improved Correlations and Search](search-correlation.md).

## When to create a correlation

Correlations are specific sets of custom rules that you can create to be notified or alerted when the data Alert Logic receives matches the pattern for the data you specified in the correlation. Correlations allows you to be notified or alerted for incidents or observations outside of what Alert Logic already generates in the [Incidents](../incidents.md) page. The correlations features allows for an extra layer of protection that your organization can actively and internally monitor. For example, if your organization has a custom-built internal application or software, you can create a correlation rule to be notified when a new user logs into your application or when files are moved or deleted in your application. Other examples of correlations you can create are for user login failures that occur more than five times in ten minutes, deny logs that block certain requests, and installation of a new program on your domain controller.

You can configure the correlation rule to generate a FIM notification, an observation notification, or an incident notification. Specific examples of the types of notifications and alerts you can create a correlation for are:

* Incident notification alerts about a correlation for an administrative user that logs into your production data center
* FIM notification alerts about a correlation for sensitive files that were moved or deleted by a user that is not authorized to access those files
* Observation notification about a correlation that provides valuable security information (a failed administrative user login, for example), but you do not consider it as severe as an incident.

    You can use correlations to perform your own internal analysis of messages, but the Alert Logic Security Operations Center (SOC) does not review correlation incidents or observations.    ## Correlation query example 

The examples illustrated in this document can help you understand the correlation interface and system. A correlation (incident, observation) occurs once for each unique result of the SELECT field. The suppression setting in the correlation configuration  applies for a distinct set of values in each correlation. There is an overall limit of 300 (incidents or observations) per hour.

The table below can help you understand correlations. Consider the following examples with a hypothetical fruit log parser:

| time | message | color | fruit |
|---|---|---|---|
| 1:00 PM | My apple is red | red | apple |
| 1:30 PM | My pear is red | red | pear |
| 4:00 PM | My banana is green | green | banana |
| 4:30 PM | My tomato is red | red | tomato |

Below is the basic example of the fruit log parser message:

| SELECT color, fruit |
| WHERE EXISTS (color) |

The example generates four potential correlation occurrences, since all four values are distinct, regardless of the suppression that is set:

* red, apple
* red, pear
* green, banana
* red, tomato

If you add aggregations to the example, the **Limit per time** suppression applies to unique values:

| SELECT color, fruit, COUNT(message) |
| WHERE EXISTS (color) |
| GROUP BY color, fruit |

The example above with the **Limit per time** suppression generates four potential correlation occurrences:

* red
* red
* green
* red

For the example above, if the suppression is set to **Limit generation to once per hour**, the rule  generates three potential correlation occurrences and suppresses 1:30 (because red occurred 30 minutes earlier):

* 1 PM: (red)
* 4 PM: (green)
* 4:30 PM (red)

Continuing with the example, if the suppression is set to **Limit generation to once per 6 hours**, only two potential correlations occurrences exist:

* 1 PM: (red)
* 4 PM: (green)

You should avoid the SELECT message since it generates a correlation per unique message, which is not specific to what you may need.

| SELECT message, color |
| WHERE EXISTS (color) |

If there were 500 messages with unique colors (blue, orange, yellow, brown) at 1:15 PM, only the first 299 would generate correlation occurrences, since there is a limit of 300 for every 24 hours. This correlation rule would not generate another correlation until 1:15 PM the following day.

The following example generates up to four instances since there are only four unique messages.

| SELECT message |
| WHERE EXISTS (message) |
