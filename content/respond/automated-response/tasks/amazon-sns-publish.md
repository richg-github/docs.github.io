# Configure a Send Message to Amazon SNS Topic Task (Draft)

In your automated response playbook, you can configure a Send Message to Amazon SNS Topic task to trigger an action in Amazon Web Services (AWS) by sending a message.

The task uses Amazon SNS to send a message from Alert Logic to:

* Endpoints subscribed to an Amazon Simple Notification Service (SNS) topic
* Mobile platform endpoint
* Phone number as a text (SMS) message

This task uses the Amazon SNS `Publish` action to send the message. For more information, see the [AWS documentation for the Publish action](https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/sns.html#SNS.Client.publish).

Complete the following steps to successfully configure the Send Message to Amazon SNS Topic  task:

1. [Create a connection target for the AWS IAM role](#CreateaconnectiontargetfortheAWSIAMrole)
2. [Add the task to your playbook](#Addthetasktoyourplaybook)
3. [Configure the task input](#Configurethetaskinput)
4. [Configure the task output (optional)](#Configurethetaskoutputoptional)

## Create a connection target for the AWS IAM role

The Send Message to Amazon SNS Topic task requires a connection target for the AWS IAM role that grants Alert Logic access to perform this action.

To check whether it exists,  in the Alert Logic console, click ![](../../../Resources/Images/dashboard/configure-icon.png)**Configure** in the navigation menu (![](../../../Resources/Images/dashboard/menu-icon.png)),  click **Connectors**, and then click the **Connection Targets** tab.

If any AWS IAM role connection targets appear in the list, review their configurations to determine whether the one you need already exists.

If you do not have a connection target for your AWS IAM role already, complete the instructions in [Configure AWS IAM Role Connection Target](../../../configure/connectors-beta/connection-targets/AWS-IAM-role.md).

## Add the task to your playbook

If you have not added the  task to your playbook, complete the instructions in [Add a task in the workflow diagram](../add-task.md#Addataskintheworkflowdiagram) and [Add task details (optional)](../add-task.md#Addtaskdetailsoptional).

## Configure the task input

Complete these instructions to provide the input values for your  Send Message to Amazon SNS Topic  task.

**To configure the task input:**

1. On the task **Input** tab, select the connection target in **AWS IAM Role Connection Target** that you created or identified in [Create a connection target for the AWS IAM role](#CreateaconnectiontargetfortheAWSIAMrole).
2. In **Amazon SNS Region**, enter the AWS region that the Amazon SNS topic is in.
If you are sending a message to endpoints, the AWS region of the topics and endpoints must be the same.
3. Enter a value in the field corresponding to how you want Amazon SNS to send a message:
Enter a value in only one of the fields and leave the other two blank.
   * **Phone Number to Text**—To send a message directly to a phone number as a text (SMS) message, enter the phone number in E.164 format (US example: +12225550100).
   * **Target ARN for Mobile Platform Endpoint**—To send a message to a mobile platform endpoint, enter the targeted endpoint ARN.
   * **SNS Topic ARN**—To send a message to endpoints subscribed to an SNS topic, enter the ARN of the SNS topic.
7. In **Message**, enter the message that you want to send.  
The text is either a string value or, if you are sending the message to an SNS topic and want a different message for each notification protocol, a JSON object. For more information, see the details about the `Message` parameter in the [AWS documentation for the Publish action](https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/sns.html#SNS.Client.publish).
8. (Optional) In **Message Subject**, enter the ASCII text that you want to use in the subject line for a message sent to an email endpoint. If present, the subject is included also in the JSON messages delivered to other endpoints.
For the format requirements, see the details about the `Subject` parameter in the [AWS documentation for the Publish action](https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/sns.html#SNS.Client.publish).
9. In **Message Structure**, if you are sending a message to endpoints subscribed to an SNS topic and want a different message for each notification protocol, select **json**. Otherwise, leave it blank.
For the format requirements, see the details about the `MessageStructure` parameter in the [AWS documentation for the Publish action](https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/sns.html#SNS.Client.publish).
10. In **Message Attributes**, enter structured information about the message if the message is a string value.
For the format requirements, see the details about the `MessageAttributes` parameter in the [AWS documentation for the Publish action](https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/sns.html#SNS.Client.publish) and [Amazon SNS message attributes](https://docs.aws.amazon.com/sns/latest/dg/sns-message-attributes.html).
11. (Optional) If you are sending a message to a first-in-first-out (FIFO) topic and want to provide a token for deduplication of sent messages, enter a unique identifier in **Message Deduplication ID**.
For the format requirements, see the details about the `MessageDeduplicationId` parameter in the [AWS documentation for the Publish action](https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/sns.html#SNS.Client.publish).
12. In **Message Group ID**, if you are sending a message to a FIFO topic, enter a tag to specify that the message belongs to a specific message group.
For the format requirements, see the details about the `MessageGroupId` parameter in the [AWS documentation for the Publish action](https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/sns.html#SNS.Client.publish).

### Insert a YAQL expression in an input field

Any field that supports one or more [Yet Another Query Language](https://yaql.readthedocs.io/en/latest/) (YAQL) expressions has a **SELECT VARIABLE** drop-down list above the field. A YAQL expression can  reference a value in the playbook context, such as a field in the incident payload, or the published result of a previous task.

To insert a YAQL expression, place your cursor in the field where you want to insert the reference, click **SELECT VARIABLE**, and then select the variable. A YAQL expression that references the selected value appears in the field.

## Configure the task output (optional)

This task generates the following results when it completes. You can publish a current task result or other values by adding them as output. Published output  is available for reference in later playbook tasks. For instructions, see [Configure task output (optional)](../add-task.md#Configuretaskoutputoptional).

* **MessageId** (*string*)—Unique identifier assigned to the published message
   * *Suggested rewrite:* Unique identifier that Amazon SNS assigns to a published message
* **SequenceNumber** (*string*)—Sequence number (for FIFO topics)
   * *Suggested rewrite:* Sequence number (for FIFO topics only) that Amazon SNS assigns to each message

## Technical reference

[Ideally this paragraph would state why the following information is useful, what to do with it...]

### Action Name

Send Message to Amazon SNS Topic

### Action Type

sns_publish

### Permissions

[Include this section if needed. Example:  Azure permissions.]

### Limitations

[Include this section if needed. Example: This action only works in AWS regions supported by Alert Logic.]
