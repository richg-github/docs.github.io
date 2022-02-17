# Correlations and Notifications

You can create a log correlation policy in the Alert Logic console and then receive a notification if a log message, or a combination of log messages, meets the correlation conditions. Correlations help you detect security weaknesses or threats for further investigation and response by allowing you to define custom logic to meet the specific security needs of your company or the accounts you manage.

You can configure Alert Logic to do either of the following in near real time when log messages meet the correlation conditions:

* Generate an observation and send an [observation notification](observation.md). An observation  means that Alert Logic observed an occurrence of your log correlation.
* Generate an [incident](../../analyze/incidents.md) and optionally send an [incident notification](incident.md).

For example, you can configure a correlation to generate an incident and send a notification  if a user login failure occurs  more than five times in ten minutes. Another example is you can generate incidents and receive notifications based on  [AWS Network Firewall alerts](../collectors/aws_network_firewall.md).  You can configure the correlation to generate an observation notification instead of generating an incident. The observation notification  informs you about a correlation that provides valuable security information (a failed administrative user login, for example) but does not meet your criteria for Alert Logic to generate an incident.

    You can use correlations to perform your own analysis of log messages, but the Alert Logic Security Operations Center (SOC) does not review these incidents or observations.    
Alert Logic can send the notifications to email recipients and a configured connector such as a webhook. For more information about configuring webhooks, see [Webhook and Email Connectors](../connectors.md). For more information about the Notifications feature, see [Notifications](../notifications.md) and [Manage Notifications](manage.md).

## Start creating a correlation

Alert Logic recommends as a best practice that you create the correlation from the Log Search page since a correlation is built from a valid log search query. After you develop and validate a query (see [Search: Log Messages](../../analyze/log-message-search.md)), you can choose to create a correlation based on the query. Alert Logic then applies the query to the correlation for you.

You can also create a correlation from the Correlations page or the  [Notifications page](manage.md). Whichever method you choose, the process is similar after  you open the Create a Correlation page.

**To create a correlation from the Log Search page:**

1. In the Alert Logic console, click the menu icon (![](../../Resources/Images/dashboard/menu-icon.png)).
2. Click ![](../../Resources/Images/dashboard/investigate-icon.png)**Investigate**, and then click **Search** to access the Log Search page.
3. On the **Search** page in the Alert Logic console, click the **Log Search BETA** tab.
4. Create a valid log search query to define the correlation conditions. For more information about creating the query, see [Search: Log Messages](../../analyze/log-message-search.md). For examples of correlation queries, see [ Examples of Correlation Queries and Setup](correlation-examples.md).
5. Click the **SEARCH** drop-down menu below the query, and then click **Create Correlation**.
6. Complete the fields in the Create a Correlation page. Alert Logic adds the log search query to the correlation, which you can change.

To create a correlation from the Correlations page:

1. In the Alert Logic console, click the menu icon (![](../../Resources/Images/dashboard/menu-icon.png)).
2. Click ![](../../Resources/Images/dashboard/investigate-icon.png)**Investigate**,  click **Search**, and then click the **Correlations** tab.
3. On the **Search** page in the Alert Logic console, click the **Correlations** tab.
4. On the Correlations page, click the add icon (![](../../Resources/Images/Icons/cdAddPlus.png)).
5. Complete the fields in the Create a Correlation page.

**To complete the Create a Correlation page:**

1. Type a descriptive name for the correlation—for example, "Admin Failed Login."
2. If you want the correlation to be active, leave  **Correlation Is Active** turned on. If you want to save the definition but not activate the correlation yet, turn it off.
3. If you did not already create a log search query for the correlation, or if you want to adjust a displayed query, click **EDIT IN SEARCH**, and then create or edit the query. For more information about creating the query, see [Search: Log Messages](../../analyze/log-message-search.md). For examples of correlation queries, see [ Examples of Correlation Queries and Setup](correlation-examples.md).
4. (Optional) For a search query that includes the INTERVAL function, adjust the number of minutes or hours in the **Time Frame** window as needed. The minimum window is one minute and the maximum is 24 hours. Time frame settings do not appear if they are not applicable to your search query.
      Alert Logic generates a correlation if conditions occur within the time frame window and do not exceed the number of occurrences listed in the **Suppression** setting. The window begins when correlation conditions trigger a unique combination of values in the query SELECT statement.      8. Specify the generating option for log messages that meet the correlation conditions:
   * **Observation**—If you want Alert Logic to inform you about the correlation but not generate an incident, click **Observation**.
   * **Incident**—If you want Alert Logic to generate an incident, click **Incident**.
10. Select one of the following **Suppression** options to reduce repeated triggers:
   * **Limit generation to once per hour**
   * **Limit generation to once per 6 hours**
   * **Limit generation to once per 24 hours**
   * **Limit generation to once per week**

Suppression occurs if the same unique combination of values in the SELECT statement of the correlation query triggers an observation or incident  within the specified  time. Alert Logic generates at most 300 incidents or observations per rule in any consecutive 24-hour period.If  you configure failed user logins to trigger a correlation and you limit incident generation to once per hour, Alert Logic generates only one incident for a specific user login failure during the hour. If login failures occur for multiple users in an hour, Alert Logic generates an incident for each user (up to 300 incidents in 24 hours).14. Add details about the observation or incident that the correlation will generate.  See the relevant procedures below:
   * [Finish setting up an observation for a correlation](#set-up-observation)
   * [Finish setting up an incident for a correlation](#set-up-incident)

## Finish setting up an observation for a correlation

To finish setting up the observation that results from the correlation,  add details about the correlation to help analysts quickly understand the problem, and then save your correlation.

1. Add details about the observation:
   * **Observation Summary**—Type descriptive text to summarize the observation.
   * **Attacker**—(Optional) Select the query field that identifies the suspected attacker.
   * **Target**—(Optional) Select the query field that identifies the target of the attack.
   * **Description**—To describe the observation, type descriptive text,  insert one or more fields from the query (type the % character to see a list), or both. Field names must be enclosed with % characters. You can use [Markdown syntax](#markdown) to format the text.
3. Click **SAVE AND CONTINUE**. A page for creating the notification opens with the correlation already added as a filter. For information about setting up the notification, see [Observation Notifications](observation.md).

## Finish setting up an incident for a correlation

To finish setting up the incident that results from the correlation,  add details about the correlation to help analysts quickly understand the problem. Then you need to choose whether to set up an incident notification and save your correlation.

1. Add details about the incident:
   * **Incident Summary**—Type descriptive text to summarize the incident.
   * **Attacker**—(Optional) Select the query field that identifies the suspected attacker.
   * **Target**—(Optional) Select the query field that identifies the target of the attack.
   * **Investigation Report**——Add information to help with incident investigation. You can type descriptive text,  insert one or more fields from the query, or both. Enclose field names with % characters. You can use [Markdown syntax](#markdown) to format the text.
   * **Recommendations**—(Optional) Add a recommended response to the incident. You can type descriptive text,  insert one or more fields from the query, or both. Enclose field names with % characters. You can use [Markdown syntax](#markdown) to format the text.
3. Specify whether to send a notification when the correlation conditions generate an incident:
   * To send a notification, turn on **Create Incident Notification in Next Step**, and then click **SAVE AND CONTINUE**. A page for creating the notification opens with the correlation already added as a filter. For more information about setting up the notification, see [Create an incident notification](incident.md#create).
   * To generate the incident but not send a notification, leave **Create Incident Notification in Next Step** turned off, and then click **SAVE**.

## Alert Logic Markdown

When you click a field that supports Markdown syntax for text formatting, a Markdown icon (![](../../Resources/Images/Icons/markdown-icon.png)) appears. Alert Logic supports the following syntax:

| Element | Syntax |
|---|---|
| Paragraph | To start a new line of text (equivalent of a <br> in HTML), type three space characters at the end of the line. |
| Heading | Type one or more # characters before the heading, with each # representing a heading level. # Heading text (an <h1> in HTML) ## Heading text (an <h2> in HTML) |
| Block quotation | Type a > character before the block quotation (equivalent of a <blockquote> in HTML). > First paragraph in the quotation > > Second paragraph in the quotation |
| Bold and italic text | Enclose the text with two * characters for bold (**bold**) or one * character for italic (*italic*). You can use * and _ characters to combine bold and italic. **You _must_ notify the on-call team.** Gives you this: **You *must* notify the on-call team.** |
| Code | Enclose the text with a single backtick character (') to apply a monospace font to preformatted text. To create a block of code, enclose the block with three backticks ('''). '''
Code line 1
Code line 2
''' |
| Unordered list | Before each item in the list, type a *, a -, or a + character followed by a space. The characters are interchangeable. * Item + Item - Item |
| Ordered list | Before each item in the ordered list, type a number. 1. Step 1 2. Step 2 3. Step 3 |

## View and manage correlations

The Correlations page  lists your existing correlations. You can [create](#createFromCorrelationPage), preview, and manage correlations from this page.

To narrow the set of correlations listed, you can use the filters in the left navigation. You can also group and sort the correlations with tools available toward the top of the page.

To access the Correlations page, from the Search page, click the **Correlations** tab.

You can click **Preview** next to a specific correlation to see its details and manage the correlation.

    You can also view and manage correlations from the [Notifications page](manage.md).    ### Filter the correlations list

The Correlations page displays all active correlations created from the customer account and its managed accounts. You can also display inactive correlations and apply additional filters to narrow the list to a specific set of correlations.

To filter the correlations list:

1. In the left navigation, click the correlation status of interest:
   * **Active**
   * **Inactive** (correlation is saved but not turned on)
3. To further narrow the list to show only incident or observation correlation types, click **Incidents** or **Observations**.
4. To clear filters and start over, delete any text you typed in **Search filters** or select **CLEAR ALL FILTERS**.

### Organize the correlations list

You can organize the correlations list by grouping and sorting the correlations. Alert Logic groups your correlations by correlation type and sorts them by date last triggered within each grouping. You can group and sort the notifications by other criteria to suit your needs.

To organize your correlations:

1. To change the grouping, click **Group by**, and then click the option you want. Available options match the filters listed in the left panel.
2. To change the way the list is sorted within each grouping, click **Sort by**, and then click the option you want. Available options include:
   * Last Triggered
   * Alphabetically
   * Creation Date
   * Last Modified Date

### Search the correlations list

You can use the search bar  to filter the list to include only correlations that contain specific words in important fields, like name.

### View and manage correlations from the detail view

You can view the details about a specific correlation. The detail view indicates the last time the correlation was triggered, the date the correlation was created and last modified, the log search query, and other details about the correlation that can help you understand the correlation and respond to it quickly.

For an incident correlation type, the view includes the number of open incidents generated by the correlation and a RESPOND link, which accesses the Incident List filtered to show incidents generated by the correlation.

From the detail view, you can also view the list of notifications that will be sent when correlation conditions are met, add a notification, edit the correlation, or delete it.

**To view details about a correlation:**

1. From the Search page, click the **Correlations** tab.
2. To the right of the correlation you want to view, click **Preview**.
3. When you are finished viewing correlation details, click **Hide**.

To add a notification to a correlation:

1. From the Search page, click the **Correlations** tab.
2. To the right of the correlation for which you want to set up a notification, click **Preview**.
3. Toward the bottom of the detail view, click **+ADD**. A page for creating the notification opens with the correlation already added as a filter. For information about setting up the notification, see the relevant information:
   * [Create an incident notification](incident.md#completeCreationPage)
   * [Create an observation notification](observation.md#create)

To delete a correlation:

1. From the Search page, click the **Correlations** tab.
2. To the right of the correlation you want to delete, click **Preview**.
3. Toward the bottom of the detail view, click the **DELETE** icon.

To edit a correlation:

1. From the Search page, click the **Correlations** tab.
2. To the right of the correlation you want to edit, click **Preview**.
3. Toward the bottom of the detail view, click the **EDIT** icon.
4. In the Edit a Correlation page, change any of the settings. You can:
   * Make the correlation active or inactive
   * Change the correlation search query
   * Change the correlation type
   * Change the suppression option
   * Edit the details  that explain the problem (summary, attacker, and so on)
   * Add a notification

**To open a list of incidents generated by the correlation:**

1. From the Search page, click the **Correlations** tab.
2. To the right of the notification, click **Preview**.
3. Toward the top of the detail view, click **RESPOND >**. For more information about incidents and responding to them, see [Incidents](../../analyze/incidents.md).

    The ability to review the list is useful for evaluating the correlation criteria as well as responding to the incidents.
