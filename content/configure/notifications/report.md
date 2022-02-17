# Scheduled Reports and Notifications

You can schedule an Alert Logic report to run periodically and receive an email notification when the report is generated. If you need to generate a compliance report on a regular schedule, for example, you can schedule the report and then receive the report or a confirmation that the report generated successfully. Scheduled reports also offer Alert Logic partners a way to generate reports regularly and deliver them to their customers.

Reports generated from schedules are saved and available for review and download. When the report is ready, a notification can be sent to your email, emails of other users, or even a [connector](../connectors.md) like a webhook.

For more information about the Notifications feature, see [Notifications](../notifications.md) and [Manage Notifications](manage.md).

## Create a report schedule and notification

After you set up the report you want to schedule, you can create the schedule and subscribe users and/or a connector to receive a notification when the report is ready.

To create a report schedule and notification:

1. In the Alert Logic console, click the menu icon (![](../../Resources/Images/dashboard/menu-icon.png)).
2. Click ![](../../Resources/Images/dashboard/validate-icon.png)**Validate**,  click **Reports**, and then access the report you want to schedule.
3. From the **Reports** page in the Alert Logic console,  access the report you want to schedule.
4. Set up the report criteria if the report is interactive.
5. Click **SCHEDULE THIS REPORT** to open the Schedule a Report page.
      Some reports such as the Current Vulnerability Finder, List of Vulnerabilities, and Current Vulnerabilities Breakdown cannot be scheduled because they are tabular reports primarily downloaded as CSV files not PDF files.  If the report cannot be scheduled, the option appears grayed out.      Some reports such as the Current Vulnerability Finder  cannot be scheduled.  If the report cannot be scheduled, the option appears grayed out.      7. Type a descriptive name for the report schedule—for example, "Daily Health Summary Report for Security Team."
8. If you want the schedule to be active, leave  **Schedule Is Active** turned on. Turn it off if you want to save the schedule but not activate it yet.
9. Select a report option. Available options can vary according to report contents.
   * **Summary** (PDF File)—Contains the report visualization only in a PDF file
   * **Full (PDF File)**—Contains the full report, including visualizations and any tabular data, in a PDF file.
   * **Data Only (CSV File)**—Contains all data  fields for the report in a CSV file that is compressed with gzip.
   * **Summary and Data (Compressed File)**— Contains the summary report (visualizations only) in a PDF file and the data fields in a CSV file. The files are compressed with gzip.
11. Specify how often you want to generate the report. For reports designed to be generated daily, weekly, or monthly, the frequency is selected for you.
   * **Daily**—Every day, generates the report for the previous day.
   * **Weekly**—Every Monday, generates the report for the previous calendar week (Monday—Sunday).
   * **Monthly**—The first day of the month, generates the report for the previous calendar month.
   * **Weekly**—On the day you select, generates the report for the previous calendar week (Monday—Sunday).
   * **Monthly**—On the day of the month you select, generates the report for the previous calendar month.
   * **Run Once**—Available for non-interactive reports only, generates the report immediately for the period you select. For a monthly report, for example, you can choose to generate a report for the last month or an earlier one.
13. Select the time you want Alert Logic to generate the report, using the 24-hour clock standard. You can schedule some reports only during specific hours to avoid generating an empty or incomplete report. Alert Logic schedules the report in the time zone reported by your web browser.
14. (Optional) Under **Report Settings**, check the report criteria.  This area appears only for interactive reports. If you want to change the settings, click **CANCEL** to go back to the report and change the criteria there. To change the report settings for an existing schedule, set up the report with the new settings, create the schedule, and then delete the old schedule if you want.
15. To subscribe users to receive a notification email, click **Subscribe User(s)**, and then:
   1. Under **Notification Delivery**, select the users that you want to receive the notification. The list includes your name and user names in the customer account. You can use the search bar to help you find recipients.
   2. (Optional) Customize the **Email Subject**. You can change the text and insert variables enclosed with double braces: {{*variable*}}. For the variable list, see [Email subject variables](#Emailsubjectvariables).
   3. If you want to send the report as a PDF file attachment, select the **Attach PDF File** check box. If you leave it cleared, the email will provide only a link to the Downloads page with the list filtered to display the report generated by the schedule.The PDF report attachment is unencrypted and may contain sensitive information about your organization.
   4. If you want to attach the generated report to the email, select the **Attach File** check box. If you leave it cleared, the email provides a link to the Downloads page instead, with the list filtered to display the report generated by the schedule.The report attachment is unencrypted and may contain sensitive information about your organization.
17. To subscribe a connector to receive a notification, click **Subscribe Connector**, and then select a configured connector under **Notification Delivery**. The connector URL will receive the payload listed.
18. Click **SAVE**.

## Email subject variables

To customize the subject line of an email notification, you can add the following variables to the Email Subject field:

| Variable | Description | Example |
|---|---|---|
| {{artifact_create_date}} | Date and time when the report was generated | 2020-05-11 12:00 GMT |
| {{cadence}} | Frequency of report generation and when it is run | Daily, 12:00 GMT |
| {{cid}} | Customer account identifier | 12345678 |
| {{customer_name}} | Customer name of the Alert Logic account where the report was generated | XYZ Corporation |
| {{report_id}} | Report identifier | 20200511-120000-652A6542-D5F7-3E0C-7290-AD4F789B61E0 |
| {{report_type}} | Name of scheduled report as displayed in the Alert Logic console | Daily Health Summary |
| {{schedule_id}} | Schedule identifier | 652A6542-D5F7-3E0C-7290-AD4F789B61E0 |
| {{scheduled_report_name}} | Report schedule name | Daily Health Summary Report for Security Team |

## View and manage report schedules and notifications

You can view and manage report schedules and their notifications from the Notifications page, listed under ![](../../Resources/Images/dashboard/manage-icon.png)**Manage** in the Alert Logic console. To access the Notifications page, click the Settings icon (![](../../Resources/Images/supportThreeDots.png)) in the Alert Logic console, and then click **Notifications**.The Schedules tab on the Notifications page lists existing report schedules and  the number of recipients notified when the scheduled report is generated. A schedule does not appear for non-interactive reports generated with the **Run Once** option.

See [Manage Notifications](manage.md) for information about how to:

* Filter the list
* View report schedule details
* Delete report schedules and notifications
* Edit report schedules and notifications
* View the interactive report related to a schedule
* Open a list of reports generated by a schedule

## View list of generated reports

The Downloads page lists all reports generated by your report schedules. From this page, you can download and manage generated reports. To access the Downloads page, click the Downloads tab on the Reports page.

The list includes all reports in your customer account and its managed accounts. You can narrow the set of reports listed  by using the filters in the left navigation. You can also group and sort the reports with tools available toward the top of the page.

### Filter the report downloads list

The Downloads page lists all reports generated from report schedules. You can  apply filters to narrow the list to a specific set of reports.

To filter the report downloads list:

1. In the left navigation, click any of the filters to narrow the list. Available filters vary according to the schedules in your environment and filters you select.
   * Display—You can use this filter to display the latest reports only.
   * Schedule—You can use this filter to display only the reports generated by a specific schedule
3. To search for a filter, type a filter value in **search filters**. For example, you can quickly find downloads for a specific schedule by typing part of the schedule name.
4. To clear filters and start over, delete text from **search filters** (if applicable) or select **CLEAR ALL FILTERS**.

### Organize the generated report list

In addition to filtering the reports list, you can organize the reports by grouping and sorting the list. Alert Logic groups your reports by report type and sorts them by date within each grouping. You can group and sort the reports by other criteria to suit your needs.

Organizing the list of generated reports is similar to [organizing the report schedule list](#organize).

### Search by date to filter the list

You can use the date range drop-down menu at the top of the downloads list to filter the reports by generation date. Click the menu and then use the calendar to select a date range.

### Download a report generated by a schedule

To the right of the report you want to download, click **Download**. If you select more than one report, the download is a compressed file containing the selected report PDF files.

### Delete reports generated by a schedule

Click the  icon next to one or more reports you want to delete, and then click the **DELETE** icon.

If you want to delete all reports currently listed, select the check box at the top of the list. On the bar that appears at the bottom of the page, click the **DELETE** icon.

## View and manage report schedules and notifications

The Report Schedules page  lists existing report schedules and  the number of users or connectors that receive a notification when the scheduled report is generated. You can view and manage scheduled reports  from this page.

The list includes all report schedules in your customer account and its managed accounts.  You can use filters in the left navigation to narrow the set of report schedules listed. You can also group and sort the schedules with tools available toward the top of the page.

You can click  **View** next to a specific report schedule to see details about and manage the schedule.

For more information, see:* [Access the report schedule list](#access)
* [Filter the report schedule list](#filter)
* [Organize the report schedule list](#organize)
* [Search the report schedule list](#search)
* [View and manage report schedules](#view)

        You can also view and manage report schedules and notifications from the [Notifications page](manage.md).

### Access the report schedule list

From the Reports page, click the **Report Schedules** tab to open the report schedule list.

### Filter the report schedule list

The Report Schedules page displays all active report schedules created from the customer account and its managed accounts. You can also display inactive or deleted schedules, and apply additional filters to narrow the list to a specific set of schedules.

To filter the report schedule list:

1. In the left navigation, click the schedule status of interest:
   * **Active**
   * **Inactive** (schedule is saved but not turned on)
   * **Deleted**
3. Click any of the filters to further narrow the list. Available filters vary according to the schedules in your environment and filters you select.
   * Managed Accounts
   * Recipients
   * Customers
   * Report Category
   * Report Subcategory
   * Report Subcategory 2
   * Schedules
   * Scheduling Cadence
5. To search for a filter, type a filter value in **Search filters**. For example, you can quickly find schedules for a specific report by typing part of the report name.
6. To clear filters and start over, delete text from **Search filters** (if applicable) or select **CLEAR ALL FILTERS**.

To display your own report schedules, you can select yourself as recipient.

### Organize the report schedule list

In addition to filtering the report schedules, you can organize them  by grouping and sorting the list. Alert Logic groups your report schedules by report type and sorts them by date within each grouping. You can group and sort the schedules by other criteria to suit your needs.

To organize your report schedules:

1. To change the grouping, click **Group by**, and then click the option you want. Available options match the filters listed in the left panel.
2. To change the way the list of alert notifications is sorted within each grouping, click **Sort by**, and then click the option you want. Available options include Name, Create Time, and Updated Time. Available options include Date and filters listed in the left panel.

### Search the report schedule list

You can use the Search bar toward the upper-right corner of the page to highlight schedules that contain specific search words. You can search by schedule name, recipients, and filter names.

### View and manage report schedules

You can view the details about a specific report schedule. From the detail view, you can edit or delete the report schedule, view the interactive report from which the schedule was created, and view a list of reports generated by the schedule. Examples of editing capabilities include:

* Make the schedule active or inactive
* Change the scheduling cadence
* Subscribe or unsubscribe users or connector
* Change delivery options

**To view details about a schedule:**

1. From the Reports page, click the **Report Schedules** tab.
2. To the right of the schedule you want to view, click **View**.
3. When you are finished viewing notification details, click **Hide**.

To delete a report schedule:

1. From the Reports page, click the **Report Schedules** tab.
2. To the right of the schedule you want to delete, click **View**.
3. Toward the bottom of the detail view, click the **DELETE** icon.

Deleted notifications are moved from Active to Deleted status.

To edit a report schedule:

1. From the Reports page, click the **Report Schedules** tab.
2. To the right of the schedule you want to edit, click **View**.
3. Toward the bottom of the detail view, click the **EDIT** icon.
4. In the Edit Report Schedule page, change any of the settings.

**To view the interactive report related to a schedule:**

1. From the Reports page, click the **Report Schedules** tab.
2. To the right of the report schedule, click **View**.
3. Toward the bottom of the detail view, click the **VIEW INTERACTIVE REPORT** icon.

**To open a list of reports generated by a schedule:**

1. From the Reports page, click the **Report Schedules** tab.
2. To the right of the report schedule, click **View**.
3. Toward the bottom of the detail view, click the **VIEW PAST REPORTS** icon.
