# Alert Logic Log Collector for Microsoft Azure Event Hubs

Microsoft Azure Event Hubs is a data streaming platform and event ingestion service that can receive and process millions of events per second. Alert Logic allows you to configure Event Hubs to collect your Azure logs and forward them to Alert Logic.

To grant Alert Logic permission to access Event Hubs for log collection, you must have:

* Microsoft Azure account with Active Directory tenant privileges
* Alert Logic user account
* Alert Logic access key

Alert Logic recommends that you create Azure deployments in the Alert Logic console for each Azure subscription you want to use to collect logs from Event Hubs.

## Create an Alert Logic access key

Access keys store your customer information to allow integration of data from your Microsoft Azure account to Alert Logic integrations and APIs. You can create an access key through the Alert Logic console. For more information, see [Create and Manage Alert Logic Access Keys ](access-key-management.md).

## Register a new Azure web application

Any application that you want to use Azure Active Directory (AD) must be registered in an Azure AD tenant. This registration process involves giving Azure AD details about your application, such as the URL where it is located, the URL to send replies after a user is authenticated, and the URL that identifies the app.

To register an Azure web application to collect logs:

1. Log in to the Azure portal.
2. On the left side panel, click Azure** Active Directory**, and then select **App Registrations**.			 Do not select **App Registrations (Preview)**.
3. Click **+ New  application registration**, and then provide the following configuration parameters:
   * **Name**—Type a name for the new application (such as <kbd>alehubcollector</kbd>).
   * Select Single tenant for supported account types.
   * Leave the Redirect URI blank.
5. Click **Register**.
6. On the Registered app panel, under **Managed application in local directory**, click the name of the application you created.
7. On the Properties panel, note the following:
   * Application ID for use as the App Client ID value when you deploy the ARM template
   * Object ID for use as the Principal ID value when you deploy the ARM templateThis Object ID value is not the same as the Object ID value seen on the Registered App page. Use only the Object ID value seen on the Properties page.
9. Close the Properties panel to return to the Registered app panel, which you need to set up AD security permissions.

## Set up the required Active Directory security permissions

Azure requires you to create a client secret that provides the AD security permissions to the Registered app you created, which allows it to collect Azure log data from Event Hubs.

To create a client secret for your registered app:

1. On the Registered app panel, click **Certificates &amp; secrets**.
2. On the main panel, click **+ New client secret**.
3. In the **Description** field, type a key description, and then set Expires to **Never**.
4. Click **Save**.
5. Copy and save the secret key value, which you need to use as the App Client Secret ID when you [Download and deploy the ARM template](#Download).

    You cannot retrieve the key value after you close the Keys blade. If you do not copy and save the key value before you deploy the ARM template, you must create another key.     ## Download and deploy the ARM template

The Azure Resource Manager (ARM) is the Azure API that allows you to use JSON-formatted ARM templates to deploy resources. You can deploy the ARM template configured to create a new Event Hub along with the log collector, or you can deploy the ARM template configured to subscribe the collector to an existing Event Hub.

### Deploy the custom Azure Resource Manager template for a new Event Hub

Alert Logic provides a custom ARM template that you must configure to allow communication between Azure and Alert Logic.

**To deploy the ARM template:**

1. Access the [ARM template page](https://portal.azure.com/#create/Microsoft.Template/uri/https:%2F%2Fraw.githubusercontent.com%2Falertlogic%2Fehub-collector%2Fv1%2Ftemplates%2Fehub.json) in Azure.
2. Provide the following required template parameters:
   * **Application Name**—Type the name of the log source to appear in the Alert Logic console.
   * Alert Logic** Access Key ID**—Type the access key ID generated when you created the Alert Logic access key.
   * **Alert Logic Secret Key**—Type the secret key generated when you created the Alert Logic access key.
   * **Alert Logic API endpoint**—Do not change the default parameter value (<kbd>api.global-services.global.alertlogic.com</kbd>).
   * Alert Logic** Data Residency**—Do not change the default parameter value (<kbd>default</kbd>).
   * **Event Hub Resource Group**—Leave parameter value blank.
   * **Event Hub Connection String**—Leave parameter value blank.
   * **Event Hub Namespace**—Leave parameter value blank.
   * **Event Hub Name**—Do not change the default parameter value (<kbd>insights-operational-logs</kbd>).
   * **Event Hub Consumer Group**—Do not change the default parameter value (<kbd>$Default</kbd>).
   * Event Hub Filter JSON—Type the filter in JSON format (<kbd>{resultType":"Success"}</kbd>). Only messages that contain the specified property are collected. If both filter values are provided then logs are collected based on both the values.
   * Event Hub Filter Regex—Type the filter in REGEX format ( <kbd>/*.Policy or "Policy"</kbd>). Only messages that contain the specified property are collected. If both filter values are provided then logs are collected based on both the values.
4. Select **I agree to the terms and conditions stated above**.
5. Click **Purchase**.

The new Event Hub you created with this ARM template uses the following event hub scaling parameters:

* Maximum throughput units: 20
* Auto-inflate: Enabled
* Partitions: 32
* Data retention period: 7 days

If you want to use other hub scaling parameter values, you can edit the template or contact Alert Logic for assistance.

**To use other hub scaling parameter values:**

1. On the Azure Custom deployment page, click **Edit template**, and then make the appropriate changes to the following lines:
   * <kbd>"newEhubMaxThroughputUnits": xx,</kbd>
   * <kbd>"newEhubPartitionCount": xx,</kbd>
   * <kbd>"newEhubRetentionDays": xx</kbd>
3. Click **Save**.

### Adjust firewall rules in Event Hub

You must configure the firewall configuration for Event Hub to receive messages. To adjust the firewall:

1. In the new Event Hub you created, on the left panel, under Settings, click **Networking**.
2. In the **Firewalls and virtual networks** tab, in the Firewall section, select **Yes** to **Allow trusted Microsoft services to bypass this firewall**.
3. Click **Save**.

### Deploy the custom Azure Resource Manager template for an existing Event Hub

If you want to deploy the ARM template for an Event Hub that you already configured, you must provide additional parameter values when you deploy the Alert Logic custom ARM template.

**To deploy the ARM template:**

1. Access the [ARM template page](https://portal.azure.com/#create/Microsoft.Template/uri/https:%2F%2Fraw.githubusercontent.com%2Falertlogic%2Fehub-collector%2Fv1%2Ftemplates%2Fehub.json) in Azure.
2. Provide the following required template parameters:
   * **Application Name**—Type the name of the log source to appear in the Alert Logic console.
   * Alert Logic** Access Key ID**—Type the access key ID generated when you created the Alert Logic access key.
   * **Alert Logic Secret Key**—Type the secret key generated when you created the Alert Logic access key.
   * **Alert Logic API endpoint**—Do not change the default parameter value (<kbd>api.global-services.global.alertlogic.com</kbd>).
   * Alert Logic** Data Residency**—Do not change the default parameter value (<kbd>default</kbd>).
   * **Event Hub Resource Group**—Type the resource group for the existing Event Hub.
   * **Event Hub Connection String**—Type the connection string for the existing Event Hub.
           For information about using Azure PowerShell and Azure CLI to get the connection string, see the Microsoft document, [Get an Event Hubs connection string](https://docs.microsoft.com/en-us/azure/event-hubs/event-hubs-get-connection-string).       

   * **Event Hub Namespace**—Type the namespace for the existing Event Hub.
   * **Event Hub Name**—Type the name of the existing Event Hub.
   * **Event Hub Consumer Group**—Type the name of the consumer group of the existing Event Hub.                                     If the Event Hub has other consumers, create a separate consumer group for the Alert Logic collector and use that name here. For more information, see the Microsoft document, [Consumer Groups](https://docs.microsoft.com/en-us/azure/event-hubs/event-hubs-features#consumer-groups).
2. Select **I agree to the terms and conditions stated above**.
3. Click **Purchase**.

You ensure the firewall is configured for Event Hub to receive messages. To adjust the firewall, see [Adjust firewall rules in Event Hub](#Adjust).

### Verify the deployment

After you deploy the template, Alert Logic recommends you perform the following steps to verify the template deployed successfully:

1. In the Alert Logic console, select the Azure deployment for the Azure subscription where you deployed this log collector.
2. Click **CONFIGURE LOG SOURCES**, and then filter the list by **Push (Office 365, EventHub)**  collection method.
3. Verify that the new Event Hubs log source with the name you provided during deployment appears with the source status of "OK."

If the Event Hub log source does not appear, you can:

* Wait approximately 30 minutes, and see if the new Event Hub log source appears.
* Remove the Azure resource group that contains the log source, and deploy the ARM template again.
* Contact Alert Logic Technical Support at:
   * US: (877) 484-8383 (Option 1)
   * UK: +44 (0) 203 011 5533 (Option 1)

## Integrate with Azure Event Hubs

The following links contain instructions to help you integrate different Azure services with Event Hubs.

* [Azure Active Directory Logs](https://docs.microsoft.com/en-us/azure/active-directory/reports-monitoring/tutorial-azure-monitor-stream-logs-to-event-hub#stream-logs-to-an-event-hub)
* [Azure Diagnostic Logs](https://docs.microsoft.com/en-us/azure/azure-monitor/platform/diagnostic-logs-stream-event-hubs#stream-diagnostic-logs-using-the-portal)
* [Azure Activity Logs](https://docs.microsoft.com/en-us/azure/azure-monitor/platform/activity-logs-stream-event-hubs#enable-streaming-of-the-activity-log)
* [Azure Security Center Events](https://docs.microsoft.com/en-us/azure/security-center/security-center-partner-integration#exporting-data-to-a-siem)
* [Azure SQL Audit Logs](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-auditing#subheading-2)
