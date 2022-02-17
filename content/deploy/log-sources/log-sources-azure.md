# Configure Log Sources for Microsoft Azure

Alert Logic supports the following log source types for Azure:

* **[Azure Activity logs](#azureActivityLogs)**—Logs that provide insight into the operations performed on resources in your subscription
* **[Azure App Service web server logs](#azureAppServiceWebLogs)**—Logs that provide detailed error information for HTTP failure status codes, failed requests, or HTTP transactions using the W3C extended log file format
* [Set up collection of Microsoft Office 365 Logs](../../prepare/office365-log-collector.md)—Activity logs that provide information including administrative, user, and policy actions
* **[Azure SQL auditing logs](#azureSQLLogs)**—Logs that provide information on database events
* [Alert Logic Log Collector for Microsoft Azure Event Hubs](../../prepare/azure-event-hubs-log-collector.md)—Logs collected by Azure Event Hubs, which streams Azure Active Directory logs, Diagnostic Activity logs, Security Center logs, and SQL Audit logs to Alert Logic

For more information about other log source types, see [Configure Log Sources for All Deployments](log-sources-all-deployments.md) or [Configure Log Sources for Amazon Web Services (AWS)](log-sources-aws.md).

After you provision and install the Alert Logic agent on your target host, the agent automatically creates an associated log source in the Alert Logic console and configures it with the default collection configuration policy for that log source type. You must create and configure new collection sources with existing collection policies to meet more specific requirements. For more information about Log Management policies, see [Log Management Policies](../../configure/log-management-policies.md).

## Create and maintain Azure Activity log sources

**To create an Azure Activity log source:**

1. From the Deployments page, click the  deployment for which you want to create an Activity log collection source.
2. Click **CONFIGURE LOG SOURCES**.
3. Click the **add** icon (![](../../Resources/Images/Icons/cdAddPlus.png)).
4. From **Source Log Type**, select **Azure Activity Logs**.
5. In the **Source Name** field, type a descriptive name.
6. Select **Enable Collection**.
7. Select one of the following:
If you select **Create new Audit Account**, verify the account has the proper permissions to allow Alert Logic to read the Azure Activity events.
To properly set up a role with the minimum permissions required, you must create a custom role in Azure. For more information, read [Create custom roles for Azure Role-Based Access Control](https://azure.microsoft.com/en-us/documentation/articles/role-based-access-control-custom-roles/).
The role below provides a minimum set of permissions required for Activity Log collection:{ 
     "Name":  "<name of your role>",
     "Id": "<auto-assigned>",
     "IsCustom":  true,
     "Description":  "<description of the role>",
     "Actions":       [
                          "Microsoft.Authorization/*/read",
                          "Microsoft.Insights/eventtypes/*/read"
                      ],
     "NotActions":    [

                      ],
     "AssignableScopes":   [
                               "/subscriptions/<add your Subscription ID>"
                           ]
}
   * To use an existing audit account, select **Use an existing Audit Account** and select the Azure account you want to use.
   * To create a new audit account, select **Create new Audit Account** and select the settings you want. Azure will ask you to create a new user name and password.
9. In **Collection Alerts**, select one or more alert options.
10. In **Subscription ID**, type your Azure Subscription ID.
11. In **Resource Group Filter**, type a Resource Group name.
12. In the **Tags** field, type an easily filtered tag.
13. Click **SAVE**.

**To update **Azure** Activity logs sources:**

1. From the Deployments page, click the  deployment for which you want to update the log source.
2. Click **CONFIGURE LOG SOURCES**.
3. Place your cursor over the desired collection source  and click the pencil icon (![](../../Resources/Images/pencil icon.png)).
4. Make the necessary updates.
5. Click **SAVE**.

## Create and maintain Azure App Service web server logs

**To create an Azure App Service web server logs source:**

1. From the Deployments page, click the  deployment for which you want to create an Azure App service web server collection source.
2. Click **CONFIGURE LOG SOURCES**.
3. Click the **add** icon (![](../../Resources/Images/Icons/cdAddPlus.png)).
4. From **Source Log Type**, select **App Service Web Server Logging**.
5. In the **Source Name** field, type a descriptive name.
6. Select **Enable Collection**.
7. Select one of the following:
In the [Azure Portal](https://portal.azure.com/), browse to the storage account in which you store your logs, click **Settings**, and then click **Access keys** to view, copy, and regenerate your account access keys.
   * To use an existing storage account, select **Use an existing Storage Account** and select the storage account you want to use.
   * To create a new storage account, select **Create new Storage Account** and select the settings you want. Azure will ask you to create a new user name and password.
9. In **Collection Alerts**, click the field and select one or more alert options.
10. In **App Service Name**, type the name of your App Service Web application.
11. In **Storage Blob Container**, type the storage account container name where your web server logging is located.
12. In the **Tags** field, type an easily filtered tag.
13. Click **SAVE**.

**To update an Azure App Service web server logs source:**

1. From the Deployments page, click the  deployment for which you want to update the log source.
2. Click **CONFIGURE LOG SOURCES**.
3. Place your cursor over the desired collection source  and click the pencil icon (![](../../Resources/Images/pencil icon.png)).
4. Make the necessary updates.
5. Click **SAVE**.

## Azure SQL auditing logs

Though this feature appears to all users, only those with an Azure account can utilize it.

**To create an Azure SQL database auditing logs collection source:**

1. From the Deployments page, click the  deployment for which you want to create an Azure SQL auditing log collection source.
2. Click **Scope of Protection**
3. Click **CONFIGURE LOG SOURCES**.
4. Click the **add** icon (![](../../Resources/Images/Icons/cdAddPlus.png)).
5. From **Source Log Type**, select **Azure SQL Auditing**.
6. In the **Source Name** field, type a descriptive name.
7. Select **Enable Collection**.
8. Select one of the following:
In the [Azure Portal](https://portal.azure.com/), browse to your storage account where your logs are stored, click **Settings**, and then **click Access keys** to view, copy, and regenerate your account access keys.
   * To use an existing storage account, select **Existing Storage Account** and select the storage account you want to use.
   * To create a new storage account, select **Add new Storage Account** and select the settings you want. Azure prompts you to provide your **Credential Name**, **Storage Account Name**, and **Access Key**.
10. In **Collection Alerts**, select one or more alert options.
11. In the **Azure SQL Table Name**, type your SQL Table Name between **SQLDBAuditLogs** and **YYYYMMDD**.
12. In the **Tags** field, type an easily filtered tag.
13. Click **SAVE**.

**To update an Azure SQL database auditing logs collection source:**

1. From the Deployments page, click the  deployment for which you want to update the log source.
2. Click **CONFIGURE LOG SOURCES**.
3. Place your cursor over the desired collection source  and click the pencil icon (![](../../Resources/Images/pencil icon.png)).
4. Make the necessary updates.
5. Click **SAVE**.

## Azure Event Hubs log collection

Microsoft Azure Event Hubs is a data streaming platform and event ingestion service that can receive and process millions of events per second. Alert Logic allows you to configure Event Hubs to collect your Azure logs and forward them to Alert Logic. For more information, see [Alert Logic Log Collector for Microsoft Azure Event Hubs](../../prepare/azure-event-hubs-log-collector.md).

## Additional Tasks

To learn how to perform additional tasks, such as viewing source information, mass editing sources, and archiving and restoring collection sources, see [View log source information](../log-sources.md#viewCollectionSourceInformation).
