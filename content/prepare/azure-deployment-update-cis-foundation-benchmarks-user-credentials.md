# Update your Azure Deployment with User Credentials for CIS Foundation Benchmarks

Alert Logic requires updates to your Azure deployments to comply with Microsoft Azure Center for Internet Security (CIS) Foundation Benchmarks,  an established guideline for  baseline configuration best practices. The update furthers your security measures by allowing Alert Logic to perform CIS benchmark checks on your deployments that expose vulnerabilities.

For more information about Microsoft Azure CIS Benchmarks, see [cisecurity.org/benchmark/azure](https://www.cisecurity.org/benchmark/azure/).

When you configured your existing Azure deployments, you created  an Azure role-based access control (RBAC) with user credentials. To update, you  must create an app registration, which will replace your user credentials, and then use RBAC to assign a role to that app registration. You must also grant certain permissions in your Azure resources to access Microsoft Graph and Key vaults. These procedures require administrative permission in the Azure portal.

These instructions do not apply in the following cases:

* You have previously configured RBAC with an app registration. For guidance on what you must update if you have an app registration, see [Update your Azure Deployment for CIS Foundation Benchmarks ](azure-benchmark-deployment-configuration.md).
* This is your first time configuring an RBAC in your Azure resources. For guidance on how to configure your Azure resources for RBAC, app registration, and CIS benchmark checks, see [Configure App Registration and RBAC for Microsoft Azure Resources](azure-rbac-role-setup.md).

A remediation to update your Azure deployments was listed in your Remediations page in the Alert Logic console.

You  can generate a CIS Foundation Benchmark report for Azure in the Alert Logic console. For more information, see [CIS Microsoft Azure Foundation Benchmark](../analyze/reports/compliance/azure-foundation-benchmark.md).

To update your Azure resources for CIS Benchmark checks, you must:

1. [Create an app registration in Azure](#Create-User)
2. [Update the role document](#Update-the-role-document)
3. [Update your RBAC role document](#Update-your-RBAC-role-document)
4. [Grant permissions to access Microsoft Graph](#Grant-permissions-to-access-Microsoft-Graph)
5. [Grant permissions to access key vaults](#Grant-permissions-to-access-Key-vaults)
6. [Assign the role to the app registration](#Assign-Role)
7. [Update your deployment in the Alert Logic console](#Update-deployment)

## Create an app registration in Azure

Create an app registration in the Azure portal. You will assign an RBAC role to this app registration.

**To create an app registration**:

1. Log into the [Azure portal](https://portal.azure.com/).
2. In the left menu, click **Azure Active Directory**.
3. On the left panel, under Manage, click **App registrations**.
4. Click **New registration**, and enter a name.
5. Click **Register**.Note the Application (client) ID, and the Directory (tenant) ID, which you will need later.
6. On the left panel, under Manage, click **Certificates &amp; secrets**, and then click **+ New client secret**.
7. Enter a description, and then on Expire, select **Never**.
8. Click **Add**. Note the Value, which you will need later.

## Update the role document

You must replace the previous JSON file you saved when you first created an RBAC role.

1. Create a new text file and copy the [Alert Logic role](../pdf-files/Azure-RBAC-Role-Benchmark.txt) into it. Note the directory where you save the file. You must know the path and file name for later.
2. Make the following changes to the file:
   1. In the <kbd>"Name": "&amp;lt;Resource Explorer (Alert Logic&amp;gt;",</kbd> line, change the <kbd>&amp;lt;Resource Explorer (Alert Logic)&amp;gt;</kbd> entry to the name of your app registration.
   2. In the <kbd>"/subscriptions/&amp;lt;subscription id&amp;gt;"</kbd> line, change the <kbd>&amp;lt;subscription id&amp;gt;</kbd> value to the subscription ID found in the Azure portal, on the Subscriptions blade.
4. Save the text file as a JSON file.

## Update your RBAC role document

You must update the custom RBAC role with the new path to the role document.

1. Open either Azure CLI 2.0 or Azure PowerShell, log in to your Azure account, and then specify the default subscription. 
Azure Azure CLI 2.0 commands
<kbd>az login</kbd>
<kbd>az account set --subscription </kbd><your subscription id>Azure Azure PowerShell commands
<kbd>Login-AzureRmAccount</kbd>
<kbd>Get-AzureRmSubscription –SubscriptionName </kbd>[your subscription name]<kbd> | Select-AzureRmSubscription</kbd>
2. Update the following line with the with the new path. 
Azure Azure CLI 2.0 commands
<kbd>az role definition create --role-definition </kbd>[path to the role document]Azure Azure PowerShell commands
<kbd>New-AzureRmRoleDefinition -InputFile </kbd>[path to the role document]
3. In the Azure portal, under Subscriptions, select your subscription, and then click **Access control (IAM)**.
4. Click **Roles** to verify that the RBAC role you created appears in the portal.                   
If the role does not appear, refresh the list of roles.

## Grant permissions to access Microsoft Graph

You must grant permissions to access Microsoft Graph in the Azure portal, which allows Alert Logic to perform CIS benchmark checks.

**To grant permissions to access Microsoft Graph**:

1. Log into the [Azure portal](https://portal.azure.com/), and then click **Azure Active Directory**.
2. On the left panel, click **App registrations**, and then select your app registration.
3. On the left panel, click **API permissions**, and then click **+ Add a permission**.
4. On the Request API permissions blade, click **Microsoft Graph**.
5. Click **Application permissions**, and then in the list, select the following permissions:
   1. Click **Application** to see permissions in this category, and then select **Application.Read.All**.
   2. Click **Group** to see permissions in this category, and then select **Group.Read.All**.
   3. Click **RoleManagement** to see permissions in this category, and then select **RoleManagement.Read.Directory**.
   4. Click **User**  to see permissions in this category, and then select **User.Read.All**.
7. Click **Add permissions**, and then on the API permissions pane, click **Grant admin consent**.
8. In  the pop-up window, click **Yes** to allow the changes you made on the permissions.

## Grant permissions to access key vaults

You must grant certain permissions to access your key vaults, which allows Alert Logic to perform CIS benchmark checks. You must repeat these steps for each of your key vaults.

**To grant permissions to access your key vault**:

1. In the Azure portal, click **Key vaults**.
2. Select a key vault from the list, and then on the left panel, click **Access policies**.
3. Click **+ Add Access Policy**.
4. In the Key permissions field, select **Get** and **List**.
5. In the Secret permissions field, select **Get** and **List**.
6. Click **Select principal**, and then from the list, select the app registration you created.
7. Click **Add**.                
Repeat these steps for each key vault in the list.

## Assign the role to the app registration

You must assign the role you created to your registered app.

1. In the Azure portal, click **Subscriptions**.
2. In the Subscriptions blade, select the subscription you want Alert Logic to protect, and then click **Access Control (IAM)**. Note the subscription ID, which you will need when you create an Azure deployment.
3. Click **+Add**, and then click **Add role assignment**.
4. Select the RBAC role you created.
5. From the list, click the app you registered earlier.
6. Click **SAVE**.

## Update your deployment in the Alert Logic console

In the Alert Logic console, update the required fields:

* Subscription ID
* Active Directory ID
* Application ID
* Key ID
