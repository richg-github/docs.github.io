# Configure Microsoft Azure Connection Target (Beta)

A Microsoft Azure connection target securely stores reusable authentication credential information for integrations with Microsoft Azure.

Complete the following steps to  configure a connection target for Microsoft Azure:

1. [Create an app registration in Azure](#CreateanappregistrationinAzure)
2. [Grant permission to perform actions in Azure](#GrantpermissiontoperformactionsinAzure)
3. [Create a client secret in Azure](#CreateaclientsecretinAzure)
4. [Create the Microsoft Azure connection target from the Alert Logic console](#CreatetheMicrosoftAzureconnectiontargetfromtheAlertLogicconsole)
5. [Use the connection target in automated response](#Usetheconnectiontargetinautomatedresponse)

## Create an app registration in Azure

Create an app registration in Azure Active Directory to hold the permissions and credentials granted to Alert Logic.

**To create an app registration:**

1. Log into the [Azure Active Directory console](https://aad.portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Overview).
2. On the left panel of the AzureActive Directory console, under Manage, click **App registrations**.
3. Click **+ New registration**.
4. Enter a name for your connection to Alert Logic automated response. Leave the other items as is.
5. Click **Register**.
6. Copy the Application (client) ID  to a text editor for later.
7. Copy the  Directory (tenant) ID to a text editor for later.

## Grant permission to perform actions in Azure

The next step in the Azure Active Directory console is to grant Alert Logic permissions to perform actions in Azure.

If you grant permission to manage Azure users, you can perform several actions  in automated response, for example:

| Action Type | Name |
|---|---|
| Simple response | Azure Active Directory Disable User |
| Playbook task | [Disable Azure AD User](../../../respond/automated-response/tasks/azure-disable-user.md) |
| Playbook task | [Enable Azure AD User](../../../respond/automated-response/tasks/azure-enable-user.md) |

If you grant permission to access Microsoft Defender for Endpoint, you can perform several actions  in automated response, for example:

| Action Type | Name |
|---|---|
| Simple response | Microsoft Defender ATP Isolate Endpoint |
| Playbook task | Isolate Victim Endpoint |
| Playbook task | Release Endpoint from Isolation |

Complete one or both of the following procedures, depending on your goals for the connection to Azure.

**To grant permission to manage Azure users:**

1. On the left panel of the app registration for your new app, under Manage, click **API permissions**.
2. Click **+ Add a permission**.
3. Select **Microsoft Graph**.
4. On the Request API permissions page, in response to the question about the type of permissions your application requires, click **Application permissions**.
5. In the list of permissions, scroll down and click **User**  to see permissions in this category, and then select **User.ReadWrite.All**.
6. Click **Add permissions**.
7. From the page listing active permissions, click **Grant admin consent to** next to Add a permission.
8. Click **Yes** to confirm.
The status of the User.ReadWrite.All permission becomes "Granted", and a green check mark icon appears next to the granted permission.

**To grant permissions to access Microsoft Defender for Endpoint:**

1. On the left panel of the app registration for your new app, under Manage, click **API permissions**.
2. Click **+ Add a permission**.
3. On the Request API permissions page, select **APIs my organization uses**.
4. In the text box, type "WindowsDefenderATP", and then select **WindowsDefenderATP**.
5. On the Request API permissions page, in response to the question about the type of permissions your application requires, click **Application permissions**.
6. In the list, select the following permissions:
   1. Click **User**  to see permissions in this category, and then select **User.Read.All**.
   2. Click **Machine** to see permissions in this category, and then select **Machine.Isolate**.
8. Click **Add permissions**.
9. From the page listing active permissions, click **Grant admin consent to**, next to Add a permission.
10. Click **Yes** to confirm.
The status of the User.ReadWrite.All permission and Machine.Isolate permission becomes "Granted", and a green check mark icon appears next to the granted permissions.

## Create a client secret in Azure

The last step in the Azure Active Directory console is to create a client secret.

**To create a client secret:**

1. On the left panel of the app registration for your new app, under Manage,  click **Certificates &amp; secrets**.
2. Select **Client secrets** if it is not active.
3. Click **+ New client secret**.
4. Enter a description (example: Alert Logic Automated Response).
5. Select an expiration, and *note the expiration date* for future renewal.
6. Click **Add**.
7. Copy the Value to a text editor for later.

## Create the Microsoft Azure connection target from the Alert Logic console

After you finish the configuration in Azure, the next step is to create the connection target in the Alert Logic console.

**To create a Microsoft Azure connection target**:

1. In the Alert Logic console, click the navigation menu icon (![](../../../Resources/Images/dashboard/menu-icon.png)), click ![](../../../Resources/Images/dashboard/configure-icon.png)**Configure**, and then click **Connectors**.
2. Click the **Connection Targets** tab.
3. On the Connection Targets page, click the add icon (![](../../../Resources/Images/Icons/cdAddPlus.png)), and then click Microsoft Azure.
4. On the Create a Microsoft Azure Connection Target page, type a descriptive name for the connection target —for example, "Microsoft Azure Connection Target".
5. In **Directory (Tenant) ID**, paste the Directory (tenant) ID that you noted in [Create an app registration in Azure](#CreateanappregistrationinAzure).
6. In **Application (Client) ID**, paste the Application (client) ID that you noted in [Create an app registration in Azure](#CreateanappregistrationinAzure).
7. In **Client Secret Value**, paste the Value for the client secret that you noted in [Create a client secret in Azure](#CreateaclientsecretinAzure).
8. Click **SAVE**.

## Use the connection target in automated response

After you save the connection target, you can use it in  an automated response. For more information about automated response, see [Get Started with Automated Response (Beta)](../../../respond/automated-response.md).

## Manage connection targets

You can view the list of connection targets and edit or delete an existing one. For more information, see [Manage Connection Targets](../../../Z-Sandbox/bbaskin/connectors-beta/connection-targets/manage-connection-targets.md).
