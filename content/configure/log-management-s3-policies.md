# Log Management S3 Policies

S3 collection policies set the guidelines for collecting Amazon Simple Storage Service (S3) access logs, which provide details about a single access request, such as the requester, bucket name, request time, request action, response status, and any error codes. S3 policies allow you to collect S3 logs for Alert Logic to review.

Alert Logic also allows you to create other types of Log Management policies. These policies dictate how Alert Logic collects log messages, and allows you to reuse this common configuration for several log sources of the same type. To learn more about other log management policies, see the links below:

* [Log Management Flat File Policy](log-management-flat-file-policy.md)
* [Log Management Windows Event Log Policies](log-management-windows-event-policies.md)
* [Log Management Syslog Policies](log-management-syslog-policies.md)

## Configure S3 collection policies

To access the Log Management policies page, click **CONFIGURATION**, click **Log Management**, and then click **Policies** in the left navigation panel.

You must create an S3 collection policy before you can create a S3 collection source. For more information, see [Configure Log Sources for Amazon Web Services (AWS)](../deploy/log-sources/log-sources-aws.md#flatFileLogs).

After you create the S3 collection source, the collection source executes the S3 collection policy.

If you update, archive, or delete any collections or policies, you could break interconnected configurations.

### Create a S3 collection policy

No default policy exists for the S3 collection policy. You must create a default policy for the S3 collection policy to use this feature.

**To create a S3 collection policy**:

1. Access the Log Management Policies page and click the **S3** tab.
2. Click the add icon (![](../Resources/Images/Icons/cdAddPlus.png)).
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
2. Click the trash icon (![](../Resources/Images/Icons/trash icon.png)) for the S3 collection policy to delete.
3. Click **DELETE**.
