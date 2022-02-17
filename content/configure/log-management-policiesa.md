# Log Management Policies

Alert Logic allows you to create four types of Log Management policies. These policies dictate how Alert Logic collects log messages, and allows you to reuse this common configuration for several log sources of the same type.

* Flat File policy allows you to collect flat file messages. This is a common log message format for web servers and other server software.
* Syslog policy allows you to collect syslog messages, which are a way for network devices to send event messages to a logging server – usually known as a syslog server.
* Windows Event Log policy allows you to collect event log files that track significant events on a Windows server, such as user logins or program errors.
* S3 Policy sets guidelines for collecting Amazon Simple Storage Service (S3) access logs, which provide details about a single access request, such as the requester, bucket name, request time, request action, response status, and error code.

Alert Logic automatically assigns either a Windows Event Log or Syslog source to each host in your environment. To edit a default collection source, you must create a new Windows Event Log or Syslog policy. Also, to collect Flat File or S3 log messages, you must create a new collection policy, and then create the corresponding collection source.

To access the Log Management policies page, click **CONFIGURATION**, click **Log Management**, and then click **Policies** in the left navigation panel.

## Configure Flat File collection policies

Flat File log messages are a common log message format that can be collected, stored, and normalized similarly to Windows Event Log messages and Syslog messages. A Flat File policy lets you collect Flat Files for Alert Logic to review.

You must create a Flat File collection policy before you can create a Flat File collection source. For more information, see [Configure Flat File log sources](../deploy/log-sources/log-sources-all-deployments.md#flatFileLogs).

After you create the Flat File collection source, the collection source executes the Flat File collection policy.

If you update, archive, or delete any collection or policies, you could break interconnected configurations.

### Configurations for Flat File collection policy

No industry standard exists to structure Flat File log messages. As a result, log formats vary by computer device.

#### Enable collection and parse logs

1. **Define the rotation schema**. The rotation schema (or pattern) is the order that the date appears within the log message. For example, Flat Files may contain variable data like dates in MM.DD.YYYY (month, day, year) or DD.MM.YYYY (day, month, year) format.

For Linux users, the Alert Logic console automatically detects standard Linux log rotate formats and also provides other common formats for selection during set up.3. **Choose a single or multi-line log**. By default, Alert Logic assumes that each message is contained on a single line. When a single message spans multiple lines, you must:
   1. **Define a fixed number of lines per log message**, or
   2. **Use a known pattern** that matches the beginning, middle, or end of each log message. This pattern can be a simple Perl Compatible Regular Expression (PCRE).
5. **Pick the desired time stamp method**. Choose one of the following three options to configure the time stamp for each Flat File:
   * Create a custom time format.
   * Choose one of several predefined rules.
   * Choose the local time zone and settings of the log source.

#### Supported Flat File rotation formats

Alert Logic supports gzip, bzip2, and zip compressed logs. When you define a log rotation format, you are instructing Alert Logic how to identify:

* The active log file, into which new log messages are written.
* Rotated log files, into which no new log messages are written.
* The order in which rotated log files are collected (i.e. which files have the oldest or most recent messages).

The following is a list of supported Flat File rotation format examples:

   * **YYYYMMDD (IIS Native Method)**:
      * The currently active log file is <name>.log. For example: ex.log
      * Periodically, a new active file is created and the old active file is renamed to reflect the date: <name>YYYYMMDD.log. For example: ex20091230.log
      * Alert Logic collects from each file in order, based on the date in each file name.
   * **YYYYMMDD (append method)**:
      * The currently active log file is given the form: <name>.YYYYMMDD
      * Periodically, a new log file is created and become the active log file.
      * Alert Logic collects from each file in order, based on the date in each file name.
   * **Epoch Timestamp**
      * The currently active log file is given the form: <name>.<timestamp>
      * Periodically, a new log file is created and become the active log file.
      * Alert Logic collects from each file in order, based on the timestamp in each file name.
   * **Incrementing Integer Method (logrotate)**
      * The currently active log file is <name>
      * Periodically, the active log file is renamed to <name>.1, <name>.2 to <name>.3, and so forth.
      * Alert Logic collects from each file in order, based on the numeric suffix.
   * Other formats are collected in a similar format, based on the date in each file name according to the pattern provided:
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

### Create a Flat File collection policy

The collection policy determines which Flat File log messages to collect, how to separate log messages within a Flat File, and how to read the time of each log message. Also, the collection policy can specify when Alert Logic collects messages from associated log sources.

To create a Flat File collection policy:

1. Access the Log Management Policies page and click the **Flat File** tab.
2. Click the add icon (![](../Resources/Images/Icons/cdAddPlus.png)).
3. In **Flat File Policy Name**, type a descriptive name.
4. In **Source File Path**, type the path information.

To use an agent for collection, specify the local file system path to the log files. Otherwise, specify the network share path to the log files.6. In **File Name or Pattern**, type the file name or date pattern of the flat file log messages. Alert Logic can only collect Flat File log messages that match the pattern.

<kbd>htaccess.*</kbd> is a file name with a pattern. The * represents the time stamp of the flat file log. Alert Logic accepts a variety of date formats.8. From **File Name Rotation Scheme**, select a file name rotation scheme. The format must match the format of your Flat File log messages.

The default **Auto-Detect** identifies many rotation schemes. Alert Logic recommends you specify the rotation scheme format of your Flat File log messages. If you are unsure of the format, or if you do not find the specific format from the drop-down menu, select **Auto-Detect**.10. In **Multi-line Handling**, select a multi-line handling option:
   * If all of your flat file log messages do not contain a single line, select **File contains log messages with multiple lines**. Also, select and enter a configuration:
      * If the lengths of your log messages are consistent, keep the selection **Each log message spans a fixed number of lines**, and then specify the number of lines.
      * If the lengths of your log messages are not consistent:
         1. Select **Each log message follows a known pattern**.
         2. Select the appropriate **Pattern application**.
         3. Type the **Pattern** for the log message.
         4. If your pattern is a Perl Compatible Regular Expression (PCRE), select **Regular expression**.
   * If all of your flat file log messages contain a single line, keep the selection: **File contains single line log messages**.

Pattern application options:   * **At the beginning of message**: A line that matches the specified pattern marks the beginning of a new message; non-matching lines are lumped into the prior message.
   * **In the middle of message**: A line that does not match the specified pattern marks the beginning of a new message; matching lines are lumped into the prior message.
   * **At the end of message**: A line that matches the specified pattern marks the end of a message; non-matching lines prior to that are lumped into this message.
15. In **Timestamp Rule**, select a timestamp rule option:
   * To use a custom timestamp, **select Parse file name using a custom timestamp format**, and then enter a format for the date string in the expanded configuration area. In the **Format of date string** field, type a format for the date string, and follow the on-screen instructions.
   * To use an existing timestamp, select **Parse file name using a pre-defined timestamp format**, and then choose a format from **Select a format**.
   * To use the timestamp from the collector, keep the selection **Set message time as collect time**.
19. In **Host Credential**, select or create a credential:
If you use the Alert Logic agent for log collection, do not select or create host credentials.
   * To use an existing credential, keep the default selection: **Use an existing credential**, and then from **Choose a credential**, select a credential.
   * To create a new credential, select **Create a new credential**, and then enter new credentials. In the corresponding configuration fields, type a **Credential Name,****Host Username**, and **Host Password**. In the **Retype Password** field, retype the host password.
21. In **Collection Schedule**, select or create a collection schedule:
   * To create a new collection schedule:
      1. Select **Create a new schedule**.
      2. Enter and select the schedule options.
      3. Type a **Schedule Name**.
      4. Select a **Schedule Time Zone**.
      5. Select **Blackout** to enable blackout periods, or add or remove extra blackout periods.
   * To select a collection schedule, keep the default selection: **Use an existing schedule**, and then from **Choose a schedule**, select a schedule.
24. Click **SAVE**.

### Update a Flat File collection policy

To update a Flat File collection policy:

1. Access the Log Management Policies page and click the **Flat File** tab.
2. In the list of Flat File collection policies, click the pencil icon (![](../Resources/Images/pencil icon.png)) for the collection policy to edit.
3. Make the necessary updates. For more information, see [Create a Flat File collection policy](#Create).
4. Click **SAVE**.

### Delete a Flat File collection policy

To delete a Flat File collection policy:

1. Access the Log Management Policies page and click the **Flat File** tab.
2. Click the trash icon (![](../Resources/Images/Icons/trash icon.png)) for the Flat File collection policy to delete.
3. Click **DELETE**.

## Configure Syslog collection policies

Syslog is a way for network devices to send event messages to a logging (syslog) server. A Syslog policy lets you collect syslog files for Alert Logic to review.

You must create a Syslog collection policy before you can create a Syslog collection source. For more information, see [Configure Syslog source  ](../deploy/log-sources/log-sources-all-deployments.md#syslogLogs).

If you update, archive, or delete any collections or policies, you could break interconnected configurations.

### Create a Syslog collection policy

**To create a Syslog collection policy**:

1. Access the Log Management Policies page and click the **Syslog** tab.
2. Click the add icon (![](../Resources/Images/Icons/cdAddPlus.png)).
3. In **Syslog Policy Name**, type a descriptive name.
4. In **Syslog Listen Port**, type the port where the agent receives Syslog messages.
5. In **Local Syslog Cache Disk Limit (MB)**, type the maximum amount of disk space you want to allow to store Syslog messages before they are transmitted to Alert Logic. Larger values allow the agent to store more message when the agent is unable to transmit message to Alert Logic.
6. In **Collection Schedule Blackout Periods**, select or create a collection schedule:
   * To select a collection schedule, keep the default selection: **Use an existing schedule**, and then from **Choose a schedule**, select a schedule.
   * To create a new collection schedule:
      1. Select **Create a new schedule**.
      2. Enter and select the schedule options.
      3. Type a **Schedule Name**.
      4. Select a **Schedule Time Zone**.
      5. Select **Blackout** to enable blackout periods, or add or remove extra blackout periods.
8. Click **SAVE**.

### Update a Syslog collection policy

**To update a Syslog collection policy**:

1. Access the Log Management Policies page and click the **Syslog** tab.
2. In the list of syslog collection policies, click the pencil icon (![](../Resources/Images/pencil icon.png)) for the syslog collection policy to edit.
3. Make the necessary updates. For more information, see [Create a Syslog collection policy](#Create2).
4. Click **SAVE**.

### Delete a Syslog collection policy

**To delete a Syslog collection policy**:

1. Access the Log Management Policies page and click the **Syslog** tab.
2. Click the trash icon (![](../Resources/Images/Icons/trash icon.png)) for the syslog collection policy to delete.
3. Click **DELETE**.

## Configure Windows Event Log collection policies

Windows Event Log files track significant events on a Windows server, such as user login or program errors. A Windows Event Log policy lets you collect event log files for Alert Logic to review.

If you update, archive, or delete any collections or policies, you could break interconnected configurations.

### Create a Windows Event Log collection policy

**To create a Windows Event Log collection policy**:

1. Access the Log Management Policies page and click the **Windows Event Log** tab.
2. Click the add icon (![](../Resources/Images/Icons/cdAddPlus.png)).
3. In **Windows Event Log Policy Name**, type a descriptive name.
4. In **Collection Schedule Blackout Periods**, select or create a collection schedule:
   * To create a new collection schedule:
      1. Select **Create a new schedule**.
      2. Enter and select the schedule options.
      3. Type a **Schedule Name**.
      4. Select a **Schedule Time Zone**.
      5. Select **Blackout** to enable blackout periods, or add or remove extra blackout periods.
   * To select a collection schedule, keep the default selection: **Use an existing schedule**, and then from **Choose a schedule**, select a schedule.
7. Choose one of the following:
   * To collect specific Windows Event Log streams, clear **Collect All Available Event Log Streams** and select your desired streams under **Alert and Collect on Selected Streams**.
   * To collect all Windows Event Log streams, keep the default selection **Collect All Available Event Log Streams** selected.
10. Click **SAVE**.

### Update a Windows event log collection policy

**To update a Windows event log collection policy**:

1. Access the Log Management Policies page and click the **Windows Event Log** tab.
2. In the list of Windows Event Logs, click the pencil icon (![](../Resources/Images/pencil icon.png)) for the Windows Event Log to edit.
3. Make the necessary updates. For more information, see [Create a Syslog collection policy](#Create2).
4. Click **SAVE**.

### Delete a Windows Event Log collection policy

**To delete a Windows Event Log collection policy**:

1. Access the Log Management Policies page and click the **Windows Event Log** tab.
2. Click the trash icon (![](../Resources/Images/Icons/trash icon.png)) for the Windows event log policy to delete.
3. Click **DELETE** to confirm.

## Configure S3 collection policies

S3 collection policies set the guidelines for collecting Amazon Simple Storage Service (S3) access logs, which provide details about a single access request, such as the requester, bucket name, request time, request action, response status, and error code, if any. S3 policies allow you collect S3 logs for Alert Logic to review.

You must create an S3 collection policy before you can create an S3 collection source.

If you update, archive, or delete any collections or policies, you could break interconnected configurations.

### Create a S3 collection policy

No default policy exists for the S3 collection policy. You must create a default policy for the S3 collection policy to use this feature.

**To create a S3 collection policy**:

1. Access the Log Management Policies page and click the **S3** tab.
2. Click the Add icon (![](../Resources/Images/Icons/cdAddPlus.png)).
3. In the **Name field**, enter a name for the new S3 policy.
4. In Policy Template, select **Customized**.
5. **In Multiline Handling**, select a multiline handling option:
   * If some of your log messages are longer than a single line, select **File contains log messages with multiple lines**. Also, select and enter a configuration:
      * If the lengths of your log messages are consistent, select **Each log message spans a fixed number of lines** and then type the number of lines in **Number of lines**.
      * If the lengths of your log messages are not consistent, select **Each log message follows a known pattern**, select the appropriate **Pattern application**, type the Pattern that takes place in the log message, and then select **Regular expression** to use a Perl Compatible Regular Expression (PCRE).
   * If all of your S3 log messages contain a single line, select **File contains single line log messages**.
8. Select a **Timestamp Rule** option:
   * To use a custom timestamp, select **Parse times from messages using a custom timestamp format**. Follow the on screen instruction and then enter a format for the date string in the **Custom** field. Click **Check Format**, to check that the format is valid.
   * To use an existing timestamp, select **Parse times from messages using a pre-defined timestamp format**, and then select a format from **Format of date string**.
   * To use the timestamp from the collector, select **Set message time as collect time**.
12. Click **SAVE**.

### Update an S3 collection policy

To update a S3 collection policy**:**

1. Access the Log Management Policies page and click the **S3** tab.
2. In the list of S3 policies, click the pencil icon (![](../Resources/Images/pencil icon.png)) for the S3 collection policy to edit.
3. Make necessary changes to:
   * The selected **Policy Template**. For information about settings for a Customized policy template, see [Create a S3 collection policy](#Create3).
   * The policy **Name**
6. Click **SAVE**.

### Delete a S3 collection policy

**To delete a S3 collection policy**:

1. Access the Log Management Policies page and click the **S3** tab.
2. Click the trash icon (![](../Resources/Images/Icons/trash icon.png)  ) for the S3 collection policy to delete.
3. Click **DELETE**.
