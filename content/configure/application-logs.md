# Application Logs for Flat File Configuration

The application logs feature allows you to configure applications with functional APIs  to automatically collect logs from multiple sources, using tag and topology-based asset scoping in the Alert Logic console. You can also copy an existing log configuration to create a new one, and edit it as necessary.

The log collection configuration is a streamlined workflow with specific application log templates. Log collection allows you to configure flat file logs, which are log messages stored in flat text files. Flat files are a common log message format for web servers and other server software.

To access the log collection setup, click the menu icon (![](../Resources/Images/dashboard/menu-icon.png)) from the Dashboards page. Click ![](../Resources/Images/dashboard/configure-icon.png)**Configure**, and then click the deployment for which you want to configure collections. On the left navigation panel, click **Logs**, and then click **Application Logs**.

This document only applies to new Managed Detection and Response Professional and Enterprise customers who are configuring flat file collections for the first time. If you have previously configured flat file collections, see [Log Management Flat File Policy](log-management-flat-file-policy.md).

## Application log collections  

The Application Logs page lists applications logs that have templates with predefined fields, including ones that are not yet enabled. Click the drop-down menu to view all application logs or only view existing application logs that are enabled. You can use the search bar to find a specific log collection definition. You can preview, edit, manage assets, duplicate and delete existing application logs.

## Add a new application log 

The collection method and policy determines which flat file log messages to collect, how to separate log messages within a flat file, and how to read the time of each log message. Asset scoping determine the asset tags, assets, or topology elements from which Alert Logic collects logs.

After you have filled out all required fields and scoped assets, you must turn on **Collect** for the application to start collecting log data.

**To add a new application log with rules**:

1. Click the add icon (![](../Resources/Images/Icons/cdAddPlus.png)).
2. In the drop-down list, select an application log template.
3. In the **Application Name** field, type a name for your application in the field.
4. To automatically enable collection from the application, select the check box.
5. Under Collection Method and Policy, in the  **Application File Path** field, type the path information.                
To use an agent for collection, specify the local file system path to the log files.
6. In the **File Name or Pattern** field, type the file name or date pattern of the flat file name. Alert Logic can only collect flat file log messages that match the pattern.For more information about pattern matching, see [File name pattern syntax ](#File2).                
For WLA deployments on IIS web servers, you must use the file path pattern processed by the Filebeat agent.
7. In the File Name Rotation Scheme section, select a file name rotation scheme. The format must match the format of your flat file log name. Alert Logic recommends that you specify the rotation scheme format of your flat file name. For more information about rotation scheme, see [File log formats](#File).                The default **Auto-Detect** identifies many rotation schemes. If you are unsure of the format, or if you do not find the specific format from the drop-down menu, select **Auto-Detect**.
8. In the Multiline Handling section, select a multiline handling option:
   * If all of your flat file messages contain log entries with a single or separate line, select **Single line log messages**.
   * If all of your flat file log messages contain log entries that span multiple lines, select **Log messages with multiple lines**, and then select and enter a configuration:
      * If the lengths of your log messages are consistent, select **Each log message spans a fixed number of lines**, and then specify the number of lines.
      * If the lengths of your log messages are not consistent:
         1. Select **Each log message follows a known pattern**.
         2. Select the appropriate **Pattern application**.
         Pattern application options:
            * **At the beginning of message**: A line that matches the specified pattern marks the beginning of a new message; non-matching lines are grouped into the prior message.
            * **In the middle of message**: A line that does not match the specified pattern marks the middle of a new message; matching lines are grouped into the prior message.
            * **At the end of message**: A line that matches the specified pattern marks the end of a message; non-matching lines prior to that are grouped into this message.
         4. Type the **Pattern** for the log message.
         5. If your pattern is a Perl Compatible Regular Expression (PCRE), select **Regular expression**.
10. In Timestamp Rule section, select a timestamp rule option:
   * To use a custom timestamp, select **Parse file name using a custom timestamp format**, and then enter a format for the date string in the expanded configuration area. In the **Format of date string** field, type a format for the date string, and follow the on-screen instructions.
   * To use an existing timestamp, select **Parse file name using a pre-defined timestamp format**, and then choose a format from **Select a format**.
   * To use the timestamp from the collector, select **Set message time as collect time**.
14. Click **SAVE AND NEXT**.
15. In the Manage Assets section, search for assets from which to collect logs.
16. Select the tags or topology elements from the drop-down list. Tags are separated by <kbd>AND</kbd>, and topology elements are separated by <kbd>OR</kbd>. Tags and topology elements are separated by <kbd>OR</kbd>.
17. Click **SAVE**.
18. Ensure **Collect** is turned on for the application you just created in the Application Logs list.

### File name pattern syntax 

File name or pattern must determine a single log stream. Multiple rotated log file names can represent a single log stream, but the only variables allowed for the same log stream across multiple log files are date/integer, constant, or blank.  The agent will fail to collect if the file name or pattern matches multiple log streams.

The file name or pattern can contain multiple wildcard symbols (*), as long as all existing files that match the pattern constitute a single log stream. This means that the file name or pattern can be sorted unambiguously according to the explicitly specified file rotation scheme or auto-detected file rotation scheme. The rotation scheme can be specified as one of the following:

* Use a predefined timestamp format
* Use a custom timestamp format
* Use an increasing counter format
* Use an increasing counter format

If you specify <kbd>*.log*</kbd> as a pattern, and there are only <kbd>access-2019-12-01.log</kbd> and <kbd>access-2019-12-06.log</kbd> files in the directory (both match the specified pattern and the only variable part is the date), collection succeeds. If there are only <kbd>access.log.2019-12-01</kbd> and <kbd>access.log.2019-12-06</kbd>, collection succeeds.

However, if there are <kbd>access.log</kbd> and <kbd>error.log</kbd>, collection fails since both files match the specified pattern, but variable parts of the file names match something other than the specified or detected date pattern.

A predefined timestamp format option assumes automatic format detection by the agent based on the predefined list of formats. The agent tries to iterate over each of the predefined patterns until it matches a single log stream.

The **Application File Path** field can also contain multiple wildcard * symbols. The wildcard in Application File Path matches a part of the directory name. It allows the agent to collect the same log stream from multiple directories. The agent determines these directories based on the pattern with wildcards specified in Application File Path.

### File log formats

No industry standard exists to structure flat file log naming. As a result, log formats vary by computer and device. Alert Logic supports gzip, bzip2, and zip compressed logs. The rotation scheme is the order that the date appears within the log message. For example, flat files may contain variable data like dates in MM.DD.YYYY (month, day, year) or DD.MM.YYYY (day, month, year) format.

When you define a log rotation schema, you instruct Alert Logic how to identify:

* Active log file into which new log messages are written
* Rotated log files into which no new log messages are written
* Order in which rotated log files are collected (such as which files have the oldest or most recent messages)

The Alert Logic console automatically detects standard log rotation formats and also provides other common formats for selection during setup.

Rotation patterns can be detected in the following order:

* Epoch Timestamp
* YYYY-MM-DDThh_mm_ss
* YYYY-MM-DD
* MM-DD-YYYY
* MM-DD-YY
* MM.DD.YYYY
* MM.DD.YY
* MM_DD_YYYY
* MM_DD_YY
* YYYYMMDD_hhmmss
* YYYYMMDD
* YYMMDDhh
* YYMMDD
* YYMM

DD-MM-YYYY date patterns and increasing or decreasing integer counter patterns cannot be auto-detected due to ambiguities. You must specify increasing or decreasing integer counter explicitly. All files matching the specified file name pattern must conform to a single date or counter rotation pattern (a blank date or counter is allowed). Otherwise, collection errors will result.

The following is a list of supported flat file rotation format examples:

   * **YYYYMMDD (IIS Native Method)**:
      * The currently active log file is <name>.log. For example: ex.log
      * Periodically, a new active file is created and the old active file is renamed to reflect the date: <name>YYYYMMDD.log. For example: ex20091230.log
      * Alert Logic collects from each file in order, based on the date in each file name.
   * **YYYYMMDD (append method)**:
      * The currently active log file is given the form: <name>.YYYYMMDD
      * Periodically, a new log file is created and becomes the active log file.
      * Alert Logic collects from each file in order, based on the date in each file name.
   * **Epoch Timestamp**
      * The currently active log file is given the form: <name>.<timestamp>
      * Periodically, a new log file is created and becomes the active log file.
      * Alert Logic collects from each file in order, based on the timestamp in each file name.
   * **Incrementing Integer Method (logrotate)**
      * The currently active log file is <name>
      * Periodically, the active log file is renamed to <name>.1, <name>.2 to <name>.3, and so forth.
      * Alert Logic collects from each file in order, based on the numeric suffix.
   * Other similar formats are also supported, and is based on the date in each file name according to the pattern provided:
      * YYMM
      * MM-DD-YY
      * MM_DD_YYYY
      * DD_MM_YY
      * YYMMDD
      * MM.DD.YYYY
      * DD-MM-YY
      * DD-MM-YYYY
      * YYMMDDhh
      * MM.DD.YY
      * DD.MM.YYYY
      * DD_MM_YYYY
      * MM-DD-YYYY
      * MM_DD_YY
      * DD.MM.YY
      * YYYY-MM-DD
      * YY-MM-DD

#### Define the rotation scheme

The rotation scheme is the order that the date appears within the log message. For example, Flat Files may contain variable data like dates in MM.DD.YYYY (month, day, year) or DD.MM.YYYY (day, month, year) format.

The Alert Logic console automatically detects standard log rotation formats and also provides other common formats for selection during setup.

#### Choose a single or multi-line log

By default, Alert Logic assumes that each message is contained on a single line. When a single message spans multiple lines, you must:

* **Define a fixed number of lines per log message**, or
* **Use a known pattern** that matches the beginning, middle, or end of each log message. This pattern can be a simple Perl Compatible Regular Expression (PCRE).

#### **Pick the desired time stamp method**.

Choose one of the following options to configure the time stamp for each Flat File:

* Choose the local time zone and settings of the log source.
* Choose one of several predefined rules.
* Create a custom time format.

## Collecting application logs

To view enabled application logs only, click the drop-down menu in the Application Logs list, and then select **Collecting Application Logs**. You can also use the search bar to find a specific application log collection. Click **View** to view details on enabled application logs.

### Edit an existing application log 

To edit an existing application log:

1. From the preview,  click the edit icon (![](../Resources/Images/pencil icon.png)) for the application log collection you want to edit.
2. Make the necessary changes. For more information, see [Add a new application log ](#Add-new-application-rule).
3. Click **SAVE**.

### Manage assets

1. From the preview, click the assets icon (![](../Resources/Images/Icons/assets.png)) for the application log collection you want to scope assets.
2. In the Manage Assets section, select or clear the tags or topology elements from the drop-down list. For more information, see [Add a new application log ](#Add-new-application-rule).
3. Click **SAVE**.

### Duplicate an existing application log 

**To duplicate an existing application log:**

1. From the preview, click the duplicate icon (![](../Resources/Images/Icons/duplicate.png)) for the application log collection you want to copy.
2. Make the necessary changes. For more information, see [Add a new application log ](#Add-new-application-rule).
3. Click **SAVE**.

### Delete an existing application log

To delete an existing application log, from the preview,  click the delete icon (![](../Resources/Images/Icons/trash icon.png)) for the application log collection you want to edit.Click **DELETE**.
