# Create and Manage Alert Logic Access Keys 

Access keys store credentials that are used to integrate external applications with the Alert Logic API. Access keys must be generated in the Alert Logic console.

**To access this functionality:**

1. In the Alert Logic console menu, click ![](../Resources/Images/dashboard/manage-icon.png)Manage, and then click **Users**.
2. Scroll to the desired user account, and then click **VIEW**.
3. In the account information slideout panel, click the **Access Keys** tab.

From this page, you can generate, download, and manage your access keys. If you are an administrator, you can manage the access keys of others in your customer account or customer accounts you manage.

## Alert Logic access keys

Access keys contain the two components you need to configure access to the Alert Logic back end.

* Access key ID—Numerical identification information for the access key you generated.
* Secret key—Encrypted account token that provides authentication information for the access key. If you lose your secret key, you must generate a new access key.

## Generate an access key

    After you exit the Access Key Created window, you cannot view your secret key in the Alert Logic console. Either save the access key ID and secret key to your files, or click **Download Key File** to download the access key ID and secret key to a CSV file.     
To generate and store an access key:

1. In the **Access Keys** tab, click **GENERATE NEW KEY**.
2. From the Access Key Created window, click **DOWNLOAD KEY FILE**.

## Edit access key information

The Access Keys tab on the user account slideout panel allows you to view and edit access key information. You can view the following information, but you can edit only the access key name:

* Access key name
* Access key ID
* When the key was last accessed
* Who created the key
* Date the key was created

To edit the access key name:

1. In the **Access Key** tab, from the list of access keys, click the access key you want to edit.
2. Click **EDIT**.
3. Type a new name for the access key.
4. Click **SAVE**.

## Delete an access key

Alert Logic allows you to store only five access keys per user. If you have five access keys stored and need to generate another key, you must first delete one of your existing access keys before you create a new access key. For more information on creating and managing users, see [Customer Accounts, User Accounts, and User Roles](users-roles.md).

    Be sure you delete an access key you no longer use. If you delete an access key used for an integration, the account authentication required for the integration will no longer work.     
To delete an access key:

1. In the **Access Keys** tab, from the list of access keys, click the access key you want to delete.
2. Click **DELETE**.
3. To confirm access key deletion, click **DELETE**.

## Manage access keys of others

If your Alert Logic user account has the Administrator role, you can manage the access keys of others in your customer account. Account administrators can select a user account and perform the following access key management procedures for the selected user account:

* Create an access key
* Edit an access key
* Delete an access key
