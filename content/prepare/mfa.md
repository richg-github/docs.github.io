# Multi-factor Authentication

Multi-factor authentication (MFA) provides additional account security through a required authentication code that you must enter, in addition to your Alert Logic account credentials, when you log into the Alert Logic console. If your account requires MFA, you must set up a device, such as a smart phone or a tablet, to generate the required authentication code to sign into the Alert Logic console. Alert Logic supports time-based one-time password (TOTP) apps, like Google Authenticator, Authy, or 1Password. You can download these apps from the Apple App Store (Apple iOS devices) or Google Play (Android devices).

Add and set up your MFA device when you first log in after:

* An administrator enables MFA.
* You enable MFA for your user account.
* You or an administrator deletes your device.

    Be sure the date and time settings for your phone are configured to set automatically at the time you set up your MFA device and when you log into the Alert Logic console using MFA. Otherwise, your login may not succeed.     ## Enable and disable MFA in the Alert Logic console

Only users with the Administrator role can enable or disable MFA for entire accounts and can remove individual users' MFA devices without deactivating the MFA for the entire account.

To enable or disable MFA for the entire account:

1. In the Alert Logic console menu, click ![](../Resources/Images/dashboard/manage-icon.png)Manage, and then click **Users**.
2. In the MFA status box at the top of the AIMS User Management page, click **EDIT**.
3. In the Edit MFA for the Account slideout panel, click the **Account Requires MFA** toggle to select either **Enabled** or **Disabled**.
4. Click **SAVE**.

If your account administrator did not enable MFA for the entire account, and if you want to use MFA to log in, you can enable and disable MFA for only your account.

To enable or disable MFA for only your user account:

1. In the Alert Logic console menu, click ![](../Resources/Images/dashboard/manage-icon.png)Manage, and then click **Users**.
2. In the list of users, select your user information.
3. In the account information slideout panel, click **MFA**, and then click **ADD DEVICE**.
4. Follow the instructions that appear on the screen.
5. Click **VERIFY SETUP**.
6. Click **CONTINUE**.
7. Log into the Alert Logic console, and use the authentication code sent to your MFA device.

## Set up a new MFA device

If your account administrator enabled MFA since your last login, or if you or your administrator removed your MFA device since your last login, you must set up a new MFA device when you log in.

To set up an MFA device:

1. Access the Alert Logic console login screen.
2. Follow the instructions that appear on the screen.
3. Click **VERIFY SETUP**.
4. Click **CONTINUE**.
5. Log into the Alert Logic console, and use the authentication code sent to your MFA device.

## Remove an MFA device

If you no longer have access to the MFA device you set up, you or your account administrator can remove the MFA device attached to your user account.

If you or your account administrator removed your MFA device, you must set up a new MFA device before you can log into the Alert Logic console.

To remove an MFA device:

1. In the Alert Logic console menu, click ![](../Resources/Images/dashboard/manage-icon.png)Manage, and then click **Users**.
2. Find the user account you want to edit, and then click **VIEW**.
3. In the account information slideout panel, click **MFA**, and then click **REMOVE DEVICE**.
4. Click **SAVE**.
