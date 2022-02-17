# Create Saved and Scheduled Log Searches

Alert Logic is offering an improved version of the Log Search feature. To learn more about this feature, see [Get Started with Search](../../get-started/search-a.md).

You can save and schedule any log search for frequent use. To ensure every saved search runs correctly, the Alert Logic console does not allow you to save a search until you enter at least one valid search statement in the search bar and successfully run the search. The Saved Searches feature lists all saved searches in groups created by users in your customer account, and you can run and edit those searches. You can also view  scheduled search results or export them to a CSV file.

## Group options

Alert Logic requires searches and search templates be saved to groups, which help organize searches and templates into logical folders. From either the Saved Searches panel or the Templates panel, you can perform the following actions:

* Create a new group
* Rename a group
* Move a group to the trash

To create a new group:

1. Click **GROUP OPTIONS**.
2. Click **Create new group**.
3. In the group name field, type a name for the group.
4. Click **SAVE**.

To rename a group you created:

1. From the list of groups, select a group to rename.
2. Click **GROUP OPTIONS**.
3. Click **Rename group**.
4. In the group name field, type the new name for the group.
5. Click **SAVE**.

To move a group you created, and its contents, to the trash:

1. From the list of groups, select a group to remove.
2. Click **GROUP OPTIONS**.
3. Click **Move to trash**.				Only a user account with an Administrator or a Power User role can restore or permanently delete a group or the saved searches or templates in the group. Be sure you want to remove a group and its contents before you move it to the trash.

## Save log searches

If the security goals for your organization require you to run specific searches more than once,  you can create a saved search so you can easily find and run the search in the future.

To save a search:

1. On the Log Search page, enter a valid search query.
2. On the **SEARCH** button, click the down arrow (![](../../Resources/Images/Icons/arrow-down-icon.png)), and then click **Save and Schedule Search**.
3. In the **Save Search** panel, type a name and description for the search.
4. Click **Save to group** to select a group into which you want to save the search, or click **CREATE NEW GROUP** to save the search to a new group.
5. Click **SAVE**.

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

    If you want the saved search to follow more than one schedule, click **+ ADD SCHEDULE** and follow the previous steps.     1. Click **SAVE**.

To execute a saved search:

1. On the Log Search page, click **Saved Searches**.
2. From the **Saved Searches** panel, select and expand the group that contains the saved search you want to run.
3. Select the search you want to run.
4. Click **+ SET TO SEARCH** to populate the search fields.
5. Click **SEARCH**.

## Delete or edit saved and scheduled searches

Alert Logic allows you to make the following changes to saved searches and search schedules you created:

* Delete a saved search
* Edit the search name
* Edit or delete existing search schedules
* Add search schedules

To delete a saved search:

1. On the Log Search page, click **Saved Searches**.
2. From the **Saved Searches** panel, select and expand the group that contains the saved search you want to delete.
3. Click the trash icon (![](../../Resources/Images/Icons/trash icon.png)) to delete the search.
4. When prompted, click **MOVE TO TRASH**.			Only a user account with an Administrator or a Power User role can restore a deleted search from the trash. Be sure you want to delete a saved search before you move it to the trash.

To edit the details of a saved search:

1. On the Log Search page, click **Saved Searches**.
2. From the **Saved Searches** panel, select and expand the group that contains the saved search you want to edit.
3. Click the pencil icon (![](../../Resources/Images/pencil icon.png)) to edit the search.
4. Make changes to any of the following:
   * Name
   * Description
   * Group
   * Search schedule
   * Notification email addresses
6. Click **SAVE**.

To edit a schedule for a saved search:

1. On the Log Search page, click **Saved Searches**.
2. From the **Saved Searches** panel, select and expand the group that contains the saved search you want to edit.
3. Select the saved search with the schedule you want to edit.
4. Click the pencil icon (![](../../Resources/Images/pencil icon.png)) to edit the search.
5. Select the schedule you want to edit, and then make changes as described in [Save and schedule log searches and configure notifications](#schedule-and-notify).
6. Click **SAVE SCHEDULE**.
7. Click **SAVE**.

To delete a schedule for a saved search:

1. On the Log Search page, click **Saved Searches**.
2. From the **Saved Searches** panel, select and expand the group the contains the saved search you want to edit.
3. Select the saved search with the schedule you want to delete.
4. Click **EDIT SCHEDULES**.
5. Select the schedule you want to delete.
6. Click **DELETE**.
7. Click **SAVE**.

To add a schedule to a saved search:

1. On the Log Search page, click **Saved Searches**.
2. From the **Saved Searches** panel, select and expand the group that contains the saved search you want to edit.
3. Click the pencil icon (![](../../Resources/Images/pencil icon.png)) to edit the search.
4. Select the saved search to which you want to add a schedule.
5. Click **EDIT SCHEDULES**.
6. Click **+ ADD SCHEDULE** to specify the frequency for the new schedule, as described in [Save and schedule log searches and configure notifications](#schedule-and-notify).
7. Click **SAVE SCHEDULE**.
8. Click **SAVE**.

## Restore or permanently delete a saved search

If your user account has the Administrator or Power User role, you can permanently delete saved searches or restore them from the trash.

**To permanently delete a saved search:**

1. On the Log Search page, click **Saved Searches**.
2. From the **Saved Searches** panel, click the drop-down arrow (![](../../Resources/Images/Icons/arrow-down-gray-icon.png) ), and then select **Trashed searches**.
3. Select the group that contains the saved search you want to permanently delete, and then select the search.
4. Click **TRASH OPTIONS**.
5. Click **Permanently Delete Selected**.
6. Click **PERMANENTLY DELETE**.

To restore a saved search from the trash:

1. On the Log Search page, click **Saved Searches**.
2. From the **Saved Searches** panel, click the drop-down arrow (![](../../Resources/Images/Icons/arrow-down-gray-icon.png) ), and then select **Trashed searches**.
3. Select the group that contains the template you want to restore, and then select the template.
4. Click **TRASH OPTIONS**.
5. Click **Restore Selected**.

## View and export scheduled search results

The Saved Searches panel lists your recent searches. Click a recently executed scheduled search to perform the following tasks:

* View the results of the search on your screen
* Export the results of the search to a CSV file
