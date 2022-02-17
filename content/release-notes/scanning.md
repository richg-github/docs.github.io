# Scanning Release Notes

## Scanning release notes

    2021    ### Release date: November 17, 2021

#### Features

Alert Logic released agent-based vulnerability scanning.  Agent-based scanning enables users to leverage the vulnerability assessment coverage of authenticated network scanning without the need to manage credentials and with a reduction in network traffic and impact. To learn more, including how to enable this feature by deployment, see [Agent-Based Scanning](../analyze/manage-scans-and-results/agent-based-scan.md).

### Release date: April 6, 2021

#### Features

Alert Logic added an enhancement to your scope of protection capability for Data Center deployments. You can now define your protection  at a subnet level. To learn how to change your scope of protection, see [Change Protection Level of an Asset](../deploy/change-protection.md).

### Release date: March 25, 2021

#### Features

Alert Logic released three new vulnerability reports in the Vulnerabilities tab of the Reports page in the Alert Logic console. The Scan Summary Breakdown reports provide summary, detailed, and variance vulnerability results for  specific scan schedules. These reports can be downloaded  as an image, data (CSV), crosstab, PDF, or PowerPoint file. For more information about each report, see:

* [Scan Host Summary](../analyze/reports/Vulnerabilities/scan-schedule-breakdown/scan-host-summary.md)
* [Scan Details List](../analyze/reports/Vulnerabilities/scan-schedule-breakdown/scan-details-list.md)
* [Scan Variance](../analyze/reports/Vulnerabilities/scan-schedule-breakdown/scan-variance.md)

### Release date: January 28, 2021

#### Features

Alert Logic released the following enhancements to scan schedules for the Managed Detection and Response platform:

* For internal and external vulnerability scans, you can now specify the ports to scan. You can choose ports in predefined groups or define a custom list of ports to scan.
* You can also specify ports  to exclude from internal and external vulnerability scans.

To learn more, see [Manage Scan Schedules](../analyze/manage-scans-and-results/schedules.md).

    2020    ### Release date: September 15, 2020

#### Features

Alert Logic released the following enhancements to  scan scheduling:

* A quarterly scan option is now available for internal and external vulnerability scans.
* For monthly scans, you can now choose to scan during a certain week on a certain day.

Alert Logic is also releasing the Last Scanned Breakdown report in the Vulnerabilities tab of the Reports page. The report provides visibility into when your assets were last scanned for vulnerabilities. To learn more, see [Last Scanned Breakdown](../analyze/reports/Vulnerabilities/last-scanned-breakdown.md).

### Release date: August 8, 2020

#### Features

Alert Logic released enhancements to scan scheduling. Default scan schedules are available  that you can edit, or you can create additional schedules for all or selected assets in your deployment. The improved Scan Schedules page is available from your deployments. To learn more, see [Manage Scan Schedules](../analyze/manage-scans-and-results/schedules.md).

You can now also optimize scan performance from the Topology page in the Alert Logic console. To learn more, see [Adjust scan performance](../analyze/manage-scans-and-results/adjust-settings.md#Adjustscanperformance).

    2019    ### Release date: September 17, 2019 

Alert Logic added a new feature to the scanning functionality, Scan Now. If you need to run a scan immediately, you can use the Scan Now feature on the Topology page. This scans the selected asset right away or as soon as possible, outside of the normal schedule. See [Manage Scans and Scan Results](../analyze/manage-scans-and-scan-results.md#Expedite) for more information.

    2018    ### Release date: March 6, 2018

#### Bug fixes

* This release adds a function that improves the results of aborted or canceled scans. The scanner attempts to get all possible information from aborted and canceled scans.
* This release resolves an issue with scans that have identical hostname and IP address. The scan continues and no longer triggers an error.

#### Features

None

#### Security

None

#### Changes

None

#### Notice

None

### Release date: February 20, 2018

#### Bug fixes:

* This release resolves an issue with one of the scanning components timing out. All scans now run uninterrupted.
* This release resolves an issue with a scanning component restarting and interfering with an existing scan job. This issue is fixed.

#### Features

None

#### Security

None

#### Changes

None

#### Notice

None

### Release date: February 2, 2018

#### Bug fixes:

None

#### Features

* Added client-side logic for out-of-memory prevention.

#### Security

None

#### Changes

None

#### Notice

None

    2017    ### Release date: September 21, 2017

#### Bug fixes:

* This release resolves an issue with Windows patch scanning that would cause specific Windows configurations to not report patches correctly.
* This release resolves an issue with OVAL checks that caused a small number of checks to not be evaluated.
* This release resolves an issue with the Windows users check. The system now checks all users.
* This release adjusts some web-based checks to not look in clearly non-vulnerable paths.

#### Features

None

#### Security

None

#### Changes

None

#### Notice

None

### Release date: September 7, 2017

#### Bug fixes:

* This release improves logic around the reporting of exposure ID 91882 to lower the rate of false positives.
* This release merges some Struts checks and adjusts parameters on certain web-based tools to reduce overall scan time.
* This release resolves issues with PCI Web Application scans that caused some scans to take an excessively long time to complete.
* This release disables exposure ID 81979 (Missing HttpOnly Flag From Cookie) from PCI Web Application scans due to a high false positive rate.

#### Features

* This release improves the accuracy of the HSTS check for all scans.
* This release adds the Struts CVE-2017-9805 exploit check.

#### Security

None

#### Changes

None

#### Notice

None

### Release date: August 24, 2017

#### Bug fixes:

* This release resolves an issue with Windows credentialed scans over SMB2 and NTLanMan v2 protocols.
* This release reconfigured PCI web application scans to reduce the number of incomplete scans.

#### Features

None

#### Security

None

#### Changes

None

#### Notice

None

### Release date: August 10, 2017

#### Bug fixes

None

#### Features

* This release optimizes the way Alert Logic handles a very large number of open ports in NMAP.
* This release updates the Netbios user check to further reduce false positives.

#### Security

None

#### Changes

None

#### Notice

None

### Release date: July 18, 2017

#### Bug fixes

* This release resolves an issue where PCI Compliance reports could be downloaded for reports that failed to run. This was corrected and report links are no longer available for reports that failed to run.
* This release adds warning text in the comment section when users attach files to a dispute. The text informs the user that a comment is required before pressing the ‘add comment’ button.
* This release resolves an issue where Threat Manager appliance scan enable status did not work correctly in the new Alert Logic console. This has been corrected and the scanning status of the appliance now works as expected.
* This release resolves an issue where users could select an invalid appliance for Cloud Defender fast scans. This has been corrected and users may no longer select invalid appliances.

#### Features

None

#### Security

None

#### Changes

None

#### Notice

None

### Release date: July 12, 2017

#### Bug fixes

None

#### Features

* This release adds a new check for CVE-2017-9791, the Apache struts 1 plugin.

#### Security

None

#### Changes

None

#### Notice

None

### Release date: July 11, 2017

#### Bug fixes

* This release resolves an issue with MSSQL false positives and SSH default credential false positives.
* This release resolves an issue with Sweet32 vulnerability false positives.

#### Features

* This release adds several remote Intel AMT checks.
* This release adds speed and functional improvements to Linux patch scanning.

#### Security

None

#### Changes

None

#### Notice

None

### Release date: July 6, 2017

#### Bug fixes

* This release resolves an issue that allowed customers to dispute expired scans. This feature is no longer available to customers.

#### Features

None

#### Security

None

#### Changes

None

#### Notice

None

### Release date: June 28, 2017

#### Bug fixes

* This release resolves an issue with false positives in NGINX.
* This release resolves an issue with Tomcat false positives.
* This release resolves an issue where some web applications were not being correctly scanned in PCI scans.

#### Features

* This release further reduces the network impact of customers using lower intensity PCI scans.

#### Security

None

#### Changes

None

#### Notice

None

### Release date: June 20, 2017 

#### Bug fixes

* This release resolves an issue with a false negative in the SSL Hostname Discrepancy check.

#### Features

None

#### Security

None

#### Changes

None

#### Notice

None

### Release date: June 15, 2017

#### Bug fixes

* This release resolves an issue where the incorrect version of MS-SQL was detected.

#### Features

* This release adds more authenticated checks for Windows Server 2016.

#### Security

None

#### Changes

None

#### Notice

None

### Release date: June 6, 2017

#### Bug fixes

* This release improves alternative name handling with X.509 certificates (aka SSL/TLS checks).
* This release improves reporting of default pages on different ports.
* This release assigns a new exposure ID for the "Default Webpage" vulnerability.
* This release improves the accuracy of the EternalBlue check to eliminate false negatives.

#### Features

* This release adds more patch scan checks for Linux OS.

#### Security

None

#### Changes

None

#### Notice

None

### Release date: May 18, 2017

#### Bug fixes

None

#### Features

* This release adds an unauthenticated check for the "WannaCry" vulnerability MS-17-010 CVE-2017-0143 to CVE-2017-0148, also called "EternalBlue".

#### Security

None

#### Changes

None

#### Notice

None

### Release date: May 11, 2017

#### Bug fixes

* Clicking the support icon now correctly inserts the email recipient in Microsoft Outlook.
* This release shows the correct ASVE name for the reviewing analyst in the Attestation of Compliance section of the Vulnerability Details Report.
* This release displays the correct analyst name for former employees in the Dispute System.
* When invalid hosts are detected during PCI Scan submit, all invalid hosts are shown in the error  message, instead of just the first invalid host.
* This release updates the contact person (name and title) on the PCI Attestation of Compliance.
* This release correctly displays HTML tags in dispute comments.

#### Features

None

#### Security

None

#### Changes

None

#### Notice

None

### Release date: May 4, 2017

#### Bug fixes

None

#### Features

* This release adds a check for the SSL/TLS Cert CN name mismatch against Alternate names.
* This release adds Drupal 8 detection.
* This release improves Microsoft patch scanning.
* This release improves Debian/Ubuntu patch scanning.
* This release adds additional preflight checks to PCI Web Application Scans.

#### Security

None

#### Changes

None

#### Notice

None

### Release date: April 25, 2017

#### Bug fixes

* This release resolves an issue with  NMAP 7.0+ OS detection.
* This release standardizes PCI Web Application Scans vulnerability details.

#### Features

* This release increases detection accuracy for the MS04-011 vulnerability and default IIS webpages.
* This release adds major improvements to the snmpscan tool time.
* This release increases the threshold for scan errors canceling PCI Web Application Scans.

#### Security

None

#### Changes

* This release removes WoSign and Startcom as trusted X.509 roots.

#### Notice

None

### Release date: April 4, 2017

#### Bug fixes

None

#### Features

* This release adds detection for CVE-2017-7269.
* This release improves scan interference detection on web pages that are responding "you are blocked" or similar.
* This release adds detection of Cisco IPSEC/IKEv2 VPN weak ciphers and weak encryption.

#### Security

None

#### Changes

None

#### Notice

None

### Release date: March 30, 2017

#### Bug fixes

* This release resolves an issue with PCI vulnerability comments. Line breaks for long comments have been restored, making the comments easier to read.

#### Features

* This release adds a notification feature to warn customers about inactivity on open PCI disputes. Customers receive a notification after three days of inactivity, and the notification contains a link to the dispute case and a warning that the dispute will automatically close after another seven days. Another notification is sent after the dispute automatically closes, and it contains a link to the PCI scan report summary.
* This release adds a support icon next to each scan listing. Click the support icon ![](../Resources/Images/Cloud Defender/Scanning/al-support.png) to send an email to support staff. The email template is automatically populated with the relevant scan information, so you just need to enter information about the issue you are having, and the support team will respond to your concerns.
* This release adds more informative error messages in the scan dispute system.

#### Security

None

#### Changes

None

#### Notice

None

### Release date: March 27, 2017

#### Bug fixes

* This release corrects a false positive in Apache Struts2 for cases where non-vulnerable servers responded with the entire original request. (CVE 2017- 5638)

#### Features

None

#### Security

None

#### Changes

None

#### Notice

None

### Release date: March 22, 2017

#### Bug fixes

* This release resolves an issue with false positives for MariaDB being mistaken for MySQL.
* This release resolves additional items related to ECC signature strength detection.

#### Features

* This release adds a new check for unencrypted AMIs in AWS EC2.
* This release improves detection for Struts 2 CVE-2017-5638, and adds URL and port to the evidence field.
* This release adds IPSEC IKEv1 VPN encryption strength detection.
* Telnet is now flagged as a failing vulnerability on all PCI scans.

#### Security

None

#### Changes

None

#### Notice

None

### Release date: March 16, 2017

#### Bug fixes

* This release resolves an issue with the scan dispute status indicator in Internet Explorer.
* This release resolves an issue where the scan dispute details showed an incorrect dispute count. The issue has been corrected and the page now shows the number of disputes that have been resolved.

#### Features

* This release improves performance on the PCI Compliance tab.
* This release improves detection of existing issues with customer systems that may interfere with system discovery and assessment.

#### Security

None

#### Changes

None

#### Notice

None

### Release date: March 10, 2017

#### Bug fixes

None

#### Features

* This release adds detection for “CVE-2017-5638 - Apache - Struts2 Jakata - Multipart Parser Code Execution issue,” which is being actively exploited in the wild.

#### Security

None

#### Changes

None

#### Notice

None

### Release date: March 7, 2017

#### Bug fixes

* This release resolves an issue with ECC signed SSL/TLS certificate analysis.
* This release resolves an issue with the HSTS vulnerability. The vulnerability is no longer triggered on IP addresses associated with proper FQDNs.

#### Features

* This release updates PCI reports to report all vulnerabilities duplicated on multiple ports in the same web application. For example, if the same vulnerability was found in a web application on port 80 and 443, it would now appear twice in the report.
* This release updates UDP port scanning to allow large custom port ranges without timing out.
* This release adds several checks for weak RDP encryption levels.
* This release adds to the list of services that are scanned for HTTP vulnerabilities and web application scanning.

#### Security

None

#### Changes

This release updates Nmap services to version 7.

None

#### Notice

None

### Release date: March 2, 2017

#### Bug fixes

* This release resolves an issue with the contact information form you use to start a dispute. The form now requires an email address.
* This release resolves an issue with the PCI scan dispute details. The dispute details now correctly list the name of the reviewing engineer.
* This release improves the appearance of the scan dispute description page.
* This release sorts the port lists in the PCI Vulnerability report by IP address.
* This release resolves an issue with PCI scan setup. Users can no longer submit scans with invalid host names.

#### Features

* This release adds more informative status messages in the scan dispute system.
* This release adds customer selection functionality to the PCI Compliance tab on the Scans page. This feature is for customers with multiple accounts only.

#### Security

None

#### Changes

None

#### Notice

None

### Release date: February 14, 2016

#### Bug fixes

None

#### Features

* This release adds functionality in the** New PCI Scan** page, allowing users to seed the scanner with hidden URL entries. The** All FQDNs** box is now titled **All Targets**, and it takes a wide range of inputs, including hidden URLs. Hidden URLs are URLs that cannot be reached from the homepage of the website. PCI reports have been expanded to show which hidden URLs were seeded in to the system. The seeded hidden URLs allow the scanner to reach more of your application, ensuring the most thorough possible scan.

#### Security

None

#### Changes

None

#### Notice

None

### Release date: February 9, 2017

#### Bug fixes

None

#### Features

* This release adds a new check for Sweet32 CVE-2016-2183, specifically on IIS with CBC and 3DES.
* This release adds a new check for HTTP Basic Authentication on HTTPS.
* This release improves vulnerability detection in Apache, Drupal, WordPress, JIRA, and VMware ESX.
* This release improves Microsoft detection, which could include more false positives that have to be disputed.

#### Security

None

#### Changes

None

#### Notice

None

### Release date: February 2, 2017

#### Bug fixes

None

#### Features

* This release adds three new vulnerability checks to the scanner.

#### Security

None

#### Changes

None

#### Notice

None

### Release date: January 31, 2017

#### Bug fixes

None

#### Features

* This release adds a check for VPCs without resources.
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

### Release date: April 25, 2017

#### Bug fixes

* This release resolves an issue in which customers were able to view, but not use, user interface controls meant only for PCI ASV analysts. With this release, only PCI ASV analysts can view engineer-specific menu items.
* This release adds vulnerability checks for open access to Elastisearch, Hadoop and CouchDB.
* This release updates the interface for setting up email contacts to receive notification when scans complete. This feature allows partners to specify both partner recipients and end user recipients.
* This release adds a permanent link to the dispute system from the PCI Compliance page.
* This release adds workflow buttons in the dispute system to guide users and streamline the dispute submission process.
* This release adds a tooltip to indicate when a scan is associated with a deleted zone or host group.
* This release updates tooltips and descriptions on the scan creation page and PCI scan creation page.
* This release adds the scan scope to the PCI executive report.
* This release changes the default port listing during scan creation. The list of "Common TCP &amp; UDP Ports" is now the default option, and it is pre-selected for the scan.

#### Security

None

#### Changes

None

#### Notice

None

### Release date: January 26, 2017

#### Bug fixes

* This release resolves an issue with	SSL/TLS checks, eliminating false positives in key length.
* This release resolves an issue with VMware version checks inflating scan duration.

#### Features

* This release adds a check for RDS retention policy length greater than seven days.
* This release adds timeout values to PCI web application scans to reduce scan durations.
* This release adds support for ECC certificates.
* This release adds the Tools component for seed URL support in PCI scans. More components will be released at a later date.
* This release improves scan efficiency through a rearrangement of vulnerability and service checks and improvements in core networking code.

#### Security

None

#### Changes

None

#### Notice

None

### Release date: January 24, 2017

#### Bug fixes

None

#### Features

* This release adds a check for AMI objects that are not configured as private.
* This release adds a check for default NACL usage.

#### Security

None

#### Changes

None

#### Notice

None

### Release date: January 19, 2017

#### Bug fixes

* This release resolves an issue with PCI disputes. The system was overwriting customer statements when new ones were entered. This issue has been corrected and the system now works as expected.
* This release resolves an issue with PCI dispute attachments. The system now returns an error when the attachment is too large (larger than 1.5 MB).
* This release resolves an issue with Vulnerability Details and Executive Summary .csv and PDF reports. The CVE numbers are now displayed consistently across all reports.
* This release resolves an issue with fast scan credentials. The system no longer allows users to enter a user name or password consisting of spaces only.

#### Features

* This release expands the functionality of the PCI dispute prefill feature. Users can expand and edit all existing notes, and all related attachments are automatically displayed.
* This release improves the functionality of the SSL/TLS check for weak hashing.
* This release adds a check for HTTP strict transport security.
* This release adds a check for Badlock (CVE-2016-0128).

#### Security

None

#### Changes

None

#### Notice

None

### Release date: January 12, 2017

#### Bug fixes

* This release resolves an issue with logging in raw socket handling.

#### Features

* This release improves the functionality of the Apache XSS check involving HTTP 3xx codes.
* This release improves the functionality of the SSL/TLS check for weak hashing.
* This release adds a check for HTTP strict transport security.
* This release adds a check for Badlock (CVE-2016-0128).

#### Security

None

#### Changes

None

#### Notice

None

### Release date: January 5, 2017

#### Bug fixes

* This release resolves an issue where customers could set credentials for external scans, which did not use credentials. The credential form is now removed for those scans.
* This release resolves an issue with the scan creation page. The page now loads the complete set of menu options for all users.
* This release resolves an issue with scheduled scans. The upcoming scans were not showing 2017 dates, but the issue is fixed now.
* This release resolves an issue with an extraneous tooltip on external scans. The tooltip has been removed.

#### Features

* This release adds a feature that sends users an automated email if a scan fails. Users can set up the list of email addresses during scan creation. This feature will be made available to users in phases over the next five weeks.
* This release adds nine new AWS checks to Cloud Insight.
* This release splits an existing Cloud Insight AWS check into two, to address ELB insecure protocols and ciphers separately.

#### Security

None

#### Changes

None

#### Notice

None

    2016    ### Release date: December 14, 2016

#### Bug fixes

* This release improves coverage in existing scripts that detect and identify Horde web applications and IMP webmail.
* This release improves DNS detection by adding several pieces of DNS software and services, and secondary methods to retrieve the information.
* This release improves NMAP service detection and fingerprinting, improving the accuracy of what software and services are detected.
* This release improves detection of point of sale applications.
* This release improves detection of SQL servers with additional methods of detection, and updates version mappings for SQL Server 2008, 2012, 2014, and 2016. Expect out-of-date database versions to be flagged with vulnerabilities.

#### Features

* This release adds new checks and coverage for VMWare ESX and ESXi.
* This release adds detection for Netscreen default credentials.
* This release adds several new web application vulnerabilities and detection methods for PCI scanning.

#### Security

None

#### Changes

None

#### Notice

None

### Release date: December 8, 2016

#### Bug fixes

None

#### Features

* This release adds two new vulnerability checks to the scanner for environments with elastic load balancers.

#### Security

None

#### Changes

None

#### Notice

None

### Release date: December 7, 2016

#### Bug fixes

* This release resolves an issue with Scans. When a customer scheduled a scan using a host group, if the host group was not the latest host group created it would show the Warning icon and a message  that all the scanners assigned to the policy were unavailable. The search for the host groups was only finding the last host group id. Development has fixed this issue and the search now finds all host group ids instead of just the last one.
* This release resolves an issue where previously resolved PCI scan dispute items were losing their resolved status.
* This release resolves an issue with the Scans detail page. Customers were not able to modify the notification targets.

#### Features

* This release adds a new vulnerability check to the scanner for environments with elastic load balancers.

#### Security

None

#### Changes

None

#### Notice

None

### Release date: December 5, 2016

#### Bug fixes

None

#### Features

* This release adds two new TLS-related vulnerability checks to the scanner. Both of these new vulnerabilities are specific to cypher policies on elastic load balancers.

#### Security

None

#### Changes

None

#### Notice

None

### Release date: December 1, 2016

#### Bug fixes

* This release fixes an issue with vulnerability description text. The text has been updated and corrected.

#### Features

* This release adds two new vulnerability checks to the scanner.

#### Security

None

#### Changes

None

#### Notice

None

### Release date: November 10, 2016

#### Bug fixes

* This release resolves an issue with the Weblogic default credentials check.

#### Features

None

#### Security

None

#### Changes

None

#### Notice

None

### Release date: November 1, 2016

#### Bug fixes

* This release resolves an issue with MS SQL version reporting to increase detection accuracy.
* This release resolves an issue with false negatives in patch key identification for CentOS, RedHat Linux, andAmazon Web Services (AWS)Linux.
* This release resolves an issue with non-white space characters during OVAL checks using SSH. The system can now handle these characters, improving detection.
* This release changed the behavior of the 500 error and added additional HTTP header information for debugging. This results in higher fidelity in internal error messages among backend components and faster debugging and resolution.
* This release adds new parameters to ignore host keys between backend components. This allows for the use of load balancers and improves scalability and stability.

#### Features

* This release adds support for CentOS 6/7 and Amazon Linux AMI SecPod content via OVAL authenticated scanning.
* This release includes several changes to improve impact on content distributing controllers and better monitoring of scanner update progress.
* This release merges several branches of improvements to Acunetix 10.5 control and parse tool.

#### Security

None

#### Changes

* This release changes the update-tools.sh cron job to start at 12:01 instead of 12:00, to avoid race conditions and improve stability.

#### Notice

None

### Release date: October 27, 2016

#### Bug fixes

* This release resolves an issue where users did not receive an email notification upon submitting a dispute. This has been fixed and email notifications now go out immediately.

#### Features

* This release adds a feature that prevents users from scheduling scan policies using scanners that are inactive, disabled, or offline.
* This release adds a feature to warn users when a previously created policy is set up to use an inactive scanner. The policy with the warning is marked with a red exclamation point icon.
* This release changes the configuration of the **Schedule Options** menu. The **Scan End Time** and **Enable rollover scanning** options are now contained in a dropdown titled **Advanced Settings**.

#### Security

None

#### Changes

None

#### Notice

None

### Release date: September 30, 2016

#### Bug fixes

None

#### Features

* This release updates the Acunetix web scanner to version 10.5, improving PCI scanning capabilities.

#### Security

None

#### Changes

None

#### Notice

None

### Release date: September 29, 2016

#### Bug fixes

* This release resolves an issue with an error message that appears when customers schedule scans that are either too long for the time window or that contain too many hosts. The new error message is clearer about the customer's options to fix the error.
* This release resolves an issue with rejected disputes in Executive Summary Reports. The report previously showed the initial customer comments only. This has been fixed and it now shows the complete discussion between the customer and Alert Logic.
* This release resolves an issue with the engineer name listed at the bottom of the report. The reports now list the individual engineer who reviewed the dispute(s).
* This release resolves an issue with the dispute process. When a customer submits a dispute regarding an item that has been disputed in the past, the system now attaches the past dispute evidence to the new dispute.
* This release resolves an issue with user passwords that contain certain special characters such as double quotes. The issue is fixed and passwords now save correctly.

#### Features

None

#### Security

None

#### Changes

None

#### Notice

None

### Release date: September 27, 2016

#### Bug fixes

None

#### Features

* This release adds three new Scan Interference Detected Exposures. These exposures replace the single previous exposure, providing more precise information about the type of scan interference that the system detected.

#### Security

None

#### Changes

None

#### Notice

None

### Release date: September 21, 2016

#### Bug fixes

None

#### Features

* This release updates the Windows OVAL definitions to increase coverage for recent vulnerabilities discovered in authenticated Windows scans.

#### Security

None

#### Changes

None

#### Notice

None

### Release date: September 15, 2016

#### Bug fixes

* This release resolves an issue with the Scan Dispute List. The list did not show complete explanatory text for remaining disputes. For scans that are in analysis, the page now displays the text “xx remaining disputes.”
* This release resolves an issue with specifying recipients for scan results. Users can now click the check box to list email recipients.
* This release resolves an issue with the Acunetix web scanner reporting false positives for CVE-2009-3555.
* This release resolves an issue with the Nmap network mapping tool updated on August 31, 2016. The tool now correctly flags HTTP service for IIS 8.5 instead of UPnP for XBox One.

#### Features

None

#### Security

None

#### Changes

None

#### Notice

None

### Release date: September 1, 2016

#### Bug fixes

* This release resolves an issue in the PCI dispute email notification. Emails with updates on PCI dispute cases now include the customer contact name.
* This release resolves an issue with the dialog box for PCI dispute comments. The Bulk Operations window no longer stays open in the background when users are viewing comments on their PCI disputes.
* This release resolves an issue in the PCI disputes. The features for accepting and rejecting disputes have changed, and clients now receive the latest updates. When an ASV engineer rejects a dispute, it is automatically locked, and client users cannot make updates anymore. Remember that all rejected disputes have comments listing why the dispute was rejected.
* This release resolves an issue with renamed vulnerabilities. Renamed vulnerabilities can be marked inactive as expected.

#### Features

* This release updates the average scan time per host estimate. The estimate is now seven minutes.
* This release adds an alert at the policy level if a scan fails. When a scan fails due to insufficient time, a single click now allows the user to remove the end time. The insufficient scan time warning now contains links to the best practice documentation and the scan policy page.

#### Security

None

#### Changes

None

#### Notice

None

### Release date: August 31, 2016

#### Bug fixes

None

#### Features

* This release updates the Nmap network mapping tool to version 7.12. This update results in faster port scanning on full port scans, improved operating system detection, and improved service detection.
* This release improves coverage of JBoss vulnerabilities.
* This release improves detection of Oracle Weblogic server information.

#### Security

None

#### Changes

None

#### Notice

* Some operating systems and services may change in the reports. The new version of Nmap provides more detailed identifications.

### Release date: August 4, 2016

#### Bug fixes

* This release resolves an issue with reporting on services without a port. Services like ICMP now correctly reflect that a port is not applicable.
* This release resolves an issue with unknown port reporting. A special note for unknown ports sometimes appeared when Alert Logic detected the port. This has been corrected.

#### Features

* This release includes an update to the formatting of the PCI Vulnerability Report.
* This release adds a field for host name next to the IP address in a PCI report.
* This release adds a feedback form to PCI Report download pages. You may use this form to submit feedback on Alert Logic or any part of the PCI scanning process.

#### Security

None

#### Changes

* This release includes an annual update of the PCI ASV Certificate number to reflect success certification for 2016.

#### Notice

None

### Release date: July 14, 2016

#### Bug fixes

None

#### Features

* Scan reports include a new field that lists the status of the scan. The scan status can be Complete or Partial. If the scan status is partial, the report will include text indicating why the result was partial.
* Cloud Defender can now export a host report in .csv format. The report includes column headings and details in each column.
* Cloud Defender can now export a vulnerability report in .csv format. The report includes column headings and details in each column.

#### Security

None

#### Changes

* The domain name input fields on the PCI Scan Schedule page are in a new order. The text accompanying the fields is now clearer and easier to understand.

#### Notice

None

### Release date: June 29, 2016

#### Bug fixes

* This release improves logging and resolves several issues with false positives in Cisco HTTP, HTTP login, rlogin, SNMP, and Shellshock.

#### Features

None

#### Security

None

#### Changes

None

#### Notice

None

### Release date: May 9, 2016

#### Bug fixes

* This release corrects some STARTTLS FTP logic to improve compatibility with FTP servers.

#### Features

* This release adds a few dozen SSL certificates and improves the way Alert Logic obtains them to stay up-to-date.
* This release updates the scanner to look for the correct error code in proxy connections. This enhancement will reduce false positives and false negatives.
* This release adds several enhancements regarding Windows patch scanning. The scanner now runs an additional check to verify full registry access, and logs that get sent to the database  for Windows patch scanning have been improved for enhanced debugging.

#### Security

None

#### Changes

* This release reduces duplicate reporting of OpenSSL issues.

#### Notice

None

### Release date: April 19, 2016

#### Bug fixes

* This release fixes an issue with SSH checks for Cisco devices.
* This release changes the wording for CVE-2014-0224 (OpenSSL CSS Injection).

#### Features

* This release adds improvements to Shellshock scanning capabilities, including additional heuristic logic to prevent scanning certain hosts, additional improvements to reduce loads on target systems, and faster scan execution.
* This release resolves an issue with obsolete operating system checks for Windows XP and Windows 2003. The scanner now takes HTTP headers into consideration when checking the operating system version.
* This release adds more ports to the default UDP scan.
* SSL checks of default SSL ports now also checks port 3389 (Windows Remote Desktop/Terminal Services) for SSL.
* This release expands the list of default credentials for testing against SSH logins.
* This release adds detection of VMware services and default accounts.
* This release improves the overall scanning speed and detection reliability.
* This release improves the scanning appliance reliability.

#### Security

None

#### Changes

None

#### Notice

None

### Release date: March 31, 2016

#### Bug fixes

None

#### Features

* This release includes several features in PCI Reports:
   * Consolidated remediation for each IP address.
   * Reports show more information on the reasoning behind as assigned pass or failure.
   * The report now lists all ports, rather than just ports with known vulnerabilities.
   * The sort order has been updated. The new sort order is: IP, Port type, port, PCI Severity, CVSS Base Score (Descending), CVE.
   * Attestation of Compliance now lists all hosts in scope rather than live hosts in scope.

#### Security

None

#### Changes

None

#### Notice

None

### Release date: February 2, 2016

#### Bug fixes

None

#### Features

* This release adds several features to the PCI dispute process to speed up the scan-dispute-pass cycle. Customers can now see the acceptance or rejection of each dispute with specific notes as entered by the Alert Logic ASV engineer. Customers may also edit and add information to their dispute entry without running another scan.

#### Security

None

#### Changes

None

#### Notice

None

### Release date: January 28, 2016

#### Bug fixes

None

#### Features

None

#### Security

* This release upgrades the secure handling and storage of user scanning credentials in Cloud Defender to 2048-bit RSA.

#### Changes

None

#### Notice

None
