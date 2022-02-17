# Import and Export Search Queries

Alert Logic is offering an improved version of the Log Search feature. To learn more about this feature, see [Get Started with Search](../../get-started/search-a.md).

If you need to share search queries with specific users, or store a search query privately for later use, you can use the Import and Export Search Query feature. An exported search query contains query details saved as a JSON file for storage and for ease of sharing electronically.

## Export a search query

After you create a search query, you can either store it for use later, or share it with specific customers. Exported search queries include all information you used as namespace values in the search, including names of assets. If any of those namespace values constitute sensitive data, you should reconsider sharing the exported query file or, if your user account has the Administrator role, you can create a search template from any valid log search you create or run. When you create a search template, Alert Logic removes and replaces namespace values with placeholder text to be replaced when a user in your organization accesses the template.  For more information, see [Create and Manage Search Templates](templates.md).

To export a search query:

1. After you create a valid search, click the drop-down icon on the right side of the **SEARCH** button.
2. Click **Export Search Query**.

The search query file appears in your default download directory as a JSON file starting with <kbd>alert-logic-search-query</kbd>.

## Import a search query

Importing a search query allows you to execute a search from a JSON file that was shared with you.

To import a search query:

1. From the Log Search page, click **Import Query**.
2. In the Import Query panel, either drag and drop a file to upload, or click the upload icon (![](../../Resources/Images/Icons/upload-icon.png)) to browse for the search query file.
3. Click **SET TO SEARCH**., which populates the search fields and allows you to make the following changes, if needed:
   * Edit the search parameters before you execute the search
   * Create Saved and Scheduled Log Searches
   * [Create a search template](templates.md#Create) (if your user account has the Administrator role)
   * [Export a search query](#Export)
5. Click **SEARCH**.
