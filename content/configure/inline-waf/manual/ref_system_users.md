# Users

The System Users page includes the following sections. Click on the link to go to the corresponding section to learn more:

<!--<MadCap:menuProxy mc-linked-toc="$topicHeadings" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />-->
To go to the documentation for the previous section of System, see [Updates](ref_system_updates.md). To go to  the next section in the manual section, see [Network Deployment](ch_network.md).

To access the Users page in the **WAF** management interface, on the left panel, under System, click **Users**.

To save configuration changes or edits you make to any features and options, you must click **Save** on the lower-right of the section or page where you are making changes. Click **apply changes** on the upper-left corner of the page, and then click **OK**. Your changes will not be stored if you do not properly save your changes.

The user document contains tools for user administration.

### User accounts

Alert Logic Managed Web Application Firewall (WAF) has two built in user accounts cannot be deleted. In addition the Administrator account can create and modify administrative accounts for additional users.

#### Built in user accounts

WAF has two built-in user accounts which cannot be deleted.

<dl><dt>        Administrator      </dt><dd>The administrator account named `admin` is used for administration of WAF in the web based management interface.
The administrator account can perform any system or proxy task in the management interface including creating and deleting new administrative users.</dd><dt>        Console operator      </dt><dd>The console operator named `operator` is the user account used to access the system console CLI. This account can only perform basic system related administrative tasks and only in the system console.
Password for the console operator can only be changed using the command-line (CLI) interface. For information on how to change it, use set password CLI command</dd></dl>#### Additional accounts

Apart from user administration additional accounts created by the administrator have the same privileges as the built in administrator account.

### Current user

This section allows the current user to change password. Minimum required length is 8 characters. Maximum length is 32 characters.

To change password enter the following information in the password fields:

**        Old password      **: enter the old password

**        New password      **: enter the new password

**        Repeat new      **: repeat the new password

To save the changes, click on the **Apply** button.

### System users

The system users section allows the administrator to add, delete and modify other system users.

To add a new user enter the users information in an empty row and click the **Save changes** button.

<colgroup></colgroup>| **                User name              ** Input field | The user name the user logs in with.<dl><dt>                  Valid input                </dt><dd>Text and special characters.</dd><dt>                  Input example                </dt><dd>`fester@somedomain.com`</dd><dt>                  Default value                </dt><dd>`None`</dd></dl> |
| **                Real name              ** Input field | The users real name<dl><dt>                  Valid input                </dt><dd>Text and special characters.</dd><dt>                  Input example                </dt><dd>`Fester Bestertester`</dd><dt>                  Default value                </dt><dd>`None`</dd></dl> |
| **                Set new password              ** Input field | The users password.<dl><dt>                  Valid input                </dt><dd>Any string</dd><dt>                  Input example                </dt><dd>`fdasdfdaqdbasdas`</dd><dt>                  Default value                </dt><dd>`None`</dd></dl> The password field is blank for existing users. To change a users password enter a new password in the field. |
| Type Dropdown |  |
| Status Dropdown |  |
| Last login Input field |  |
| Failed Input field |  |
| X Button |  |
| **                Add row              ** Button | Click this button to add an empty row if necessary. |
| **                Save changes              ** Button | Click this button to save changes to the table. |
