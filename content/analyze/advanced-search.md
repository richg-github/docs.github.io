# Perform Advanced Searches

The advanced search feature allows you to create complex queries that can combine with selected filters to further refine your incident search results. To access the advanced search feature, click **advanced search** under the search bar.

In the advanced search field, type a query statement using available fields and operators. If needed, you can use subsequent search fields to add <kbd>OR</kbd> statements and create a search that tests for multiple conditions. As you type a search statement, a warning icon (![](../Resources/Images/Icons/warning_icon_sql.png)) appears to the left of the search field until the query contains valid syntax. You cannot submit a search with invalid syntax.

## Advanced search syntax

Each search field requires you to enter values available for that field within a set of quotes. You can create a search that provides results for more than one value in a field by placing values parenthesis and separating them with commas.

    The query below searches for brute force incidents. 

<kbd>Classification="brute-force"</kbd>    The query below searches for brute force and Trojan activity incidents. 

<kbd>Classification IN("brute-force","trojan-activity")</kbd>
For additional examples that illustrate search syntax, see [Advanced search examples](#advanced-search-examples).

## Advanced search options

The advanced search feature allows you to make simple and complex incident queries using one or more of the following available fields:

* <kbd>Classification</kbd> — This field refers to incident classification types recognized by Alert Logic. 				**Available field values****Available operators**
For a full list of operators, see [Advanced search operators](#advanced-search-operators).
   * <kbd>=</kbd>
   * <kbd>!=</kbd>
   * <kbd>IN</kbd>
   * <kbd>"base"</kbd>
   * <kbd>"recon"</kbd>
   * <kbd>"application-attack"</kbd>
   * <kbd>"policy-violation"</kbd>
   * <kbd>"info-leak"</kbd>
   * <kbd>"trojan­-activity"</kbd>
   * <kbd>"worm­-activity"</kbd>
   * <kbd>"defensive-­action"</kbd>
   * <kbd>"containment-­action"</kbd>
   * <kbd>"brute­-force"</kbd>
   * <kbd>"denial-­of-­service"</kbd>
   * <kbd>"log­-policy"</kbd>
   * <kbd>"pending"</kbd>
   * <kbd>"misconfiguration"</kbd>
* <kbd>ThreatLevel</kbd> — This field refers to the possible severity level for an incident.
**Available field values**   * <kbd>"Critical"</kbd>
   * <kbd>"High"</kbd>
   * <kbd>"Medium"</kbd>
   * <kbd>"Low"</kbd>
   * <kbd>"Info"</kbd>
**Available operators**   * <kbd>=</kbd>
   * <kbd>!=</kbd>
   * <kbd>&amp;gt;</kbd>
   * <kbd>&amp;lt;</kbd>
   * <kbd>=&amp;lt;</kbd>
   * <kbd>=&amp;gt;</kbd>

For a full list of operators, see [Advanced search operators](#advanced-search-operators).* <kbd>DetectionSource</kbd> — This field refers to the service or feature that detected the incident.
**Available field values**   * <kbd>"IDS"</kbd>
   * <kbd>"LOG"</kbd>
   * <kbd>"MANUAL"</kbd>
   You can also use <kbd>"MANI"</kbd> or <kbd>"MANL"</kbd>
   * <kbd>"WAF"</kbd>
   * <kbd>"guardduty"</kbd>
**Available operators**   * <kbd>=</kbd>
   * <kbd>!=</kbd>
   * <kbd>IN</kbd>

For a full list of operators, see [Advanced search operators](#advanced-search-operators).* <kbd>IncidentID</kbd> — This field refers to the ID Alert Logic assigns to the incident.
**Available operators**   * <kbd>=</kbd>
   * <kbd>IN</kbd>

For a full list of operators, see [Advanced search operators](#advanced-search-operators).* <kbd>IP</kbd> — This field refers to any IP address that appears in the incident. You can also use CIDR values in this field.
**Available operators**   * <kbd>=</kbd>
   * <kbd>!=</kbd>
   * <kbd>IN</kbd>

For a full list of operators, see [Advanced search operators](#advanced-search-operators).* <kbd>SourceIP</kbd> — This field refers to the IP address from which the attack occurred. You can also use CIDR values in this field.
**Available operators**   * <kbd>=</kbd>
   * <kbd>!=</kbd>
   * <kbd>IN</kbd>

For a full list of operators, see [Advanced search operators](#advanced-search-operators).* <kbd>DestinationIP</kbd> — This field refers to the IP address of the asset on which the incident occurred. You can also use CIDR values in this field.
**Available operators**   * <kbd>=</kbd>
   * <kbd>!=</kbd>
   * <kbd>IN</kbd>

For a full list of operators, see [Advanced search operators](#advanced-search-operators).
* <kbd>Account</kbd> — This field refers to the customer account in which the incident occurred.
**Available operators**   * <kbd>=</kbd>
   * <kbd>!=</kbd>
   * <kbd>IN</kbd>

For a full list of operators, see [Advanced search operators](#advanced-search-operators).
* <kbd>Deployment</kbd> — This field refers to the deployment in which the target asset appears.
**Available operators**   * <kbd>=</kbd>
   * <kbd>!=</kbd>
   * <kbd>IN</kbd>

For a full list of operators, see [Advanced search operators](#advanced-search-operators).
### Advanced search operators

The advanced search feature allows you to use the following operators to create your queries:

* <kbd>AND</kbd> — This operator allows you to string together multiple items and will display a list of incidents where all the conditions separated by <kbd>AND</kbd> are true.
* <kbd>OR</kbd> — This operator is inclusive and allows for wider searches by displaying a list of incidents where any of the <kbd>OR</kbd> statements is true. Each additional line in the advanced search feature is an <kbd>OR</kbd> statement.
* <kbd>IN</kbd> — This operator allows you to specify multiple values in a clause to display a list of incidents with multiple field values. For example, if you use the <kbd>IN</kbd> operator with the <kbd>ThreatLevel</kbd> field, you can display incidents with Critical and High threat levels.

In addition, you can use the following operators to show the relationship between a value and the desired result:

* <kbd>=</kbd> — You want to see results that match a given value.
* <kbd>!=</kbd> — You want to see results that do not match a given value.
* <kbd>&amp;gt;</kbd> — You want to see results that are greater than a given value.
* <kbd>&amp;lt;</kbd> — You want to see results that are less than a given value.
* <kbd>=&amp;lt;</kbd> — You want to see results that are equal to or less than a given value.
* <kbd>=&amp;gt;</kbd> — You want to see results that are equal to or greater than a given value.

## Advanced search examples

Use the examples in this section to understand how to create queries that help you investigate incidents.

    Find incidents that occurred in a specified deployment (MyDeploymentName) and include a specified IP address (172.31.3.10).

<kbd>Deployment="MyDeploymentName" AND IP="172.31.3.10"</kbd>    Find incidents that occurred in the last seven days, with Critical and High threat levels, and in a specified deployment (MyDeploymentName). Order the results by threat level and the date of incident creation.

<kbd>ThreatLevel IN("Critical", "High") AND Deployment="MyDeploymentName"</kbd>

To order the results by threat level, click the drop-down menu above the Incident List, and then select **Organize by Threat Level**.
To limit the results to incidents from the last seven days, click the date selector drop-down menu at the upper right of the page, and then select the appropriate date range.     Find incidents that occurred in the last 30 days, from a specified source IP address (118.123.15.210), and to a specified destination IP address (172.31.17.117). 

<kbd>SourceIP="118.123.15.210" AND DestinationIP="172.31.17.117"</kbd>

To display results for only the last 30 days, click the date selector drop-down menu at the upper right of the page, and then customize the date range for the last 30 days.
