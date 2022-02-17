# Create Saved and Scheduled Log Searches

You can save and schedule any search for frequent use. To ensure every saved search runs correctly, the Alert Logic console does not allow you to search or save a search until you enter at least one valid search statement in the search bar. Alert Logic lists all saved searches, and their corresponding groups, created by users in your customer account, and you can execute, edit, and create templates from those searches. You can also view recent searches, recent scheduled results, and search all saved searches.

## Add a template

## Search for a template

## Save a search and save to group

If the security goals for your organization require you to run specific searches more than once,  you can create a saved search and save the search to a group to easily find and run the search. You also have the option to create a new group or a new subgroup to any existing group, and save a search there.

To save a search, save to a group, and schedule:

1. Enter a valid search query.
2. Next to **SEARCH**, click the drop-down arrow, and then click **Save and Schedule Search**.
3. In the **Save Search** slideout panel, provide a name for the search. You can also provide more conceptual information in the **Description** field which serves as your tooltip in the future.
4. Click **Save to group** to see the existing groups, and then choose one. If you want to create a new group or subgroup, see [Create groups](#Create).
5. Click **+ ADD SCHEDULE** to schedule searches and configure notifications, as described in [Schedule log searches and configure notifications](#schedule-and-notify).

## Create groups

## **Create a new group**

Groups allow you to organize and easily find your saved searches. All saved searches must be saved to a group. If no groups exist, you must create one.

**To create a new group**:

1. In the Save Search slideout panel, after you provided a name for the search, click **CREATE A NEW GROUP**, and then type a name for the group.
2. Click **SAVE**.

**To create a subgroup in an existing group**:

1. Click the group where you want to create a new subgroup.
2. Click **CREATE A NEW GROUP**, and then type a name for the subgroup.
3. Click **SAVE**.

## Schedule log searches and configure notifications

You can configure any saved search to run at one or more scheduled intervals. In addition, when you create a scheduled search, you can specify whether Alert Logic sends an email to you when search results are available, or if a search returns no results.

To schedule a search:

1. Enter a valid search query, and then click **SAVE**.
2. In the **Save Search** slideout panel, provide a name for the search.
3. Click **+ ADD SCHEDULE**, and then select values for the following:
   * **Schedule search to run** allows you to select the frequency for the search. The options are:3. **Search time range** allows you to specify a time range from which you want to collect data.
   4. **At time** allows you to specify the time you want the search to run.
      * Every 15 Minutes (which, when combined with email notification, provides near real-time search notifications)
      * Hourly
      * Once
      * Daily
      * Weekly
      * Monthly
5. Click the **Enabled** toggle to specify whether you want email notification of new search results. By default, this selection is turned on.
6. If you want email notification if a search produces no results, select **Include Zero Result Searches**.
7. Click **SAVE SCHEDULE**.

    If you want the saved search to follow more than one schedule, click **+ ADD SCHEDULE** and follow the previous steps.     1. Click **SAVE**.

To perform a saved search:

1. Click **Saved Searches** and select a search.
2. Click **+ ADD TO SEARCH** to populate the search fields.
3. On the log search menu bar, click **SEARCH**.

## Move to trash or edit saved and scheduled searches

You can make the following changes to a saved search and search schedules:

* Move a saved search to the trash
* Edit the search name
* Edit or delete existing search schedules
* Add search schedules

You must be the creator or owner of a saved search you want to edit or delete.

To move a saved search to the trash:

1. Click **Saved Searches** to view recent searches, recent scheduled results, and to search all saved searches.
2. Click the saved search you want to move to the trash.
3. Click the delete icon (![](../Resources/Images/Icons/trash icon.png)).
4. Click **MOVE TO TRASH** to confirm you want to move this search to the trash.

To edit a saved search:

1. Click **Saved Searches** to view recent searches, recent scheduled results, and to search all saved searches.
2. Click the saved search you want to edit.
3. Click the pencil icon (![](../Resources/Images/pencil icon.png)).
4. Make any necessary changes.
5. Click **SAVE**.

To edit a schedule for a saved search:

1. Click **Saved Searches** to view recent searches, recent scheduled results, and to search all saved searches.
2. Click the saved search for the schedule you want to edit.
3. Click **EDIT SCHEDULES**.
4. Select the schedule you want to edit, and then make changes as described in [Schedule log searches and configure notifications](#schedule-and-notify).
5. Click **SAVE SCHEDULE**.
6. Click **SAVE**.

To delete a schedule for a saved search:

1. Click **Saved Searches** to view recent searches, recent scheduled results, and to search all saved searches.
2. Click the saved search for the schedule you want to delete.
3. Select the schedule you want to delete.
4. Click **DELETE**.
5. Click **SAVE**.

To add a schedule to a saved search:

1. Click **Saved Searches** to view recent searches, recent scheduled results, and to search all saved searches.
2. Click the saved search to which you want to add a schedule.
3. Click **+ ADD SCHEDULE** to specify the frequency for the new schedule, as described in [Schedule log searches and configure notifications](#schedule-and-notify).
4. Click **SAVE SCHEDULE**.
5. Click **SAVE**.

## Manage your groups

## Import and export a search query

To import a query:

1. Click **Import Query**.
2. In the slideout panel, drag and drop, or click, to upload a JSON formatted file.
3. After the JSON file successfully uploads, click **SET TO SEARCH**.

### View and export scheduled search results

If you click a recently executed scheduled search, you can perform the following tasks:

* View the results of the search on your screen
* Export the results of the search to a CSV file

**To export a query**:

1. Next to **SEARCH**, click the drop-down arrow, and then click **Export Search Query**.
2. Enter a valid search query.
