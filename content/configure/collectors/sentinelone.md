# Configure SentinelOne Log Collector 

The Alert Logic SentinelOne Collector is an AWS-based API Poll (PAWS) log collector library mechanism designed to collect logs from the SentinelOne platform. You can find SentinelOne logs collected with keyword search in the Alert Logic console [Search: Log Messages](../../analyze/log-message-search.md) page. Alert Logic also generates security incidents from SentinelOne logs in the [Incidents](../../analyze/incidents.md) page.

You must complete the following to successfully configure your SentinelOne Log Collector:

1. [Obtain SentinelOne API token](#Set)
2. [Configuring collection from the Alert Logic console](#Configur)

## Obtain SentinelOne API token

In the SentinelOne Cloud console, you must generate an API token.

**To create an API token**:

1. In the  [SentinelOne management console](https://usea1-pax8.sentinelone.net/login), go to Settings, and then click **Users**.
2. Click on the Admin user for which you generate the API token.
3. Click **Generate** next to API Token.                 
If you see Revoke and Regenerate, you already have a token. Revoke removes the token authorization. Regenerate revokes the token and generates a new token.  If you revoke or regenerate it, existing scripts that use that token will not work. Click **Regenerate** to see a message that shows the existing token string and the date that the token expires.
4. Click **Download**, and save the API token.

## Configuring collection from the Alert Logic console

After  you identify the SentinelOne domain endpoint and obtain the security token, you must complete the log collection process in the Alert Logic console. This configuration is an account-level integration, which means you can configure more than one instance of SentinelOne collection. This capability is  useful when more than one instance of the SentinelOne application exists within your organization.

To access the Application Registry page, click the menu icon (![](../../Resources/Images/dashboard/menu-icon.png)) from the Dashboards page. Click ![](../../Resources/Images/dashboard/configure-icon.png)**Configure**, and then click **Application Registry**.

**To add a new application collection**:

1. In the Application Registry, click the **SentinelOne** tile.
2. In the **Application Name** field, enter a name for this SentinelOne collection instance.
3. Under Collection Method and Policy, in the **SentinelOne Domain** field, enter the SentinelOne domain location.
4. In the **SentinelOne API key** field, enter the API token you noted earlier.
5. (Optional) Enter a **Collection Start** time using a format such as (2020-01-01T16:00:00Z). If the **Collection Start** field is left blank, only logs generated after you configure this collection instance will be collected.             
The collection start time determines how far back you want Alert Logic to collect logs if data already exists in your account. Alert Logic can only collect logs up to 30 days prior to the date you configured this collection instance.
6. Click **ADD**.Wait a few minutes for the application to create and appear in your application list. Do not click **ADD** again.

In the Applications List tab, if you configured your application correctly, within approximately 10 minutes you will see Configured next to the application. For more information about how to add instances or manage existing collecting applications, see [Manage your configured applications](../application-registry.md#Configur).

## Security Content for incidents

Alert Logic builds collectors to capture data from various applications with the goal of creating content that generates security incidents for key security use cases in the Alert Logic console. The following security incidents are available for SentinelOne:

* Administrative Actions
* User Login AD
* User Behavior AD
