# Configure App Registration and RBAC for Microsoft Azure Resources

For Alert Logic to protect your Azure deployments, you must configure Microsoft Azure resources to allow Alert Logic to monitor your assets. All procedures require administrative permission in the Azure portal.

You  must create an app registration, and then use Azure role-based access control (RBAC) to create and assign a role to that app registration.

To comply with Center for Internet Security (CIS)  benchmarks for Microsoft Azure, an established best practices  baseline configuration guideline, you must grant certain permissions to access Microsoft Graph and Azure Key Vault. With these permissions,  Alert Logic will perform CIS benchmark checks on your deployments to detect vulnerabilities.

For more information about Microsoft Azure CIS Benchmarks, see [cisecurity.org/benchmark/azure](https://www.cisecurity.org/benchmark/azure/).

These instructions do not apply in the following cases:

* If you have previously configured RBAC with an app registration. To learn how to update your Azure resources, see [Update your Azure Deployment for CIS Foundation Benchmarks ](azure-benchmark-deployment-configuration.md).
* If you have previously configured RBAC with user credentials, see [Update your Azure Deployment with User Credentials for CIS Foundation Benchmarks](azure-deployment-update-cis-foundation-benchmarks-user-credentials.md).

A  remediation to update your Azure resources for Microsoft Azure CIS benchmark  requirements will be listed in the Remediations page in the Alert Logic console.

You  can also generate a CIS Foundations Benchmark report for Azure in the Alert Logic console. For more information, see [CIS Microsoft Azure Foundation Benchmark](../analyze/reports/compliance/azure-foundation-benchmark.md)

To create an RBAC, ensure you have one of the following command line interfaces installed before you begin:

* Azure[ PowerShell](https://azure.microsoft.com/en-us/documentation/articles/powershell-install-configure/)
* Azure [Command Line Interface](https://azure.microsoft.com/en-us/documentation/articles/xplat-cli-install/) (CLI) 2.0

    If you have Azure CLI 1.0 installed, Microsoft recommends you upgrade to CLI 2.0 and use the deprecated CLI 1.0 only for support with the Azure Service Management (ASM) model with "classic" resources. For more information, contact Microsoft Azure support.    
To configure your Azure resources, you must:

1. [Create an app registration in Azure](#Create-User)
2. [Create a custom RBAC role](#Create-Role)
3. [Grant permissions to access Microsoft Graph](#Grant-permission-Microsoft-graph)
4. [Grant permissions to access Azure Key Vault](#Grant-permission-key-vaults)
5. [Assign the role to the app registration](#Assign-Role)
6. [Create a deployment in the Alert Logic console](#Create)

## Create an app registration in Azure

Create an app registration in the Azure portal. You will assign an RBAC role to this app registration.

**To create an app registration**:

1. Log into the [Azure portal](https://portal.azure.com/).
2. Click the search bar, and then click **Azure Active Directory**. If necessary, type "Azure Active Directory".
3. On the left panel, under Manage, click **App registrations**.
4. Click **+ New registration**, and enter a name.
5. Click **Register**.Copy the Application (client) ID, and the Directory (tenant) ID to a text editor for later.
6. On the left panel, under Manage, click **Certificates &amp; secrets**, and then click **+ New client secret**.
7. Enter a description, and then on Expire, select **24 Months**.
8. Click **Add**. Copy the Value to a text editor for later.

**To create an app registration**:

1. Log into the [Azure portal](https://portal.azure.com/).
2. In the left menu, click **Azure Active Directory**.
3. On the left panel, under Manage, click **App registrations**.
4. Click **+ New registration**, and enter a name.
5. Click **Register**.Note the Application (client) ID, and the Directory (tenant) ID, which you will need later.
6. On the left panel, under Manage, click **Certificates &amp; secrets**, and then click **+ New client secret**.
7. Enter a description, and then on Expire, select **Never**.
8. Click **Add**. Note the Value, which you will need later.

## Create a custom RBAC role

After you create an app registration, you must assign an RBAC role to that registration to grant Alert Logic permission to monitor your environments. This allows limited and controlled access to your environments.

For more information about Azure RBAC or managing roles with command-line applications, see:

* [Role based access control custom roles](https://azure.microsoft-us/documentation/articles/role-based-access-control-custom-roles)
* [Manage Role-Based Access Control with the Azure command-line interface](https://docs.microsoft.com/en-us/azure/active-directory/role-based-access-control-manage-access-azure-cli)
* [Manage Role-Based Access Control with Azure PowerShell](https://docs.microsoft.com/en-us/azure/active-directory/role-based-access-control-manage-access-powershell)

To create a custom RBAC role, you must first create a role document and then create a custom role in the Azure portal.

To create a custom RBAC role, you must:

* [Create a role document](#create-a-role-doc).
* [Create a custom role in Azure](#create-custom-role).

### Create a custom role 

You can create a custom RBAC role either in the Azure portal or through a command line interface (CLI), but not both.

### Create a custom role in the Azure portal

To create a custom RBAC role, you must first create a role document and then create a custom role in the Azure portal.

1. In the Azure portal, click the search bar and click **Subscriptions**.
2. Select your subscription, and copy the Subscription ID to a text editor for later.
3. Click **Access control (IAM)**.
4. Click **+ Add**, and then click **Add custom role**.
5. Click the **JSON** tab, and then click **Edit**.
6. Delete everything in the window.
7. Copy the text from [this link](https://azure-rbac-benchmark-role.s3.us-east-2.amazonaws.com/Azure-RBAC-Role-Benchmark.json) and paste it into the JSON window.
8. In the <kbd>"/subscriptions/&amp;lt;subscription id&amp;gt;"</kbd> line, change the <kbd>&amp;lt;subscription id&amp;gt;</kbd> value to the subscription ID found on your Azure portal Subscriptions blade. Example: <kbd>"/subscriptions/00xxx000-x-000-0x0x-0000-000xx000000x"</kbd>
9. (Optional) If you have more than one subscription ID, you can make a list of them in this custom role. Example:					
"assignableScopes": [
"/subscriptions/00xxx000-x-000-0x0x-0000-000xx000000x"   "/subscriptions/00xxx000-x-000-0x0x-0000-000xx000000x"   "/subscriptions/00xxx000-x-000-0x0x-0000-000xx000000x"],
10. Click **Save**, click **Review + create**, and then click **Create**.
11. Click **Roles** to verify that the RBAC role you created appears in the portal.

If the role does not appear, refresh the list of roles.

###  Create a custom role  in the CLI

You can create a custom role using a CLI if you do not want to create it in the Azure portal. Ensure you have one of the following  installed before you begin:

* Azure[ PowerShell](https://azure.microsoft.com/en-us/documentation/articles/powershell-install-configure/)
* Azure [Command Line Interface](https://azure.microsoft.com/en-us/documentation/articles/xplat-cli-install/) (CLI) 2.0

    If you have Azure CLI 1.0 installed, Microsoft recommends you upgrade to CLI 2.0 and use the deprecated CLI 1.0 only for support with the Azure Service Management (ASM) model with "classic" resources. For more information, contact Microsoft Azure support.    
You must make changes to the Alert Logic template role document, and then create your role document in your command line interfaces.

To create a custom role in the CLI:1. In the Azure portal, click the search bar and click **Subscriptions**.
2. Select your subscription, and copy the Subscription ID to a text editor for later.
3. Create a new text file and copy the [Alert Logic role](../pdf-files/Azure-RBAC-Role-Benchmark.txt)  into it. Note the directory where you save the file. You must know the path and file name for later in the procedure.
4. Make the following changes to the file:
   1. In the <kbd>"Name": "&amp;lt;Resource Explorer (Alert Logic)&amp;gt;",</kbd> line, change the <kbd>&amp;lt;Resource Explorer (Alert Logic)&amp;gt;</kbd> to a descriptive name.
   2. In the <kbd>"/subscriptions/&amp;lt;subscription id&amp;gt;"</kbd> line, change the <kbd>&amp;lt;subscription id&amp;gt;</kbd> value to the subscription ID found on your Azure portal Subscriptions blade. Example: <kbd>"/subscriptions/00xxx000-x-000-0x0x-0000-000xx000000x"</kbd>
6. Save the text file as a JSON file.
7. Open either Azure CLI 2.0 or Azure PowerShell, and log in to your Azure account, and then specify the default subscription. 
Azure Azure CLI 2.0 commands
<kbd>az login</kbd>
<kbd>az account set --subscription </kbd><your subscription id>Azure Azure PowerShell commands
<kbd>Login-AzureRmAccount</kbd>
<kbd>Get-AzureRmSubscription –SubscriptionName </kbd><your subscription name><kbd> | Select-AzureRmSubscription</kbd>
8. Create your custom role in Azure. 
Azure Azure CLI 2.0 commands
<kbd>az role definition create --role-definition </kbd>[path to the role document]Azure Azure PowerShell commands
<kbd>New-AzureRmRoleDefinition -InputFile </kbd>[path to the to the role document]
9. In the Azure portal, under Subscriptions, select your subscription, and then click **Access control (IAM)**.
10. Click **Roles** to verify that the RBAC role you created appears in the portal.

If the role does not appear, refresh the list of roles.
## Grant permissions to access Microsoft Graph

You must grant permissions to access Microsoft Graph in the Azure portal, which allows Alert Logic to perform CIS benchmark checks.

**To grant permissions to access Microsoft Graph**:

1. In the Azure portal, click **Azure Active Directory**.
2. On the left panel, click **App registrations**, and then select your app registration.
3. On the left panel, click **API permissions**, and then click **+ Add a permission**.
4. On the Request API permissions blade, click **Microsoft Graph**.
5. Click **Application permissions**, and then in the list, select the following permissions:
   1. Click **Application** to see permissions in this category, and then select **Application.Read.All**.
   2. Click **Group** to see permissions in this category, and then select **Group.Read.All**.
   3. Click **RoleManagement** to see permissions in this category, and then select **RoleManagement.Read.Directory**.
   4. Click **User**  to see permissions in this category, and then select **User.Read.All**.
7. Click **Add permissions**, and then on the API permissions pane, click **Grant admin consent for Default Directory**.
8. In  the pop-up window, click **Yes** to allow the changes you made on the permissions.

## Grant permissions to access Azure Key Vault

You must grant certain permissions to access your Azure Key Vault in the Azure portal, which allows Alert Logic to perform CIS benchmark checks. You must repeat these steps for each of your key vaults.

**To grant permissions to access your key vault**:

1. In the Azure portal, click **Key vaults**.
2. Select a key vault from the list, and then on the left panel, click **Access policies**.
3. Click **+ Add Access Policy**.
4. In the Key permissions field, select **Get** and **List**.
5. In the Secret permissions field, select **Get** and **List**.
6. Click **Select principal**, and then from the list, select the app registration you created.
7. Click **Add**.                    
You must repeat these steps for each key vault in the list.

## Assign the role to the app registration

You must assign the role you created to your registered app.

1. In the Azure portal, click **Subscriptions**.
2. In the Subscriptions blade, select the subscription you want Alert Logic to protect, and then click **Access control (IAM)**. Note the subscription ID, which you will need when you create an Azure deployment.
3. Click **+Add**, and then click **Add role assignment**.
4. Select the RBAC role you created.
5. From the list, click the app you registered earlier.
6. Click **SAVE**.

If you have more than one subscription ID, you must repeat these steps to assign a role for each subscription.

## Create a deployment in the Alert Logic console

In the Alert Logic console, fill out the required fields:

* Subscription ID
* Active Directory ID
* Application ID
* Key ID (the 24 month Value you copied earlier)

If you have more than one subscription ID, you must repeat these steps to assign a role for each subscription.

The steps you must take to create a deployment vary based on your subscription level.

For Essentials subscriptions, see [Microsoft Azure Deployment Configuration (Essentials Subscription)](../deploy/azure-essentials.md)

For Professional subscriptions, see [Microsoft Azure Deployment Configuration (Professional Subscription)](../deploy/azure-pro-ent.md).
