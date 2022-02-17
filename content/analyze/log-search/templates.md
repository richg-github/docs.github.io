# Create and Manage Search Templates

Alert Logic is offering an improved version of the Log Search feature. To learn more about this feature, see [Get Started with Search](../../get-started/search-a.md).

The Alert Logic console  provides a library of search templates to help you create effective log searches that address the security concerns and goals for your organization. The Alert Logic console allows user accounts with the Administrator role to create and manage search templates to supplement the template libraries for their customer accounts and the customer accounts they manage.

You can create a library of search templates  from effective log searches to help you address specific security concerns and goals for your organization. The Alert Logic console allows user accounts with the Administrator role to create and manage search templates for their customer accounts and the customer accounts they manage.

## About search templates

You have access to all the search templates in the Alert Logic template library, including custom templates created by your account administrators. When you use a search template, you must substitute the placeholder text with values relevant to your search.

You have access to all the search templates in the  template library, which includes all custom templates created by your account administrators. When you use a search template, you must substitute the placeholder text with values relevant to your search.

Templates are organized into groups, which help organize templates by type of search. Use the search field and the template drop-down menu to help narrow down the list of available search templates.

To use a search template:

1. From the Log Search page, click **Templates**.
2. Select and expand the group that contains the search template you want to use.
3. Select the search template you want to use.
4. Click **ADD TO SEARCH**.
5. In the **WHERE** and **SELECT** fields, replace the placeholder text with values relevant to your search.
6. Click **SEARCH**.

After you enter your values into a search template, you can choose to save the search for future use. For more information, see [Create Saved and Scheduled Log Searches](save-schedule.md).

## Move a search template to the trash

You do not permanently delete a template when you move it to the trash. However, only a user account with an Administrator or a Power User role can restore or permanently delete search templates. For more information, see [Administrator tasks](#admin-tasks).

**To move a search template to the trash:**

1. From the Log Search page, click **Templates**.
2. From the **Templates** panel, select and expand the group that contains the template you want to delete.
3. Select the search template you want to move to the trash.
4. Click the trash icon (![](../../Resources/Images/Icons/trash icon.png)).

    Only a user account with an Administrator or a Power User role can restore or permanently delete search templates. Be sure you want to remove a search template before you move it to the trash.     ## Administrator tasks

If your user account has the Administrator role, you can perform the following tasks:

* Create a search template
* Edit a search template
* Restore or permanently delete a search template

### Create a search template

Administrators can create a search template from any valid log search you create or run. When you create a search template, Alert Logic removes and replaces potentially sensitive data with placeholder text to be replaced when a user in your organization uses the template.

To create a search template:

1. After you create a valid search, click the down arrow (![](../../Resources/Images/Icons/arrow-down-icon.png)) on the right side of the **SEARCH** button.
2. Click **Create Search Template**.
3. In the **Create Search Template** panel, provide the following information:
   * Template Name
   * Description
5. Select (or create) a group where you want to save the template.
6. Click **CREATE TEMPLATE**.

### Edit a search template

If your user account has the Administrator role, you can edit search templates created for your organization. Only users with the Administrator role can edit custom search templates. If you are not an administrator, the option to edit a template does not appear. You cannot edit search templates provided by Alert Logic. If you want to customize a search template provided by Alert Logic, you can create a customized search from the template, and then follow the procedure to [Create a search template](#Create).

To edit a search template:

1. From the Log Search page, click **Templates**.
2. Select and expand the group that contains the search template you want to edit.
3. Select the search template you want to edit.
4. In the **Create Search Template** panel provide the following information:
   * Template Name
   * Select (or create) a group in which to save the template
   * Provide a description of the template
6. Click **SEARCH**.

### Restore or permanently delete a search template

If your user account has the Administrator or Power User role, you can permanently delete search templates or restore them from the trash.

**To permanently delete a search template:**

1. From the Log Search page, click **Templates**.
2. From the **Templates** panel, click the drop-down arrow (![](../../Resources/Images/Icons/arrow-down-gray-icon.png) ), and then select **Templates in trash**.
3. Select the group that contains the template you want to permanently delete, and then select the template.
4. Click **TRASH OPTIONS**.
5. Click **Permanently Delete Selected**.
6. Click **PERMANENTLY DELETE**.

To restore a search template:

1. From the Log Search page, click **Templates**.
2. From the **Templates** panel, click the drop-down arrow (![](../../Resources/Images/Icons/arrow-down-gray-icon.png) ), and then select **Templates in trash**.
3. Select the group that contains the template you want to restore, and then select the template.
4. Click **TRASH OPTIONS**.
5. Click **Restore Selected**.

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
