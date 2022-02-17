# Customer Accounts, User Accounts, and User Roles

The account provisioning process includes the creation of a customer account for your organization and a user account, with the Administrator role applied, under that customer account. Users in your organization with administrator privileges can log into the Alert Logic console to create and manage the user accounts required for your organization.

For information about managing your own user account, see [Manage Your User Account](manage-user-account.md).

## Customer accounts 

The customer account represents the environment you want to protect. When you log in to your user account, the top right of the Alert Logic console displays the name of the customer account and your user account. If your organization manages assets for other customer accounts, you can remain logged into your user account and view any customer account associated with your organization.

### Multi-account management

The account selector allows you to monitor all the managed (child) accounts in your organization. If you use this feature to change your account selection to that of a managing (parent) account, you can monitor, assess, and compare the security posture across the entire organization.

Click the account name located in the upper right of your screen to view the full list of accounts in your organization. From the drop-down, select a parent account. You can use the search feature to narrow the list.

If your organization manages assets for other customer accounts, you could see data from child accounts on the Incidents page and the Reports page.

For all other features, the Alert Logic console displays results only for the chosen customer account. If, on any feature page, you want to view results for only a specific managed account, use the account selector to change the customer account.

## User accounts

User accounts allow individual users access to the Alert Logic console. Users with the appropriate permissions can create and manage user accounts and define the permissions for each account.  In addition, user accounts with the administrator role can require all users to set up multi-factor authentication to log into the Alert Logic console. For more information, see [Multi-factor Authentication](mfa.md).

### User account list

To view the list of user accounts in your organization account, open the navigation menu in the Alert Logic console, click the ![](../Resources/Images/dashboard/manage-icon.png)Manage menu item, and then select **Users**.

### User Roles

Alert Logic provides five roles, each with different permissions, to be assigned to user accounts. When you create a user account, you must also assign the account a role that determines the information the user can see and the activities they may perform on their own account and other accounts.

All user account holders can see the full customer account list and the summary and dashboard pages for those customer accounts. Therefore, you should carefully consider who in your organization should have a user account, and which role you should assign to the user accounts you create.

**Select from the following user roles:**

* **Administrator**        —The Administrator role allows full management of, and read access for, the account and any managed accounts. Only administrators can create and manage other users for the managing account and for managed accounts. Administrators can also control features for the managing account and all its managed accounts.
Assign this role to your master account, and only to accounts that require a high level of control.
* **Owner**        —The Owner role allows full management and read access for the user account they are assigned, but do not have the ability to edit other user accounts. Owners also have full read and modify permissions to any managed accounts,  including the ability to edit users on the managed accounts. Owner accounts cannot create or delete users in managed accounts. 
Assign this role to delegate daily configuration management activities, excluding user management, on your account and managed accounts.
* **Power User**        —The Power User role allows full access within the managing account, except for user management. Power users can view all the information in their managed accounts, but cannot modify the information (including user accounts). 
Assign this role to delegate configuration management activities for your managing account, but not the management of managed accounts or other users.
* **Support/Care**        —The Support/Care role allows only read access for the managing account and all its managed accounts.
Assign this role to delegate read access to the managing account and its managed accounts for people that need to support and troubleshoot issues for your account and its managed accounts.
* **Read Only**        —The Read Only role allows only read access for the managing account. Users assigned this role cannot make changes and cannot view information for any managed accounts.
Assign this role to delegate  read access to an account, but do not want to delegate any visibility to the managed accounts.

| Role | Administrator | Owner | Power User | Support/Care | Read-Only |
|---|---|---|---|---|---|
| User Management | X |  |  |  |  |
| Modify (own account) | X | X | X |  |  |
| Modify (managed account) | X | X |  |  |  |
| View (own account) | X | X | X | X | X |
| View (managed account) | X | X | X | X |  |

### Work with users

#### Create a user account

Upon provisioning, Alert Logic created a customer account for your organization and a user account with the Administrator role to enable you to create additional user accounts.

**To create a user account:**

1. Click the ![](../Resources/Images/Icons/cdAddPlus.png) icon.
2. Complete the **User Details** fields.
3. Under **Roles**, select the role you want to assign to the user account.
4. Click **Create**.

#### Create a user account as a notification target

You can create a user account that exists only to receive email notification messages. Create this user account if:

* You want to consolidate notifications within a single email account
* You need an audit trail of relevant events
* Multiple members of your organization, who do not need access to the console, need notification email messages

The user account you create as a notification target does not have the ability to log into the Alert Logic console, and therefore does not receive a verification email to set up a password. The email address you use to create the account should exist solely for this purpose and can be a shared email address that multiple people monitor.

To create a Notification Only Target:

1. Click the ![](../Resources/Images/Icons/cdAddPlus.png) icon.
2. Select **Notification Target Only**.
3. Complete only the following required fields:
   * User Email
   * First Name
   * Last Name
5. Click **CREATE**.

#### Modify a user account 

If your user account has the appropriate permissions, you can modify and update the permissions for existing user accounts.

**To modify an existing user account:**

1. Scroll to the user  account you want to modify, and then click **View**.
2. Modify the **User Details** fields.
3. Under **Roles**, select the role you want to assign to the user account.
4. Click **SAVE**.

#### Delete a user account

Account administrators should delete user accounts when they are no longer required. This practice ensures only those in your organization who need to monitor and protect your environment have access, and it aids in user account management.

**To delete a user account:**

1. Scroll to the user  account you want to delete, and then click **View**.
2. Click **Delete**.
3. When the system asks you to confirm, click **YES**.

#### Lock and unlock a user account

Locking a user account allows administrators to revoke a user's access for security reasons, while also retaining access to the data in the account. In addition, an administrator who needs access to data in an account no longer in use could choose to lock the account rather than delete it.

**To lock or unlock a user account:**

1. Scroll to the user  account you want to lock, and then click **View**.
2. Click **LOCK** or **UNLOCK**.
3. When the system asks you to confirm, click **YES**.
