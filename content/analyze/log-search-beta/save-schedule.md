# Saved and Schedule Searches

Alert Logic saves your recent executed log searches and allows you to save and schedule any log search for frequent use. You must successfully run the search to be able to save and schedule a search. The Saved Searches feature lists all recent executed searches, and recent scheduled searches. You can also view  scheduled search results or export them to a CSV file.

## Save log searches

If the security goals for your organization require you to run specific searches more than once,  you can create a saved search so you can easily find and run the search in the future.

To save a search:

1. On the Log Search page, enter a valid search query.
2. On the **SEARCH** button, click the down arrow (![](../../Resources/Images/Icons/arrow-down-icon.png)), and then click **Save and Schedule Search**.
3. Under Saved Search Details, type a name and description for the search.
4. (Optional) Under Add Tags, you can tag a search in an existing tag or create a new one to help you organize your searches.
5. (Optional) Under Schedule Search, you can create a schedule for the search query to run automatically. If you want to schedule the search, you will fill out the Create Saved Search Schedule in a different page. For more information, see [Create a search schedule and notification](schedule-searches.md#Create).
6. Under Search Query, make any changes to the search a this time.
7. Click **SAVE**.

## Save and schedule log searches and configure notifications

You can configure any saved search to run at one or more scheduled intervals. When you create a scheduled search, you can specify whether Alert Logic sends an email to you when search results are available, or if a search returns no results.

To save and schedule a search:

1. On the Log Search page, enter a valid search query.
2. On the **SEARCH** button, click the down arrow (![](../../Resources/Images/Icons/arrow-down-icon.png)), and then click **Save and Schedule Search**.
3. In the **Save Search** panel, provide a name for the search.
4. Click **Save to group** to select a group into which you want to save the search, or click **CREATE NEW GROUP** to save the search to a new group.
5. Click **+ ADD SCHEDULE**, and then select values for the following:
   * **Schedule search to run** allows you to select the frequency for the search. The options are:3. **Search time range** allows you to specify a time range from which you want to collect data.
   4. **on each day** allows you to specify the day you want the search to run.
   5. **at time** allows you to specify the time you want the search to run.
      * Every 15 Minutes
      * Hourly
      * Once
      * Daily
      * Weekly
      * Monthly
7. If you want to receive email notification for a search that produces no results, select **Include Zero Result Searches**.
8. Use the search bar to search and add users to receive a notification when the search is complete. The list includes users in your customer account.
9. Click the **Enabled** toggle to specify whether you want email notification of new search results.
10. If you want to receive email notification for  a search that produces no results, select **Include Zero Result Searches**.
11. Click **SAVE SCHEDULE**.

1. Click **SAVE**.

To execute a saved search:

1. On the Log Search page, click **Saved Searches**.
2. From the **Saved Searches** panel, click the saved search you want to run.
3. Select the search you want to run.
4. Click ![](../../Resources/Images/search/arrow.png) to add the saved search.
5. Click **SEARCH**.

## Delete or edit saved and scheduled searches

Alert Logic allows you to make the following changes to saved searches and search schedules you created:

* Delete a saved search
* Edit the search name
* Edit or delete existing search schedules
* Add search schedules

To delete a saved search:

1. On the Log Search page, click **Saved Searches**.
2. From the **Saved Searches** page, select and expand the saved search you want to delete.
3. Click the delete icon (![](../../Resources/Images/Icons/trash icon.png)) to delete the search.
4. When prompted, click **YES**.

To edit the details of a saved search:

1. On the Log Search page, click **Saved Searches**.
2. From the **Saved Searches** page, select and expand the saved search you want to delete.
3. edit.
4. Click the pencil icon (![](../../Resources/Images/pencil icon.png)) to edit the search.
5. Make changes to any of the following:
   * Name
   * Description
   * Tags
   * Schedule Search (Opens in a separate window)
   * Search Query
7. Click **SAVE**.

To edit a schedule for a saved search:

1. On the Log Search page, click **Saved Searches**.
2. From the **Saved Searches** page, select and expand the group that contains the saved search you want to edit.
3. Select the saved search with the schedule you want to edit.
4. Click the pencil icon (![](../../Resources/Images/pencil icon.png)) to edit the search.
5. Select the schedule you want to edit, and then make changes as described in [Save and schedule log searches and configure notifications](#schedule-and-notify).
6. Click **SAVE SCHEDULE**.
7. Click **SAVE**.

To delete a schedule for a saved search:

1. On the Log Search page, click **Saved Searches**.
2. From the **Saved Searches**  page, select and expand the group that contains the saved search you want to edit.
3. Select the saved search with the schedule you want to delete.
4. Click **EDIT SCHEDULES**.
5. Select the schedule you want to delete.
6. Click **DELETE**.
7. Click **SAVE**.

To add a schedule to a saved search:

1. On the Log Search page, click **Saved Searches**.
2. From the **Saved Searches**  page, select and expand the group that contains the saved search you want to edit.
3. Click the edit icon (![](../../Resources/Images/pencil icon.png)) to edit the search.
4. Select the saved search to which you want to add a schedule.
5. Click **EDIT SCHEDULES**.
6. Click **+ ADD SCHEDULE** to specify the frequency for the new schedule, as described in [Save and schedule log searches and configure notifications](#schedule-and-notify).
7. Click **SAVE SCHEDULE**.
8. Click **SAVE**.

## View and export scheduled search results

The Saved Searches panel lists your recent searches. Click a recently executed scheduled search to perform the following tasks:

* View the results of the search on your screen
* Export the results of the search to a CSV file
