# Update your Azure Deployment for CIS Foundation Benchmarks 

Alert Logic requires updates to your Azure deployments to comply with Microsoft Azure Center for Internet Security (CIS) Foundation Benchmarks,  an established best practices  baseline configuration guideline. The update furthers your security measures by allowing Alert Logic to perform CIS benchmark checks on your deployments that expose vulnerabilities.

For more information about Microsoft Azure CIS Benchmarks, see [cisecurity.org/benchmark/azure](https://www.cisecurity.org/benchmark/azure/).

When you configured your Azure deployments, you created an app registration, and then used an Azure role-based access control (RBAC) to create and assign a role to that app registration in your Azure resources. You must update the role document you used to create RBAC, and then update the new path to the role document. You must also grant certain permissions in your Azure resources to access Microsoft Graph and Key vaults. These procedures require administrative permission in the Azure portal.

These instructions do not apply in the following cases:

* You have previously configured RBAC and are using user credentials. For guidance on what you must update if you have user credentials, see [Update your Azure Deployment with User Credentials for CIS Foundation Benchmarks](azure-deployment-update-cis-foundation-benchmarks-user-credentials.md).
* This is your first time configuring an RBAC in your Azure resources. For guidance on how to configure your Azure resources for RBAC, app registration, and CIS benchmark checks, see [Configure App Registration and RBAC for Microsoft Azure Resources](azure-rbac-role-setup.md).

A remediation to update your Azure deployments was listed in your Remediations page in the Alert Logic console.

You  can generate a CIS Foundation Benchmark report for Azure in the Alert Logic console. For more information, see [CIS Microsoft Azure Foundation Benchmark](../analyze/reports/compliance/azure-foundation-benchmark.md).

To update your Azure resources for CIS Benchmark checks, you must:

1. [Update the role document](#Update-the-role-document)
2. [Update your RBAC role document](#Update-your-RBAC-role-document)
3. [Grant permissions to access Microsoft Graph](#Grant-permissions-to-access-Microsoft-Graph)
4. [Grant permissions to access Key vaults](#Grant-permissions-to-access-Key-vaults)

## Update the role document

You must replace the previous JSON file you saved when you first created an RBAC role.

1. Create a new text file and copy the [Alert Logic role](../pdf-files/Azure-RBAC-Role-Benchmark.txt) into it. Note the directory where you save the file. You must know the path and file name for later.
2. Make the following changes to the file:
   1. In the <kbd>"Name": "&amp;lt;Resource Explorer (Alert Logic)&amp;gt;",</kbd> line, change the <kbd>&amp;lt;Resource Explorer (Alert Logic)&amp;gt;</kbd> entry to the name of your app registration.
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
2. Update the following line with the new path. 
Azure Azure CLI 2.0 commands
<kbd>az role definition create --role-definition </kbd>[path to the role document]Azure Azure PowerShell commands
<kbd>New-AzureRmRoleDefinition -InputFile </kbd>[path to the role document]
3. In the Azure portal, under Subscriptions, select your subscription, and then click **Access control (IAM)**.
4. Click **Roles** to verify that the RBAC role you created appears in the portal.                   
If the role does not appear, refresh the list of roles.

## Grant permissions to access Microsoft Graph

You must grant permissions to access Microsoft Graph in the Azure portal, which allows Alert Logic to perform CIS benchmark checks.

**To grant permissions to access Microsoft Graph**:

1. Log in to the [Azure portal](https://portal.azure.com/), and then click **Azure Active Directory**.
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

## Grant permissions to access Key vaults

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
