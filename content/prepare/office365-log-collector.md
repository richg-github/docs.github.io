# Set Up Collection of Microsoft Office 365 Logs

The instructions in this document are for an older setup of the Microsoft Office 365 log collector. If this is your first time setting up Microsoft Office 365 collectors,   see [Configure Microsoft Office 365 Log Collector](../configure/collectors/o365.md). If you previously installed the older version of Office 365 and want to update using the Alert Logic console, see [Set Up Collection of Microsoft Office 365 Logs](#Update).

Alert Logic supports Microsoft Office 365 log collection. To collect Office 365 logs, you must first create and set up an Alert Logic application in Microsoft Azure.

## Before you begin

To perform the setup required to grant Alert Logic permission to collect Office 365 logs, you must have access to the following:

* A Microsoft Office 365 account with administrative privileges
* A Microsoft Azure account with administrative privileges
* An Alert Logic account with administrative privileges

You cannot complete this procedure without administrative privileges in all three accounts.

## Register a new Office 365 web application

In the Office 365 portal, you must register a new Office 365 web application to collect Office 365 logs.

**To register an Office 365 web application: **

1. Log into the Office 365 portal as an Active Directory tenant administrator.
2. Click **Show all** to expand the left navigation area, and then  click **Azure Active Directory**.
3. Select **App Registrations**, and then click **+ New application registration**.
4. Provide the following information in the fields:
   * Name - for example, alo365collector.
   * Select **Single tenant** for supported account types.
   * Leave the Redirect URI blank.
6. Click **Register**. Note the Application (client) ID, for example, a261478c-84fb-42f9-84c2-de050a4babe3.

## Set up Active Directory security permissions

You must set up Active Directory security permissions for the application you created so it can read threat intelligence data and activity reports for your organization.

**To set up Active Directory permissions:**

1. On the main panel under the new application, click **API Permissions**, and then click **+ Add a permission**.
2. Locate and click **Office 365 Management APIs**.
3. In **Application permissions**, expand and select **ActivityFeed.Read**and **ServiceHealth.Read**.
4. Ensure all necessary permissions are selected, and then click **Add permissions**.
5. Click **Grant admin consent**, and then click **Accept** to confirm.
      Only the Active Directory tenant administrator can grant permissions to an Azure Active Directory application.      7. On the left navigation area, select **Certificates &amp; secrets**, and then click **+ New client secret**.
8. Type a key **Description** and set the duration to **Never**.
9. Click **Add**.
10. Save the key value, which you need during ARM template deployment.
11. Click **Overview** to return to the application summary, and then click the link under **Managed application in local directory**.
12. Click **Properties**, and then note the Object ID associated with the application.
      This Object ID not the same Object ID found under the Registered app view or under Settings.     
## Create an Alert Logic access key

You must generate an access key that allows the application you created to connect to the Alert Logic back end. You can do this from the Alert Logic console.

Access keys contain the two components you need to configure access to the Alert Logic back end—the access key ID and a secret key. You need both values to configure a log source.

Access key components:

* Access key ID—Numerical identification for the access key you generated. You can retrieve this value from the Alert Logic console.
* Secret key—Encrypted account information that provides permission for data to flow from AWS to the Alert Logic back end. You cannot retrieve this value after you initially generate the access key. If you lose your secret key, you must generate a new access key.

After you generate a new access key, the Alert Logic console allows you to retrieve only the access key ID. You must store both the access key ID and the secret access key immediately after you generate the access key. You can choose to copy and paste the access key ID and the secret key to a file, or you can automatically save your access key information to a .CSV file that you can save to a secure location.

    If you lose your access key ID or your secret key, you can no longer use the access key to configure new integrations and must generate a new access key.     
To generate and store an access key:

1. In the Alert Logic console, click the Settings icon (![](../Resources/Images/supportThreeDots.png)), and then select **Users**.
2. Scroll to the user account you want to modify, and then click **VIEW**.
3. In the account information slideout panel, click the **Access Keys** tab.
4. In the **Access Keys** tab, click **GENERATE NEW KEY**.
5. From the Access Key Created window, click **DOWNLOAD KEY FILE**.

To learn how to manage access keys, see [Create and Manage Alert Logic Access Keys ](access-key-management.md).

## Download and deploy the Azure Resource Manager (ARM) template

Before you can configure Office 365 log collection, you must log into Microsoft Azure and download and deploy an ARM template. You can use either the Microsoft Azure portal or a command line to deploy the template.

The steps in this section require an active Azure subscription. To verify your Azure subscription, visit Azure subscriptions blade.

If your organization uses multiple Active Directory tenants, log into the same tenant used to [Register a new Office 365 web application](#Register). To find your Office 365 tenant ID, see [Find your Office 365 tenant ID](https://support.office.com/en-gb/article/find-your-office-365-tenant-id-6891b561-a52d-4ade-9f39-b492285e2c9b).

### Deploy with the custom ARM template through the Azure portal

**To access and deploy the ARM template through the Azure portal, click [this link](https://portal.azure.com/#create/Microsoft.Template/uri/https:%2F%2Fraw.githubusercontent.com%2Falertlogic%2Fazure-collector%2Fmaster%2Ftemplate.json), and then:**

1. Provide the following required template parameters:
   * **App Client ID:** The GUID of your application that created the subscription. You can obtain it from **Azure** > **AD** > **App registrations** > **Your app name** > **Application (client) ID**.
   * **App Client Secret:** The secret key of your application from **App Registrations** > **Certificates &amp; Secrets**.
   * **Name:** The name of the log source to appear in the Alert Logic console. This must be unique to any previous deployment of a Function App.
   * **Resource Group:** Create a new resource group for the collector. This must be unique to any previous resource group name.
   * **Storage Name:** Any storage account name that does not currently exist. This must be unique to any previous storage account name.
   * **Alert Logic Access Key ID:** The <kbd>access_key_id</kbd> you created above.
   * **Alert Logic Secret Key:** The <kbd>secret_key</kbd> you created above.
   * **Alert Logic API endpoint:** Leave the default value (api.global-services.global.alertlogic.com).
   * **Alert Logic Data Residency:** Leave the default value.
   * **Office 365 Content Streams:** The log types you want to collect. Valid values are:
      * ["Audit.AzureActiveDirectory","Audit.Exchange","Audit.SharePoint","Audit.General"]
   * **Service Principal ID:** The <kbd>Object ID</kbd> of the application that created the subscription.You can obtain this value from **Azure** > **AD** > **App registrations** > **Your app name** > **Link under Managed application in local directory** > **Properties** > **Object ID**.
4. Click **Purchase**.

### Deploy through the Azure CLI

If you want to deploy through the Azure command line, you can use either [Azure Cloud Shell](https://docs.microsoft.com/en-gb/azure/cloud-shell/quickstart#start-cloud-shell) or a local installation of [Azure CLI](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli?view=azure-cli-latest).

**To deploy through the **Azure** command line:**1. In the command line, type the following to create a new resource group. (The example below creates a new resource group in the "Central US" location.)
<kbd>az group create --name &amp;lt;new-resource-group-name&amp;gt; --location "Central US"</kbd>
2. In the Azure portal, access the **Resource groups** blade, and then select the resource group you created.
3. Select **Access Control (IAM)**, and add the **Website Contributor** role to the Active Directory application identity you created above.
4. In the command line, type the following command to deploy a template, and enter the required parameters when prompted.
<kbd>az group deployment create \
    --resource-group &amp;lt;new-resource-group-name&amp;gt; \
    --template-uri "https://raw.githubusercontent.com/alertlogic/azure-collector/master/template.json"</kbd>

### Verify the installation

As a best practice, you should verify the template installed successfully.

**To verify successful installation of the template:**

1. In the Azure portal, access **Function Apps**, and then choose the Alert Logic Office 365 collector function.
2. Click **Functions** > **Master** > **Monitor**, and verify the recent log entry has the status of **OK** and contains no error messages.
3. In the Alert Logic console, browse to **Deployments** > **All Deployments** > **Log Sources**, and then filter the list by **Push (Office 365, CloudWatch)** collection method.
4. Verify a new Office 365 log source with the name provided during <kbd>az group deployment create</kbd> appears with the source status of **OK**.

If the collector stops sending information to Alert Logic, the **Current Status** for the source displays  the error, "Collector is offline." If you see this error, try one of the following troubleshooting methods:

* If you either deleted the collector application, or disabled it from the Azure portal, the Alert Logic console may not have removed it. To correct the issue, delete the collector source from the Alert Logic console.
* Occasionally the collector has an issue with the Azure Active Directory, which causes an error. Alert Logic monitors these errors and resolves them, but you may also restart the function app from the Azure portal.

For information about how Azure functions use the Application and Office 365 tenant ID as a <kbd>PublisherIdentifier</kbd> during Office 365 management API requests,  see [How the Office 365 Collector Works](https://github.com/alertlogic/azure-collector/blob/master/README.md#how-the-office-365-collector-works).
