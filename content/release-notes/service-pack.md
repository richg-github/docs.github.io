#  Service Pack Release Notes

## Cloud Defender service pack release notes 

    2018    ### Release date: August 30, 2018

#### Bug fixes

* A lag in the PCI scan process has been fixed, preventing incorrect compliance scores from appearing early.
* Cloud Defender customers can now see all necessary information about GuardDuty incidents.
* Old links were removed from log message detail pages.
* Several minor fixes were made to the Incident page.

### Release date: August 14, 2018

#### Bug fixes

* The **Events - Full** and **Top Signatures** reports are only showing relevant signature information.
* The legacy Threat Level metric was removed from individual event pages.
* Vulnerability details now display properly on Hosts pages.
* Reference links on the **Incidents** page now open in new browser tabs as expected.
* The right side information menu and bulk actions on the Incidents page have been updated and improved.
* Several display and formatting issues have been fixed.

### Release date: July 3, 2018

#### Bug fixes

* The "Logs: Top 10 Source" report now displays log sources properly.
* The "Top 10 Events Signature" widget no longer displays the Alert Logic IPv6 heartbeat signature.
* If the **More** tab appears on the Contacts &amp; Groups page, the drop-down menu now displays groups.
* If you create a correlation policy and select "Automatically create an Alert," the alert rule now triggers correctly.
* Cloud Defender now saves changes made to existing correlation policies and no longer deletes existing policy settings.
* Alert Logic corrected an issue where, if you edited a correlation rule, made no changes, and then saved the rule, values originally selected for **Properties and Fields** and **Conditions**, no longer appeared.
* The Log Management Dashboard widget for Log Sources now displays Office 365 sources.
* The Schedule a Scan page no longer contains a reference to the deprecated Alert Logic console Management feature.
* The PCI scan disputes form now accepts special characters in policy names.
* The S3 policy slide-out panel now displays the date format correctly if you select "Parse times from messages using a pre-defined timestamp format."
* "Windows Event Log Source" now appears in the **Source Log Type** field of the Log Sources page.
* If you set up a manual scan from the Cloud Insight Dashboard page, the host will not appear in the **Scanned** column until the scan completes.
* Exports of protected hosts or log sources to a CSV file now include all hosts.
* If you have managed accounts, the name of one of your managed accounts no longer briefly appears as the account name.
* The Protected Hosts page and the Appliances page now display enough useful, at-a-glance information about the listed assets.
* The CIO Report no longer includes evolved incidents in the calculation for "incidents created."

### Release date: May 29, 2018

#### Features

* This release includes new names for some items under the Deployments page to make navigation easier. The items in the left side navigation are now **Hosts**, **Log Sources**, **Networks and Protected Hosts**, **Log Collectors**, and **IDS Appliances**.

#### Bug fixes

* The mass archive option on the **Log Sources** page was corrected to work as expected.
* O365 log sources now load properly for editing.
* A list of log sources or protected hosts exports as expected, with all information and filters retained.
* The **Scans** page now notes when a scan was aborted by the user.
* The **Force Statistics Update** option is now available in **the Log Sources** list.
* Several display and formatting issues have been fixed.

### Release date: May 15, 2018

#### Features

* This release adds a service status page. The page is available at [status.alertlogic.com](https://status.alertlogic.com/), and you can also access it from the **Service Status** link on the login page or the **Service Status** option under the Support menu. For more information, refer to [this Help Center article](https://support.alertlogic.com/hc/en-us/articles/360003919052-05-16-18-New-Alert-Logic-Status-Page).
* This release adds a feature to the Support page that allows users to search deployments and view each deployment ID.
* This release expands archival functionality to protected hosts. New features include:
   * Click the slider at the top of the protected hosts list to view archived or unarchived hosts.
   * Click the archive icon (![](../Resources/Images/Icons/CaseIcon.png)) to archive a host
   * Click the unarchive icon (![](../Resources/Images/Icons/unarchive.png)) to unarchive a host.

#### Bug fixes

* This release clarifies messages that display when a deployment has an error.
* This release resolves an issue with data exported to appliance reports and log message reports.
* This release resolves cosmetic issues with page layout on whitelist policy details and the Log Messages page.
* This release resolves an issue with the centralized cloudtrail log collection status slider in a deployment.

### Release date: May 3, 2018

#### Features

* This release adds a batch editing feature for scan vulnerabilities. When you select multiple vulnerabilities, you can change the status of all of them at once.
   * To change the status of several vulnerabilities at once:
   * Select either **Only active** or **Only inactive** for the **Status** at the top of the vulnerabilities list.
   * Select two or more vulnerabilities in the list.
   * Click Change Status at the bottom of the list.
   * In the menu that appears, you may choose to change the status of these vulnerabilities for **This Host** or **All Hosts**, and you may change the status to **Active** or **Inactive**.

#### Bug fixes

* This release resolves an issue with log retention period information. The log retention period is now listed on the Support Information page.
* This release resolves a display issue with scan results. All scan results in PDF format now open in a new tab. You may view, save, or print the results form the new tab.
* This release resolves an issue with CIDR format validation on the Networks and Hosts screen. The console now validates your CIDR addresses as you type, so that you can correct any formatting issues before submitting the form.

### Release date: April 25, 2018

#### Bug fixes

* This release resolves an issue with updating agent policies. The issue is resolved and users can create and update agent policies as normal.
* This release resolves an issue with events, incidents, and blocking alert rules. To access the pages, click **CONFIGURATION**, then click **Notifications**, and then select the type of alert rule you want to create.
* This release resolves cosmetic issues with page layout on several configuration screens, and the Zones and Host Groups screens.
* This release resolves an issue that redirected users when they clicked a link to an incident.
* This release resolves an issue with updating block requests in the incidents panel.
* This release updates an error message that appears when a read-only user tries to access unauthorized tools or content.
* This release resolves an issue with list filters on the sources pages. All filters appear as intended now.
* This release resolves an issue with a link in the PCI Dispute system.

#### Features

* This release adds a time zone selection field to the **New Source** menu. You must choose a time zone to create a source.

#### Security

None

#### Changes

None

#### Notice

None

### Release date: April 20, 2018

#### Bug fixes

* This release resolves an issue where Azure deployments did not show protected hosts associated with the deployment.
* This release resolves cosmetic issues with page sizing and scrolling.
* This release resolves an issue in the menu to add a new certificate. For some users, the menu timed out before they were done filling in all the information. This issue has been resolved.
* This release resolves an issue with the **Save** button on the correlation policy and flat file log sources screens for certain deployments. The Save button now displays and works as expected.

#### Features

* This release adds a feature that displays the full name of the account you are viewing in the Alert Logic console.

#### Security

None

#### Changes

None

#### Notice

None

### Release date: April 17, 2018

#### Bug fixes

* This release resolves an issue with user time zone settings.
* This release resolves an issue where the host metadata displayed the private IP as a public IP.
* This release resolves an issue with viewing log messages within cases.
* This release resolves compatibility issues with Internet Explorer version 11.
* This release resolves an issue that caused the Alert Logic console to display an error when users tried to turn a host into a protected host.
* This release resolves an issue with appliances and agents filtering on Azure deployments.
* This release resolves an issue where metadata was missing on some log sources.
* This release resolves an issue with the **Save** button on the correlation policy editing screen.

#### Features

* This release adds a feature that allows users to select the customer account they want to use in the **Statistics** tab of **Scans**.

#### Security

None

#### Changes

None

#### Notice

None

### Release date: week of April 9-13, 2018

#### Bug fixes

* This release resolves an issue with retrieving SSL certifications.
* This release resolves an issue with the search function.
* This release resolves a cosmetic issue with the layout of the **Scans****Dashboard** page.
* This release resolves an issue with the reporting system in the Alert Logic console. All users can now access reports normally.
* This release resolves an issue with the forgotten password link on the login page.
* This release resolves an issue with incident and event counts on the dashboard pages. All counts are now accurate.
* This release resolves an issue with cached pages causing certain links to redirect users. The issue is resolved, and all links and navigation tools work as expected.
* This release resolves issues where the Alert Logic console did not work normally for users who accessed it from certain browsers. The issue is resolved, though if you continue to experience issues, use Google Chrome.
* This release resolves an issue where an internal Alert Logic feature appeared to customers as a dead link. The link no longer appears for non-Alert Logic users.
* This release resolves an issue where users could view data on the **Scan** dashboard for all accounts for which the user had access. The issue is resolved, and customers now only see data for the selected account.

#### Features

* This release adds multiple ID numbers to identify incidents and events.
* This release adds a feature that allows allowing users to easily share links to events.
   * In the Alert Logic console, click **SEARCH**, and then click **Events**. In the list that appears, find the event you want to share, and then click the share icon (![](../Resources/Images/Icons/share.png)) in the **Share** column. A new browser tab opens and shows event details. The URL in the new tab is a direct link to the event details page.
   * You may also click an event to view the event details page. From the event details page, click the share icon (![](../Resources/Images/Icons/share.png)) at the top of the page. The A new browser tab opens, and the URL in the new tab is a direct link to the event details page.

#### Security

None

#### Changes

None

#### Notice

None

### Release date: March 20, 2018 (UK); March 27, 2018 (US)

#### Bug fixes

* This release resolves an issue where customers could fill out a scan dispute form, and receive a success message if they did not submit the form. This release displays a message that directs customers to click "Submit For Review" to complete and send the dispute form.
* This release provides PCI customers with full details of a vulnerability if the description is too long to display on the screen. You can now click the description to read the full details of a vulnerability.
* This release resolves an issue in which the Threat Manager licensing page displayed incorrect average volume information. With this release, all information on the licensing page displays accurately.
* This release resolves an issue in which no CIDR/subnet validation occurs when you enter networks in Threat Manager.
* This release resolves in issue in which the check box to send an email report did not appear selected if the only notification contact was a group. With this release, the check box always displays as expected.
* This release resolves an issue in which the Web Security Manager Activity Report did not load if you used outdated Web Security Manager rule names. This release allows the use of older names and displays the report correctly.
* This release resolves an issue in which PCI scans with low vulnerabilities were categorized as "Not-Compliant" and had to be disputed. With this release, Cloud Defender categorizes low vulnerabilities correctly, so disputes for those scans are no longer required.

#### Features

None

#### Security

None

#### Changes

None

#### Notice

None

####  

### Release date: February 22, 2018 (UK); March 1, 2018 (US)

#### Bug fixes

* This release resolves an issue where automatically closed disputes displayed an incorrect status of "Pending Review." Automatically closed disputes now display the status "Finished Failing."
* This release resolves an issue where comments in the Overview page of Scan Dispute displayed the customer name instead of the user name. The comments now correctly display the user name.
* This release resolves an issue where the PCI Executive Summary Report listed the scope twice, and one scope displayed the incorrect status. The scope now appears only once, and with the correct status.
* This release corrects text on the Schedule PCI Scan page. "Hostnames must have no URL paths attached." was corrected to say "Hostnames may have URL paths included."
* This release resolves an issue in which Scan Schedule did not work on the last Day of the Month for the CDT Timezone. The Scan Schedule feature now works with any scenario.
* This release resolves an issue in which IP validation did not fail when a CIDR IP included a semicolon or any other special  character at the end
* This release resolves  an issue where the Log Executive Summary Report included Threat Manager sources. The report now only uses Log Manager sources.
* Prior to this release, the New Source creation form displayed inapplicable items. With this release, only applicable items appear.
* This release resolves an issue where customers could not save Threat Manager configurations on newly spun up appliances. With this release, Threat Manager configurations can be saved, even if the appliance does not have a monitoring policy.
* This release resolves an issue where conditions with values of 0 in a created or edited correlation policy were not saved. With this release, you can use conditions with values of 0 and they will save with your correlation policies.

#### Features

None

#### Security

None

#### Changes

None

#### Notice

None

### Release date: January 11, 2018 (UK); January 18, 2018 (US)

#### Bug fixes

* This release adds a disclosure document to the PCI scan status page to keep up with ASV qualification requirements.
* This release resolves an issue where CSV file downloads were truncated, resulting in missing information. They now download as complete files.
* This release resolves an issue with pagination of search results in the Vulnerability lists.
* This release resolves a display issue with sidebar information in Internet Explorer.

#### Features

None

#### Security

None

#### Changes

None

#### Notice

None

    2017    ### Release date: November 9, 2017 (UK); November 16, 2017 (US)

#### Bug fixes

* This release resolves an issue in which the most recent Amazon Web Services (AWS) regions did not appear as options during CloudTrail source setup. This release includes the following AWS regions:
   * US East (Ohio) - us-east-2
   * Canada (Central) - ca-central-1
   * Asia Pacific (Mumbai) - ap-south-1
   * EU (London) - eu-west-2
* This release resolves an issue in which the CloudTrail "Top 10 Users" widget appeared blank. With this release, the widget displays as expected.
* This release resolves in issue with the quarterly scan schedule. Before this release, under certain conditions, the "next scheduled date” for a quarterly scan would display an incorrect date. With this release, the next scheduled scan displays the correct date.
* This release resolves an issue in which the Event Monitor data displayed in the Alert Logic console differed slightly from the data displayed in the Event Executive Report. With this release, the data in the Alert Logic console matches the data in the Event Executive Report.

#### Features

This release introduces the Scan Variance Report, which highlights the differences between a prior report, and the current status report.

#### Security

None

#### Changes

None

#### Notice

None

### Release date: October 12, 2017 (UK); October 19, 2017 (US)

#### Bug fixes

* This release fixes an issue where on the PCI Scans Results UI page, the Executive Summary report was showing incorrect data under Part 2. Component Compliance Summary. This was solved and the Executive Summary report is showing the correct information now .
* This release fixes an issue where there were discrepancies in number of Incidents reported under Incidents By Time compared to the full report. The was corrected and the number of incidents now matches with the number of incidents reported in the full report
* In Log Manager*/Messages/Schedule Saved View*, the automatic case closing functionality was not working. This was corrected and the functionality now works as expected.
* The PCI Compliance Tab on the Scans page in the Alert Logic console was erroneously showing a dispute status of Pending Completion or Pending Dispute Results for some disputes. This was corrected and the dispute status now shows correctly.
* This release fixes an issue where PCI customers could not attach files to disputes before submitting them. This was corrected and files can now be attached.
* This release fixes an issue where reports containing a massive amount of data were failing to export into the new Excel format. This was corrected by splitting the exported files into multiple files (the number of files depends on the amount of data contained).
* This release fixes an issue where the schedule option *As soon as possible* incorrectly appeared for external scans. This option is not available for external scans, and was corrected so the option no longer appears.
* This release fixes an issue where the Alert Logic console was not showing the detailed information for Log Manager sources. This was corrected and the detailed information now appears.
* This release fixes an issue where the quick action bar in the Log Manager message search tool did not display on certain low resolutions. This was corrected and now the quick action bar displays in all resolutions.
* This release fixes an issue where the Host / Source count was disappearing from the console after clicking to Show More. This was corrected.
* This release fixes an issue where adding new whitelists in the Firefox browser when there is a long list of rules fails. This was fixed.

#### Features

None

#### Security

None

#### Changes

* Support for mass editing Threat Manager Hosts is now available.
* The Monitor Settings option on the Threat Manager Policies page is no longer supported. This option was removed.

#### Notice

None

### Release date: September 14, 2017 (UK); September 21, 2017 (US)

#### Bug fixes

* This release resolves an issue in the appliance tab in the log source menu. The tab now displays all the necessary information and scrolls as expected.
* This release resolves an issue with deployment icons. The icons are now corrected for all deployment types.
* This release resolves an issue with long searches in Saved Views. The notification dialog now displays correctly.

#### Features

None

#### Security

None

#### Changes

None

#### Notice

None

### Release date: August 31, 2017 (UK); September 7, 2017 (US)

#### Bug fixes

* This release resolves an issue in which the time stamp on the Events by Time report did not display the correct local time. The customer's local time now displays in the report.
* This release resolves an issue with PCI scan disputes that caused an error when you select multiple items. With this release, you can now select multiple items when you submit a PCI scan dispute.
* With this release, an error icon no longer appears if a scan reveals no vulnerabilities.
* This release resolves an issue in which license limits were incorrectly calculated when scan targets included FDQN and numbers in the domain name, and then displayed an error. With this release, those scans can run without error.
* This release allows you to select multiple list items on the Hosts and Sources page.
* The All Deployments page now correctly displays headers and icons.
* The Threat Manager Protected Networks page now allows you to copy and paste a list of CIDRs.
* The Accounts page now displays the correct navigation menu.
* This release removes an unnecessary **Cancel** button from the Manual Deployments page.
* This release corrects display issues on the Threat Manager Appliances page for manual deployments.
* This release resolves an issue on the My Account page in which the correct time zone did not display until you selected the time zone a second time.
* This release resolves an issue with Threat Manager in which whitelist policies were missing a complete CIDR validation.
* This release resolves an issue with Log Manager correlation alert rules in which a new form did not accept the false value by default and resulted in a validation error. With this release, the correlation alert rule form functions as expected.

#### Features

None

#### Security

None

#### Changes

None

#### Notice

None

### Release date: August 3, 2017

#### Bug fixes

* This release resolves an issue where the Historical View of Vulnerabilities report displayed information from deleted hosts. After this release, the Historical View of Vulnerabilities no longer includes hosts that were deactivated before the report start date.
* This release corrects an issue in Log Manager where policy names for log sources did not appear on the Sources page. With this release, policy names appear in the Policy column on the Sources page.
* This release corrects an issue on the Log Manager S3 Policies page where the **Show More** button did not display the expected policies. With this release, the button works as expected.
* This release resolves an internal server error that occurred in Threat Manager when customers saved certificates. With this release, the feature works as expected.
* This release fixes an issue in which an edited and updated PCI scan scope appears in the scan report, but displays results based on previous scan scope. With this release, the feature works as expected.

#### Features

None

#### Security

None

#### Changes

* This release features an improvement to the loading speed of the Reports page.
* This release removes the deprecated **Only scan hosts not found before** option from the Quick Scan page under Management.

#### Notice

None

### Release date: July 18, 2017

#### Bug fixes

* This release fixes an issue where PCI Compliance reports could be downloaded for reports that failed to run. This was corrected and report links are no longer available for reports that failed to run.
* A warning text was put in the comment section when trying to attach files to a dispute to inform the user that a comment is required before pressing the ‘add comment’ button.
* This release adds expected form field validation. Users can see the form field errors when adding certificates in the new Alert Logic console.
* This release fixes an issue where Threat Manager appliance scan enable status did not work correctly in the new Alert Logic console. This has been corrected and the scanning status of the appliance now works as expected.
* This release fixes an issue where users could select an invalid appliance for Cloud Defender fast scans. This has been corrected and users may no longer select invalid appliances.

#### Features

* Sorting functionality has been added to the existing entity list in Threat Manager and Log Manager in the new Alert Logic console.

#### Security

None

#### Changes

* The zero state has been changed when no results are found on the search. This affects all lists in the new Alert Logic console.

#### Notice

None

### Release date: July 6, 2017

#### Bug fixes

* This release resolves an issue in the Message Contexts and Message Types sections of the Log Manager data security manager. When there is no data to show, the console displays "no items" instead of "Loading."

#### Features

* This release adds a feature that makes PDF vulnerability reports more manageable. Large reports are now split into multiple sections.
* This release adds a CIDR validation check in Threat Manager. The console now displays an error message if the CIDR format is invalid.
* This release adds the functionality of the Security Content Center to the updated Alert Logic console.

#### Security

None

#### Changes

None

#### Notice

None

### Release date: June 22, 2017

#### Bug fixes

* This release resolves an issue with the Top Incidents module on the Dashboard page. The module was displaying the old Threat Levels for incidents (used prior to the NGX system).  This issue was fixed.
* This release resolves an issue where the Top 10 Vulnerabilities section displayed differing information in the ranking graph and the vulnerability details section.
* This release resolves an issue where customers could set a Threat Manager appliance Zone ID to 0, which prevented the sensor from sending events to the backend. This issue was fixed, and customers can no longer set the Zone ID to 0.

#### Features

* This release adds support for TLS 1.2 to establish connections to SCC when downloading agent images through the Alert Logic console.
* This release improves the performance on the sensor management page.

#### Security

None

#### Changes

None

#### Notice

None

### Release date: May 25, 2017

#### Bug fixes

* This release resolves an issue with failed responses from RIPE. With this release, the UI will display the message: "RIPE: The request was denied."
* This release resolves an issue with the Notifications History page when using Internet Explorer 11. With this release, the customer can now see the Alert Details on the page.
* This release resolves an issue with the notification dialog. With this release, the customer can now search contacts by either name or email. Additionally, the dialog will validate whether the email already exists (preventing duplicated contacts).
* This release resolves an issue with HIPAA reports showing suppressed incidents. With this release, Threat Manager customers no longer see suppressed incidents, instead they can only see  real incidents.

#### Features

None

#### Security

None

#### Changes

None

#### Notice

None

### Release date: May 11, 2017

#### Bug fixes

* This release resolves an issue with several content-type headers that were corrected on console.clouddefender.alertlogic.com. This release improves the WAF protection of the UI.
* This release resolves an issue with the Cogwheel for the dashboard tab. With this release, the tab was fixed for Threat Manager and Log Manager.
* This release resolves an issue with the item "Event Export By Malware and SQL Injection Attempts." With this release, the item is now displaying correctly in the report's page.

#### Features

None

#### Security

None

#### Changes

None

#### Notice

None

### Release date: March 30, 2017

#### Bug fixes

* This release fixes an issue where an error message shows when an invalid host is entered, but it does not say which host is invalid. The error message now shows the invalid host.
* This release fixes an issue where the Notification History page did not load as expected in Internet Explorer. This was corrected and the Notifications History page now works as expected for Internet Explorer.
* This release fixes an issue where the Excel export of a filtered incident search contained all the events of the parent CID and not just those filtered. This was corrected and the Excel export now shows the same information as the filtered incident search.
* This release fixes an issue where the UI Events page failed to display the Signature content and the Payload field content was difficult to read due to the format. The header and payload information format is now corrected and the Signature Content field, if content is available, now displays.
* This release fixes an issue where customer or save comments in PCI vulnerabilities report were difficult to read. Line breaks now exist, making the comments easier to read.

#### Features

None

#### Security

None

#### Changes

* For open disputes, a notification is sent out to a customer after 3 days of customer inactivity saying that the dispute will be closed in another 7 days.
* A support icon has been added next to both scans and individual results. When a customer clicks the icon, a support email is created with the recipient, subject, and email body auto-populated with pertinent information.

#### Notice

None

### Release date: March 16, 2017

#### Bug fixes

* This release fixes an issue where the Web Security Manager prompted for access credentials for OOB WAFs and then failed to grant access. Web Security Manager no longer asks for the unnecessary credentials and functions correctly.
* This release fixes an issue where the “Items in Case” displayed incorrectly in the Incidents monitor in the Alert Logic User Interface. The widget now displays correctly.
* This release fixes an issue where the Security Content Center would not reload a page after a 10-minute inactivity timeout. Now if you try to access any page in the Security Content Center after 10 minutes of inactivity, you are redirected to the cloud defender Summary Page.
* This release fixes an issue where different results were obtained for a Saved View between the Log Messages interactive search and the scheduled execution in PDF and CSV reports.  This was corrected.

#### Features

None

#### Security

None

#### Changes

* Removed two obsolete features from Cloud Defender user permission options.

#### Notice

None

### Release date: March 2, 2017

#### Bug fixes

* This release resolves an issue where the option “Parse times from messages using a custom timestamp format” in create/update policy was not working.  This was corrected.
* This release resolves an issue where the "Management -> Appliances" page listed NGTM along with legacy appliances. NGTM are no longer listed here.
* This release resolves an issue where the Time zones in the log sources export file were inconsistent. When the time zone was not detected correctly, the US/Central or America/Chicago were used as a default value, which made the field confusing. This was changed to leave the field blank in this scenario.
* This release resolves an issue where the analyst’s name was not displaying in the Vulnerability Comments. The analyst’s name now displays in the comment.
* This release resolves an issue where customers could not find the “Submit for Review” function in the New Dispute System. The instructions on the green bar are now consistent with the status of the dispute and with every step of the dispute process.

#### Features

None

#### Security

None

#### Changes

* The messages under TM -> Networks -> Protect Network are now more consistent and less confusing.
* Access to S3 and Azure pages in Log Manager is now granted based on the “modify log policy” permission option.
* New Dispute System Error message was changed to provide more meaningful error messages.
* An e-mail address is now required in the form when a user is starting a dispute.
* The customer selector on the PCI Compliance Tab now works exactly like the customer selector on the Scans Tab.

#### Notice

None

### Release date: January 31, 2017

#### Bug fixes

* This release resolves an issue with the Appliances section on the Management page. All users now have access to the section, regardless of zone restriction status.
* This release resolves an issue with the Messages page in Log Manager. Searching by the "Server Real Port" token now works as expected.
* This release resolves an issue with the tag filtering in the block monitor page. The filter now works as expected.
* This release resolves several labeling issues. The former Platforms page is now titled Deployments, and the Azure role creation page now reads "Log in to your Azure account."

#### Features

None

#### Security

None

#### Changes

None

#### Notice

None

### Release date: January 19, 2017

#### Bug fixes

* This release resolves an issue with the search function on the Host page. This issue has been corrected and the system now works as expected.

#### Features

* This release adds the ability to add Azure environments to Cloud Defender.The software now fully supports adding and managing Azure environments.
* This release adds a validation for date and time entries in the Monitor page. The system now checks to make sure that dates and times are entered correctly.
* This release removes the deprecated **Advanced** option from the Event alert rules page.

#### Security

None

#### Changes

None

#### Notice

None

### Release date: January 10, 2017

#### Bug fixes

* This release resolves an issue and improves performance in the Incident Monitor.  The system sent a high number of queries to the database, which resulted in a high event count. This issue has been fixed and event counts are now accurate.

#### Features

None

#### Security

None

#### Changes

* This release improves performance in the Case Monitor.  Several internal database queries were optimized and the way that PHP code retrieves and organizes the data was refactored.

#### Notice

None

### Release date: January 5, 2017

#### Bug fixes

* This release resolves an issue where edits to current dispute comments could change historical disputes. This was fixed and the feature works as expected.
* This release resolves an issue with the Incidents page trying to load too many rows on a page. The maximum number of rows for the page is now 50.
* This release resolves two issues in the incident monitor. Issues with filtering by tags and  by multiple summary values have been fixed, and filtering now works correctly.
* This release resolves an issue with graph generation in reports. Graphs with long label names were interfering with report generation. This issue has been fixed and long label names are accepted.
* This release resolves an issue with time zone consistency between No Logs reports in the UI and exported versions. This has been fixed and the time stamps are all consistent with the user's time zone.
* This release resolves an issue with the Log Source - Last Collected report. The report was pulling in Threat Manager sources, but that has been corrected and only Log Manager sources are included now.
* This release resolves an issue with the Message Volume by Week widget. Some totals were not displaying properly with a custom date range.
* This release resolves an issue with an extraneous error message that appeared while generating reports. The issue has been fixed and the error message is removed.

#### Features

* This release removes the ability to create an incident from an unparsed log source.
* This release updates the notification preferences menu. There are now settings for receiving notifications **always**, **never**, **per hour**, and **per day**, and you can limit the number of notifications per hour and per day.
* This release renames the UI to Cloud Defender instead of Invision.

#### Security

None

#### Changes

None

#### Notice

None

    2016    ### Release date: December 7, 2016

#### Bug fixes

* This release resolves an issue with the Log Manager Saved View scheduling and Reports scheduling. The issue would occur when a customer added a recurring schedule to a saved view or report and would select the weekly recurrence. The system would execute the report on the wrong weekday if the customer time zone was different from the application time zone (CST). Development has fixed this issue.
* This release resolves an issue with the Log parser in Log Manager. It now handles literal tokens correctly.
* This release resolves an issue with the Log Manager Messages export. The export was not working for Internet Explorer. Development has fixed this issue.
* This release resolves an issue with customers not receiving email notifications for manually created incidents.
* This release resolves an issue with Cloud Defender. The Cloud Defender UI was not accepting URL A records for PCI scans.

#### Features

None

#### Security

None

#### Changes

* This release changes the File Name Rotation Scheme selection for Log Manager Flat File policies. The customer will be able to enter a custom pattern using the new field.
* This release changes the Host and Port fields in the Certificates and Keys page for Threat Manager. Development has removed the Host and Port fields from the Create Certificate form as they are no longer used.

#### Notice

None

### Release date: December 1, 2016

#### Bug fixes

* This release resolves a Daylight Saving Time (DST) issue with the Threat Manager and Log Manager widgets in the UI Dashboard.
* This release resolves an issue in the New Correlation form for Log Manager Correlation Policies. When setting the time for triggering messages, if the customer enters a time below 10 minutes they will receive an error message. Before the fix, the error message was expressing the time value in minutes even if the customer entered the time in seconds. Development has fixed this issue and the error message now expresses the time value according to the customer selection, whether minutes or seconds.
* This release resolves an issue with the Web Security Manager Deny Logs page. The Detail button would not show if the browser window was re-sized. Development has fixed this issue and the button now shows correctly.
* This release resolves an issue with the UI Dashboard. In some cases a new widget added to the Dashboard would save to an incorrect module. This bug has now been fixed.

#### Features

None

#### Security

None

#### Changes

* This release changes the styles for the filters at the bottom of the incidents list on the Incidents page.

#### Notice

None

### Release date: November 10, 2016

#### Bug fixes

* This release resolves an issue where parent accounts with management permissions could not access or manage Log Manager collectors or Log Manager hosts in their child accounts.
* This release resolves an issue where customers could not edit individual tags for protected hosts.
* This release resolves an issue in which the Custom Port selection of the Port Scan page listed incorrect values.

#### Features

None

#### Security

None

#### Changes

* This service pack allows you to associate collection alert rules with “Networks.” This improvement allows alerts to be triggered according to the status of the specified network.

#### Notice

None

### Release date: October 27, 2016

#### Bug fixes

* This release resolves an issue where the “Rate This Incident” pop up appeared behind the Incident details in the UI.  The “Rate This Incident” pop up now appears in front of the Incident details in the UI.
* This release resolves an issue where Incident class section at the bottom of the Configure page for Blocking Configuration failed to load after more than 16384 signatures were added to the Signatures section. The Blocking Configuration page (Policies section) no longer fails when the user adds more than 16,384 signatures.

#### Features

None

#### Security

None

#### Changes

* The UI Search field in the Threat Manager > Policies > Protected Host page now has a three-character minimum.
* An option to associate Threat ManagerCollection Alerts rules with appliances allows the reception of alerts based on the appliance's status.
* It is now possible to configure Collection Alert Rules for Protected Host and/or Appliances in Threat Manager. An option for target type is added in the 'Collection Alert Rule form' to configure alerts according to the target type.

#### Notice

None

### Release date: October 27, 2016

#### Bug fixes

* This release resolves an issue where the “Rate This Incident” pop up appeared behind the Incident details in the UI.  The “Rate This Incident” pop up now appears in front of the Incident details in the UI.
* This release resolves an issue where Incident class section at the bottom of the Configure page for Blocking Configuration failed to load after more than 16384 signatures were added to the Signatures section. The Blocking Configuration page (Policies section) no longer fails when the user adds more than 16,384 signatures.

#### Features

None

#### Security

None

#### Changes

* The UI Search field in the Threat Manager > Policies > Protected Host page now has a three-character minimum.
* An option to associate Threat ManagerCollection Alerts rules with appliances allows the reception of alerts based on the appliance's status.
* It is now possible to configure Collection Alert Rules for Protected Host and/or Appliances in Threat Manager. An option for target type is added in the 'Collection Alert Rule form' to configure alerts according to the target type.

#### Notice

None

### Release date: October 13, 2016

#### Bug fixes

* This release resolves an issue with Chrome users experiencing black text on a black background in the Report section’s datepicker selectors.  This has been fixed to ensure users have the same cross-browser experience.
* This release resolves an issue where it was not possible to add tags to a protected host in Threat Manager using the mass edit functionality. It is now possible to add tags to a protected host using the mass edit functionality.
* This release resolves an issue where the gear icon of the Action column in Treat Manager Protected Host and Appliances stays over the Action text. The icon appears correctly now.
* This release resolves an issue with editing existing log collection policies in the UI. This fix solved the issue and the edit action works properly now.
* This release resolves an issue when a User clicked on an AWS Marketplace account activation expired link, a product performance issues message was displayed. An expired link message now displays.
* This release resolves an issue where the AWS Marketplace Signup form would not allow a period in the Company field.  It is now possible to enter a period in the Company field.
* This release resolves an issue where CIO Threat Trend Report sections "Active Vulnerabilities" and "Remediated Vulnerabilities" were not filtering data according to the Zones and/or Hostgroups selected, and the "Active Vulnerabilities" section was shifting the data to the left in some situations, causing counts to not match with the correct Risk level titles.  These issues were corrected so that both sections now work as expected

#### Features

None

#### Security

None

#### Changes

* Two new options were added for the “File Name Rotation Scheme” field in the Flat File Policy page of the UI. Also, “Increasing and Decreasing options are only supported by agent version 2.2.0 and above” was added into the information icon text for that field.
* The text in the AWS Marketplace Signup Form for Threat Manager with ActiveWatch was updated to clarify signup.
* Descriptions in CIO Threat and CIO Threat Trend reports were updated to clearly inform users the kind of data being reported.

#### Notice

None

### Release date: September 29, 2016

#### Bug fixes

* This release resolves an issue with potentially confusing label in TM/Alert Rules/Collection Forms. The label “Time Without Data” was renamed “Time Before Alert is Triggered” to avoid confusion when the Alert Type is different than “Collection”.
* This release resolves an issue where Grandchildren under incident evolution were not being closed when the most evolved incident was. Children and grandchildren are now closed when the most evolved incident is closed.

#### Features

None

#### Security

None

#### Changes

None

#### Notice

None

### Release date: September 15, 2016

#### Bug fixes

* This release resolves an issue with the missing data in Log Manager Summary graphs for the month of April. The issue has been resolved and summary graph data is now displayed correctly.
* This release fixes the bad character in the scan report host details header and PDF title, which now display correctly.

#### Features

None

#### Security

None

#### Changes

* With this release, Collection Alert rules are added into the mass edit functionality for protected host.
* With this release, one should be able to disassociate an ‘Assignment Policy’ associated with a protected host while editing.
* With this release, the labeling in the Networks and Appliances tooltips under the Add Monitoring Policy page was updated for a clear message and direction.

#### Notice

None

Release date: September 1, 2016

#### Bug fixes

* This release resolves an issue with the filter "Only show rows with the value" on the Incident Monitor page under the Threat column, where it was not changing after the selection was made. The issue has been resolved and filter now works as expected.
* This issue fixes the misspelled words in the Events-Full Report.
* This release resolves an issue with the alert details section, where it was not displaying content in event of large data. The issue has been resolved and UI now shows the information correctly.
* This release resolves an issue with Notification, where the message was getting truncated. That was fixed and the UI is now showing the information as expected.
* This release resolves an issue with the title appearing on the tab on the notification pages. It now appears correctly in the browser.
* This release resolves an issue in the Alert history page to display the correct information under the message section.

#### Features

None

#### Security

None

#### Changes

* With the release of Threat Manager with ActiveWatch in AWS marketplace, primary, secondary, and tertiary contact information fields are added on the signup page.

#### Notice

None

**Release date**

August 18, 2016

**Bug fixes**

* This release resolves an issue with the Log Manager summary graphs where data was missing due to the time zone conflict. The data now shows up on the graph.
* This release resolves an issue with the edit form to modify network functionality on the Threat Manager Networks section. The tags field is now displayed only when needed and multiple appliance validation now works as expected.
* This release resolves an issue with the Saved View PDF having the incorrect URL. The link on top of the PDF reports now work.
* This release fixes the trailing spaces in the filter section of the Log Manager message search.

**Changes**

* The agent version is added to the Log Manager/Threat Manager host section under the Host details.
* The UI now displays Threat Manager on the top menu instead of My Account when a user adds or edits their signature.
* The status bar is added in the UI when a dispute is submitted under the Scan Disputes section.

**Release date**

August 4, 2016

**Bug fixes**

* This release resolves an issue in the TM Network page to display correct results when filtering large amounts of data. 404 bad request error messages were appearing as a result of filtering large amounts of data. Filters now work as expected and display the correct data.
* This release resolves an issue with the Incident page in the UI. The results were not available when Zone filter was used twice. Incidents are now returned for a given time range if multiple Zone filters are used.
* This release resolves an issue with the Webhooks page in the UI. The server response was not working correctly. The server response now works as expected.

**Changes**

* The alert type field on the notification policies page has been modified to allow users to change its value in case the notification policy is created automatically.
* The UI will not allow users to modify the notification targets for a scan under the Scan report.
* Users can download a PDF of the ASV feedback form on the Reports > PCI Scan Result section.
* The PCI Vulnerability Details report was updated with additional information and better formatting.
* The hostname information is added to the PCI Executive Summary report (Sections 2, 3a, and 3b) as per the PCI format mandate.
* TheAlert LogicPCI Certificate ID is updated for PCI reports.
* The "PCI Executive Summary" and "PCI Vulnerability Details" reports were updated to only show port: [port number]/[protocol] whenever the port is different from 0.

### Release date:

July 21, 2016

**Bug fixes**

* This release resolves an issue with the **Schedule a Demo** link on the WAF page. The link in the user interface was not working previously. This issue has been resolved and the link now takes you to the right destination.
* This release corrects inconsistencies with the last modified date listed on the Scan Dispute page. The date now matches the date on the Scan Result Resolution page.
* This release resolves an issue with the Summary widget on the Log Manager Licensing page. The Duration option was not working in the widget. This issue has been corrected and duration can now be changed.
* This release resolves an issue with the description field in the Alert Details section of the Alert History page. The description was not displaying correctly. This was fixed to show the correct description text.
* This release resolves an issue with the Contacts &amp; Groups Page under Notifications. Users could not delete email contacts. This was fixed and email contacts can now be deleted.
* This release resolved an issue with the edit notification policy functionality in the Internet Explorer 11 browser (IE11). Notification policies were not getting edited in IE11. This was fixed and notification policies can now be edited in IE11.
* This release resolves an issue with inconsistent button styles. This was fixed and the Save/Cancel button design is now consistent.
* This release resolves an issue with the buttons on the Messages page in Log Manager. Icons disappeared when users hovered over them. This issue has been corrected and icons are now always visible.
* This release resolves an issue with the incident information in the Threat Security Report. The report now shows the correct number of incidents in created and in open reports.
* This release resolves an issue with the data in the incidents report. The incident count in the Internal vs External section of the report was not consistent with other sections. This issue was resolved and it now matches the other sections.

***
**Release date**

July 7, 2016

**Bug fixes**

* This release corrects inconsistencies in the user interface text for the **Retention Period** link under **Options** on the sidebar of the My Account page. The text is now consistent.
* This release resolves an issue in the Policies section of Threat Manager. The user interface did not allow users to edit the frequency of an update after it had been set to monthly or weekly. With this fix the user interface works as expected and users can choose daily, weekly, or monthly updates.
* This release resolves an issue with dispute resolution notifications on the PCI Scan Result page. When a dispute is closed by ASV, the user was previously not provided with a link to the dispute system to view the comments. This issue has been corrected and the link is now available.
* This release resolves an issue with dispute resolution notifications on the PCI Scan Result page. When a dispute is failed and closed by ASV, the PCI Scan Result page lists the date and time instead of only the date.
* This release resolves an issue with the Log Manager Top 10 Users widget. The widget was not showing user information correctly. This was fixed by allowing the widget to show the “@” character in usernames and now the information is displayed correctly.
* This release resolves an issue where the user interface was not showing the info icon inside the search boxes in the Log Manager. That was corrected.
* This release resolves an issue on the Overview - Zones page in the Management section. The table on the page was not showing the number of appliances. This was fixed and now the number of appliances is displayed correctly.
* This release resolves a display issue on the Monitor pages. The **Search Filters** button was not lined up with the other elements on the line. This was fixed.
* This release resolves an issue with the user interface appearance on the Summary page. The main menu was missing and other elements were misaligned for customers. These issues have been fixed.

Security

NA

Changes

* The form for creating/editing assignment policies in Threat Manager now includes a field for a list of secondary appliances. The Alert Logic back end allows a failover policy that it currently manages outside of the customer's control. The Secondary Appliances field lists secondary appliances managed by the customer.
* In the Public API for Azure sources, any text entered into the **Access Key** field for Azure Storage Accounts now displays as password type rather than readable text.

Notice

NA

***
**Release date**

June 23, 2016

**Bug fixes**

* This release resolves an issue on the Scan Report page where the UI was not showing the Cancel option. Development has resolved the issue and the Cancel option is now available.
* This release resolves an issue originating with the Time Zone field on the My Account page. The cache was removed from the My Account page to save any settings changes on the page.
* This release resolves an issue with the username and domain format when users set up credentials for a Quick Scan. Development has resolved the issue and user@domainname formatting is saved correctly.
* This release resolves an issue with the edit functionality of S3 policies and customized templates. Development has resolved the issue and S3 policy changes are now being saved with customized templates.
* This release resolves an issue with special characters in user email addresses. Users can now save time zone changes in the legacy user interface with special characters in the user email.

Security

NA

Changes

This release provides a new web CSS theme in the Security Content Center section. The theme now matches the rest of the user interface. This release also removes the Scan Plugin and NVD Vulnerabilities links from the Security Content Center.

Notice

NA

***
June 23, 2016

| Service/UI | Ticket # | Description |
|---|---|---|
| **Scan Report** | DE-5022 | This release resolves an issue on the Scan Report page where the UI was not showing the **Cancel** option. Development has resolved the issue and the **Cancel** option is now available. |
| **My Account** | DE-4808 | This release resolves an issue originating with the **Time Zone** field on the My Account page. The cache was removed from the My Account page to save any settings changes on the page. |
| **Quick Scan** | US-39115 | This release resolves an issue with the username and domain format when users set up credentials for a Quick Scan. Development has resolved the issue and user@domainname formatting is saved correctly. |
| **Log Manager** | DE-4782 | This release resolves an issue with the edit functionality of S3 policies and customized templates. Development has resolved the issue and S3 policy changes are now being saved with customized templates. |
| **Legacy User Interface** | DE-4525 | This release resolves an issue with special characters in user email addresses. Users can now save time zone changes in the legacy user interface with special characters in the user email. |
| **Security Content Center** | US-39280 | This release provides a new web CSS theme in the Security Content Center section. The theme now matches the rest of the user interface. This release also removes the**Scan Plugin** and **NVD Vulnerabilities** links from the Security Content Center. |

June 8, 2016

<table>
  <col />
  <col />
  <col />
  <thead>
    <tr>
      <th>Service/UI</th>
      <th>
        <p>Ticket #</p>
      </th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <b>Monitor Settings</b>
      </td>
      <td>REQ-1191928</td>
      <td>
        <p>This release resolves an issue with the Monitor Settings page (Threat Manager&amp;gt;Policies&amp;gt;Monitor Settings). The token validation was not working properly when the user was updating the page. Development has resolved this issue and the token validation now works as intended. </p>
      </td>
    </tr>
    <tr>
      <td>
        <b>Monitor Settings</b>
      </td>
      <td>REQ-1191928<br /></td>
      <td>
        <p>This release resolves an issue with the Monitor Settings page. When a user would submit the Monitor Settings form the drop-down menu at the top of the Alert Logic user interface would change from "Threat Manager" to "Select Product." Development has resolved this issue and the drop-down menu selection will remain as "Threat Manager" when a user submits the Monitor Settings form. </p>
      </td>
    </tr>
    <tr>
      <td>
        <b>PCI Scan Policy</b>
      </td>
      <td>REQ-1200422</td>
      <td>This release resolves an issues with the New PCI Scan page (Scans&amp;gt;Scans tab&amp;gt;Schedule PCI Scan). The system was not validating the <b>on this day (1-28)</b> field when a user would select the Quarterly option. A user could leave this field blank and the system would still save the schedule normally. Development has resolved this issue and the system now validates this field to make sure the user has entered a proper day into the field. </td>
    </tr>
    <tr>
      <td>
        <b>Incidents</b>
      </td>
      <td>US-38216</td>
      <td>
        <p>This release adds an enhancement to the Incidents Detail page (Incidents&amp;gt;Search for incident&amp;gt;click incident ID). With this release user will be able to rate incidents on a 5-star scale. They will also be able to provide a more indepth opinion on the incident by answering survey questions and finally, they will be able to leave comments on the incident. The following provides the details for the new enhancement:</p>
        <ol>
          <li>A new <b>Rate this Incident</b> button has been added to the Incident Details page. You can click this button	to open a pop-up where you will rate the incident using a 5-star scale. You can then click <b>Next</b> to answer three survey questions.</li>
          <li>The survey questions are as follows:</li>
          <ol>
            <li>Is this incident accurate?</li>
            <li>Is it clear what action to take?</li>
            <li>Were you notifies as expected?</li>
          </ol>
          <li>You then have the option of adding a comment to your evaluation of the incident.</li>
        </ol>
      </td>
    </tr>
  </tbody>
</table>
May 25, 2016

| Service/UI | Ticket # | Description |
|---|---|---|
| Log Manager | REQ-1151449 | This release adds a new flat file scheme support for the File Name Rotation Scheme field in the Create a New Flat File Policy form on the Flat File policies page. The following is the new flat file scheme supported: YYYYMMDD_hh. |
| **Contacts** | REQ-1184592 | This release resolves an issue with the All Contacts search (Alert Logic UI>Management>Contacts &amp; Groups). The search would work on your first query but fail on subsequent queries. Development has resolved this issue and the search now works as intended. |
| **Notification Policy** | REQ-1190917 | This release resolves an issue with the Notification Policies page. The Delete option was not available for automatically generated policies. Development has resolved this issue and the Delete option is now available for automatically generated policies. |
| Log Manager | REQ-1171415 | This release resolves an issue with the Dashboard tab on the Log Manager Summary page. The **Top 10 Log Messages Types** widget was not showing the correct information. Development has resolved this issue and the widget now displays the correct information. |
| **Reports** | REQ-1195906 | This release resolves an issue with the PCI Scan compliance report. The report was showing the wrong status for the scan results. Development has resolved this issue and the report now shows the correct status. |

May 11, 2016

| Service/UI | Ticket # | Description |
|---|---|---|
| **Vulnerability Report** | REQ-1190917 | This release resolves an issue with the top 10-vulnerability report. The Impacted Hosts list was not showing all impacted hosts. Development has resolved this issue and the Impacted Hosts list now shows the full list of impacted hosts. |
| **Log Manager** | REQ-1194339 | This release adds two new AWS regions to the Log Manager Sources creation form, as well as the editing form. The new regions are: (1) EU (Frankfurt) and (2) Asia Pacific (Seoul) |
| **Scans** | DE-4658 | This release resolves an issue with the Scans list (Alert Logic UI>Scans>Scans tab). When a customer would delete a zone or host group, the scan policy would be removed from the Scans list. Development has resolved this issue and the Scans list will show the scan policy even if the zone or host group is deleted. |

April 27, 2016

| Service/UI | Ticket # | Description |
|---|---|---|
| User Interface | DE-4624 | This release resolves an issue in which the Alert Logic console   displayed customer names upside down on the side menu. |
| User Interface | DE-4727 | This release resolves an issue with the Alert Logic console password reset function. With this release, the password reset feature functions as expected. |

April 12, 2016

| Service/UI | Ticket # | Description |
|---|---|---|
| **Host Details** | REQ-1184041 | This release resolves an issue in which customers experienced long time lags when changing the status of vulnerabilities. After the service pack, changes in vulnerability status appear when the page reloads. |
| **Log Manager** | REQ-1177479 | This release improves the Log Manager Collection Sources page by including Log Source IP information. |
| **Threat Manager** | DE-4576 | This release resolves an issue in which an incorrect error message appeared if the customer entered an invalid CIDR notation while creating or editing a whitelist policy. |
| **Support Pages** | US-35087 | This release corrects outdated documentation links appeared on the Support pages for Threat Manager and Log Manager. |
| **PCI Reports** | US-35060 | This release improves the PCI Vulnerability Details Report by grouping and sorting detected open ports and services. |

March 29, 2016

| Service/UI | Ticket # | Description |
|---|---|---|
| **Reports** | REQ-1185852 | This release resolves an issue with the HIPAA—Full and GLBA—reports where the closed incidents were shown as "Needs Review." With this release, the text is changed to "Incidents Addressed" when showing closed incidents. |
| **My Account** | REQ-1181880 | This release changes the "Product Entitlement" text to "Retention Period." This release also updates messages from "Information not available" to "This account does not include log storage." |
| **Log Manager** | US-34270 | This release resolves an issue with the sources add/edit functionality. With this release, the "Save" button is changed to "Preview" for the Azure blob and Azure table source types that require a two-step configuration. |
| **Scan Result Resolution** | DE-4388 | This release resolves an issue with incorrect data being displayed when the ASV engineer selects the "Collapse Completed Items" option. |

***
March 15, 2016

| Service/UI | Ticket # | Description |
|---|---|---|
| **Log Manager and Threat Manager** | DE-4520 | This release resolves an issue with the total bytes in the Log Manager and Threat Manager licensing widgets. With this release, the total bytes conversion is displayed correctly. |
| **Scan Result Resolution** | DE-4348 | This release resolves an issue with the asset check box. With this release, check marks are now visible in the check box when all assets are selected on the "Scan Dispute" page. |
| **Scan Result Resolution** | DE-4149 | This release resolves an issue with the asset check box. With this release, the "uncheck all" functionality correctly removes all check marks on the "Scan Result Resolution" page. |
| **Scan Result Resolution** | DE-4427 | This release resolves an issue with attaching files. With this release, users can attach files when "single vulnerability" is selected on the "Begin Dispute" page. |

***
March 1, 2016

| Service/UI | Ticket # | Description |
|---|---|---|
| **Reports** | DE-4381 | This release resolves an issue where the **Log Collection Health** report was including extra data. In addition to correctly reporting log sources, the report was also including Threat Manager protected hosts. The report now provides an accurate list of log sources only. |
| **Reports** | DE-4175 | This release resolves an issue with the **Incidents Full** report where the **Internal vs. External Incidents** section was not being populated when data was available. When pertinent data is available, the report now shows this data correctly. |
| **Reports** | DE-4150 | This release updates the **Reports Scheduling Options** to require the specification of a **Notifications** target if the customer has been migrated to the new **Notifications** system. Previously, scheduled reports would fail if a **Notifications** target was not specified. |
| **Threat Manager** | DE-4255 | This release resolves an issue where the **Configuration Status** information on the **Threat Manager Detection Networks** page was incorrect. The correct information is now provided. |
| **Scan Result Resolution** | DE-4440 | This release resolves an issue with the **Scan Result Resolution** page. Previously, when the user clicked **Close**, a duplicate dispute record was created. Now, the dispute closes successfully without creating a duplicate dispute. |

***
February 16, 2016

| Service/UI | Ticket # | Description |
|---|---|---|
| **Reports** | DE-4381 | This release resolves an issue where the **Log Collection Health** report was including extra data. In addition to correctly reporting log sources, the report was also including Threat Manager protected hosts. The report now provides an accurate list of log sources only. |
| **Reports** | DE-4175 | This release resolves an issue with the **Incidents Full** report where the **Internal vs. External Incidents** section was not being populated when data was available. When pertinent data is available, the report now shows this data correctly. |
| **Reports** | DE-4150 | This release updates the **Reports Scheduling Options** to require the specification of a **Notifications** target if the customer has been migrated to the new **Notifications** system. Previously, scheduled reports would fail if a **Notifications** target was not specified. |
| **Threat Manager** | DE-4255 | This release resolves an issue where the **Configuration Status** information on the **Threat Manager Detection Networks** page was incorrect. The correct information is now provided. |
| **Scan Result Resolution** | DE-4440 | This release resolves an issue with the **Scan Result Resolution** page. Previously, when the user clicked **Close**, a duplicate dispute record was created. Now, the dispute closes successfully without creating a duplicate dispute. |

***
February 4, 2016

| Service/UI | Ticket # | Description |
|---|---|---|
| **Summary** | INC-1145286 | This release updates the **Threats** widget on the **Summary** page. The **Critical incidents** label has been changed to **Open incidents** to more accurately represent the provided count. |
| **Threat Manager** | INC-1145693 | This release updates the exported files (PDF and Excel) for the **Top 10 Vulnerabilities** report. The exported versions of the report now include **Impacted Hosts** information, which had previously been omitted. |
| **Vulnerability Reports** | INC-1139584 | This release updates the **Hosts by Vulnerabilities** report and the **Detailed Hosts by Vulnerabilities** report, which have been modified to match data in related reports and host details pages. |

***
January 19, 2016

| Service/UI | Ticket # | Description |
|---|---|---|
| Reports | INC-1145467 | This release resolves an issue where the **No Logs **report was not showing the accurate number of log sources that were not collecting. |
| Threat Manager | INC-1077303 | This release updates wording on **Networks** page under the **Detection** section for **Threat Manager**. When adding a protected network, the Appliance section now has more proactive messaging with a link to the Monitoring page where you can add a Monitoring Policy to your network. The tool tip also advises the customer that any new Appliance added to the network will fall under the new network's monitoring policy. |
| Incident Page | INC-1156995 | This release updates wording on the **Collection** page under the **Alert Rules** section for **Log Manager**. If a customer entered a number below 15 in the **Time without logs** field they would receive an **Internal Server Error**. The error message now reads, "Alert threshold is less than allowed minimum." The tool tip has also been updated. |
| Vulnerability Reports | INC-1139584 | This release updates the column heading for the **Devices** page under the **Configure** section for **Scans**. The Urgent column heading now reads "Urgent+Critical." This now matches the information shown in the vulnerabilities report. |
| Vulnerability Reports | INC-1139584 | This release resolves an issue with the **Detailed Vulnerabilities by Host** report. The query grouping was removed to match Scans results. |
| Threat Event Report | INC-1147891 | This release resolves an issue with the **Event Export by Malware and SQL Injection Attempts** report where the **Signature Name** column was not showing any information. |
| Dashboard Widget | INC-1145328 | This release updates the **Incidents by Threat Level** widget on the **Dashboard** page to use the new NGX threat level ranges. This matches the results from the Incidents page. |

***
January 6, 2016

| Service/UI | Ticket # | Description |
|---|---|---|
| My Account Page | US28213 | This release adds the "Log Retention Period" to the My Account page. |
| Log Manager | INC-1145361 | This release resolves an issue with Long Search Saved Views. When the customer created a Saved View for a long search, no target field was provided so notifications were not sent out. This release adds a "Send notification to" field when creating Saved Views off of Long Search warnings. |
| Incident Page | INC-1162217 | This release resolves an issue with the Incident page, where customers could not view their incidents because of a permissions error. With this release, customers can view the incidents without permissions errors. |
