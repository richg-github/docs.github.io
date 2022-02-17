# Saved and Scheduled Searches

The Search experience in the Alert Logic console is intended to allow you to perform basic and advanced searches for different data types. The Search feature is flexible for structuring advanced search queries, and using fields and predefined expressions to help you find and organize  messages most relevant to your investigation.

Alert Logic saves your recent executed searches and allows you to save and schedule any search for frequent use. You must successfully run the search to save and schedule a search. The Saved Searches feature lists all recent executed searches, and recent scheduled searches. You can also view  scheduled search results or export them to a CSV file.

To access the  Search page,  click the menu icon (![](../../Resources/Images/dashboard/menu-icon.png)), and then click ![](../../Resources/Images/dashboard/investigate-icon.png)**Investigate**. Click **Search**, and then click the **Search** tab.

## Saved Searches side panel

From the Search page, you can view your recent executed searches and recent schedules searches, load searches and download search results to a CSV file. Click **Saved Searches** in the Search page to view your recent executed searches and recent schedules searches. From the **Saved Searches** side panel, click the side arrow (![](../../Resources/Images/Icons/input-icon.png)) for the search query you want to load for search. To download search results to a CSV file, click **Download**.

To manage your saved searches, click **Managed saved searches** to be redirected to the **Saved Searches** page. To view a list of all your search results from schedules searches, click **See More** to be redirected to the [Downloads](downloads.md) page.

## Save a search

If the security goals for your organization require you to run specific searches more than once,  you can create a saved search so you can easily find and run the search in the future.

To save a search:

1. On the Search page, enter a valid search query.
2. On the **SEARCH** button, click the down arrow (![](../../Resources/Images/search/down-arrow_21x23.png)), and then click **Save and Schedule Search**.
3. Under Saved Search Details, type a name and description for the search query.
4. (Optional) Under Add Tags, you can tag a search with an existing tag or create a new one to help you organize your searches.
5. (Optional) Under Schedule Search, you can create a schedule for the search query to run automatically. For further instructions, see [Create a search schedule and notification](schedule-searches.md#Create).
6. Under Search Query, make any necessary changes to your search template.
7. Click **SAVE**.

## Create a search schedule and notification

Create a schedule and subscribe users  to receive a notification when the search is complete in the Notifications page.

To create a search schedule and notification:

1. From the **Create a Saved Search** form, toggle the **Create Schedule Search** option.
2. Type a descriptive name for the search schedule—for example, "Security search for security team."
3. If you want the schedule to be active, leave  **Schedule Is Active** turned on. Turn it off if you want to save the schedule but not activate it yet.
4. Specify how often you want to conduct the search:
   * **Once**—Conducts a search at your requested time and date once.
   * **As soon as possible**—Conducts a search immediately.
   * **Every 15 minutes**—Conducts a search every 15 minutes until you cancel this schedule.
   * **Daily**—Conducts a search every day for data from the previous day.
   * **Weekly**—Conducts a search on the day you select for data from the previous calendar week (Monday—Sunday).
   * **Monthly**—Conducts a search on the day of the month you select for data from the previous calendar month.
6. Select the time you want Alert Logic to conduct the search, using the 24-hour clock standard. Alert Logic schedules the search in the time zone reported by your web browser.
If you chose **Once** or **As soon as possible**, you can opt to search for data for the last hour, six hours, 12 hours, 24 hours, seven days, 30 days, or enter an explicit start and end time.
7. Under **Search Query**, make any necessary changes to your search template.
8. Under **Recipients**, to subscribe yourself and other users to receive a notification email, click **Subscribe User(s)**, and then:
   1. Under **Notification Delivery**, select the users that you want to receive the notification. The list includes your name and other user names in the customer account. You can use the search bar to help you find recipients.
   2. (Optional) Customize the **Email Subject**. You can change the text and insert the {{scheduled_search_name}} variable to include the name of the scheduled search.
   3. If you want to send the schedule as a CSV file attachment, select the **Attach CSV File** check box. If you leave it cleared, the email will provide only a link to the Downloads page with the list filtered to display the search generated by the schedule.
   The CSV File search attachment contains a maximum of 500,000 logs. The email attachment is unencrypted and may contain sensitive information about your organization. If a search result is too large to be attached to an email message, a note will be included in the email notification. All results can always be downloaded in full using the [Downloads](downloads.md) page.7. If you want to receive a notification even if the search yielded no results, select the **Receive a notification even if the scheduled search yields no results**.
10. Click **SAVE**.

## View and manage search schedules and notifications

You can view and manage search schedules and their notifications from the **Saved Searches** page in Search. The page shows lists of existing search schedules and  the number of recipients notified when the scheduled search is generated. You can also view a list of saved searches that are not on a schedule.

To execute a saved search:

1. On the Search page, click **Saved Searches**.
2. From the **Saved Searches** list, click the saved search you want to run.
3. Select the search you want to run.
4. Click **SEARCH** to add the saved search.
5. Click **SEARCH**.

### Delete or edit saved and scheduled searches

Alert Logic allows you to make the following changes to saved searches and search schedules you created:

* Delete a saved search
* Edit the search name
* Edit or delete existing search schedules
* Add search schedules

To delete a saved search:

1. On the Search page, click **Saved Searches**.
2. From the **Saved Searches** page, select and expand the saved search you want to delete.
3. Click the delete icon (![](../../Resources/Images/Icons/trash icon.png)) to delete the search.
4. When prompted, click **YES**.

To edit the details of a saved search:

1. On the Search page, click **Saved Searches**.
2. From the **Saved Searches** page, select and expand the saved search you want to delete.
3. edit.
4. Click the edit icon (![](../../Resources/Images/pencil icon.png)) to edit the search.
5. Make changes to any of the following:
   * Name
   * Description
   * Tags
   * Schedule Search (Opens in a separate window)
   * Search Query
7. Click **SAVE**.

To edit a schedule for a saved search:

1. On the Search page, click **Saved Searches**.
2. From the **Saved Searches** page, select and expand the group that contains the saved search you want to edit.
3. Select the saved search with the schedule you want to edit.
4. Click the edit icon (![](../../Resources/Images/pencil icon.png)) to edit the search.
5. Select the schedule you want to edit, and then make changes as described in [Create a search schedule and notification](#Create).
6. Click **SAVE SCHEDULE**.
7. Click **SAVE**.

To delete a schedule for a saved search:

1. On the Search page, click **Saved Searches**.
2. From the **Saved Searches**  page, select and expand the group that contains the saved search you want to edit.
3. Select the saved search with the schedule you want to delete.
4. Click **EDIT SCHEDULES**.
5. Select the schedule you want to delete.
6. Click **DELETE**.
7. Click **SAVE**.

To add a schedule to a saved search:

1. On the Search page, click **Saved Searches**.
2. From the **Saved Searches**  page, select and expand the group that contains the saved search you want to edit.
3. Click the edit icon (![](../../Resources/Images/pencil icon.png)) to edit the search.
4. Select the saved search to which you want to add a schedule.
5. Click **+ ADD SCHEDULE** to specify the frequency for the new schedule, as described in [Create a search schedule and notification](#Create).
6. Click **SAVE SCHEDULE**.
7. Click **SAVE**.

### View and export scheduled search results

The Saved Searches panel lists your recent searches. Click a recently executed scheduled search to perform the following tasks:

* View the results of the search on your screen
* Export the results of the search to a CSV file
