# Reports

The Alert Logic Managed Web Application Firewall (WAF) Reports page includes the following sections. Click on the link to go to the corresponding section to learn more:

<!--<MadCap:menuProxy mc-linked-toc="$topicHeadings" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />-->
To go to the documentation for the previous section of the manual, see [Log](ref_services_log.md). To go to  the documentation for next subsection in the Reports subsection, see [Statistics](ref_services_statistics.md).

**To access the Reports page in the WAF management interface**:

1. On the left panel, under Services, click **Websites**.
2. On the Websites page, click the website you want to manage.
3. Under Reports, click **Reports**.

To save configuration changes or edits you make to any features and options, you must click **Save** on the lower-right of the section or page where you are making changes. Click **apply changes** on the upper-left corner of the page, and then click **OK**. Your changes will not be stored if you do not properly save your changes.

## Reports

Generation of reports which can be saved or printed for offline viewing.

<colgroup></colgroup>| **              ACL Report            ** Link | Generate a printable report based on the current ACL. The generated report shows the global URL and parameter settings, static content allowed and individual ACL entries in the database. The report will open a new browser window or tab. |
| **              Log Report            ** Link | Generate a printable report with the current log entries. Note that the report is generated according to the current log-filter criteria. The report will open a new browser window or tab. |
| **              Log export (XML)            ** Link | Export log to XML. If no filter criteria are specified the complete log will be exported. Depending on log size and filter criteria it may take a while to generate the report. It is therefore generated in the background and made available for download in the Generated proxy log reports section. |
| **              Log export (RAW)            ** Link | Raw export of the complete log in sqlite database format. Depending on log size and filter criteria it may take a while to generate the report. It is therefore generated in the background and made available for download in the Generated proxy log reports section. |

## Generated reports

Reports generated in the background are made available for download in the *Generated reports* section.

<colgroup></colgroup>| **              File name            ** Link | Click the file name to download or open the report. |
| **              Export date            ** Read only | The date the report was generated. |
| **Size** Read only |  |
| **              Status            ** Read only | Status of the report generation. When status is *Done*, the report is ready for download. |

## Retired log data 

<colgroup></colgroup>| **              File name            ** Link | Click the file name to download or open the report. |
| **              Export date            ** Read only | The date the report was generated. |
| **Size** Read only |  |
| **              Status            ** Read only | Status of the report generation. When status is *Done*, the report is ready for download. |
