# Configure Cisco AMP Log Collector 

The Alert Logic Cisco AMP Collector is an AWS-based API Poll (PAWS) log collector library mechanism designed to collect logs from the Cisco AMP service. You can find Cisco AMP logs collected with keyword search in the Alert Logic console [Search: Log Messages](../../analyze/log-message-search.md) page. Alert Logic also generates security incidents from Cisco AMP logs in the [Incidents](../../analyze/incidents.md) page.

The Alert Logic Cisco AMP collector polls [AuditLogs](https://api-docs.amp.cisco.com/api_actions/details?api_action=GET+%2Fv1%2Faudit_logs&amp;api_host=api.amp.cisco.com&amp;api_resource=AuditLog&amp;api_version=v1) and  [Events](https://api-docs.amp.cisco.com/api_actions/details?api_action=GET+%2Fv1%2Fevents&amp;api_host=api.amp.cisco.com&amp;api_resource=Event&amp;api_version=v1) APIs.

You must complete the following to successfully configure your Cisco AMP Log Collector:

1. [Obtain an API Client ID and an API key in Cisco AMP](#Obtain)
2. [Configuring collection from the Alert Logic console](#Configur)

## Obtain an API Client ID and an API key in Cisco AMP

You must create an API, and then obtain the API client ID and API key in the Cisco AMP for Endpoints console.

**To obtain an API client ID and the API key**:

1. Log in to the Cisco AMP for Endpoints console.
2. Click **Accounts**, and then click **API Credentials**.
3. Click **+ New API Credential**.
4. In the New API Credential window, select **Read-only** for the Scope.
5. Click **Create**. Make a note of the API client ID and the API key.

## Configuring collection from the Alert Logic console

After  you obtain the client API ID and API key, you must complete the log collection process in the Alert Logic console. This configuration is an account-level integration, which means you can configure more than one instance of Cisco AMP collection. This capability is  useful when more than one instance of the Cisco AMP application exists in your organization.

To access the Application Registry page, click the menu icon (![](../../Resources/Images/dashboard/menu-icon.png)) from the Dashboards page. Click ![](../../Resources/Images/dashboard/configure-icon.png)**Configure**, and then click **Application Registry**.

**To add a new application collection****:**

1. In the **Applications Registry**, click the **Cisco** tile, and then click  Cisco AMP.
2. In the **Application Name** field, enter a name for this Cisco AMP collection instance.
3. Under Collection Method and Policy, in the **Cisco AMP Domain** field, enter the Cisco AMP domain location.
4. In the **Client ID**, enter the client API ID you noted earlier
5. In the **Secret Key** field, enter the API key you noted earlier.
6. Under **Resource Names**, select from which Cisco AMP resources you want to poll.
7. (Optional) Enter a **Collection Start** time using a format such as (2020-01-01T16:00:00Z). If the **Collection Start** field is left blank, only logs generated after you configure this collection instance will be collected.             
The collection start time determines how far back you want Alert Logic to collect logs if data already exists in your account. Alert Logic can only collect logs up to 30 days prior to the date you configured this collection instance.
8. Click **ADD**. Wait a few minutes for the application to create and appear in your application list. Do not click **ADD** again.

In the Applications List tab, if you configured your application correctly, within approximately 10 minutes you will see Configured next to the application. For more information about how to add instances or manage existing collecting applications, see [Manage your configured applications](../application-registry.md#Configur).

## Security Content for incidents

Alert Logic builds collectors to capture data from various applications with the goal of creating content that generates security incidents for key security use cases in the Alert Logic console. The following security incidents are available for Cisco AMP:

* Administrative Actions
* User Login AD
* User Behavior AD
