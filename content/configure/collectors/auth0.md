# Configure Auth0 Log Collector 

The Alert Logic Auth0 Collector is an AWS-based API Poll (PAWS) log collector library mechanism designed to collect logs from the Auth0 Identity and Access Management platform.

You can find Auth0 logs collected with keyword search in the Alert Logic console [Search: Log Messages](../../analyze/log-message-search.md) page. Alert Logic also generates security incidents from Auth0 logs in the [Incidents](../../analyze/incidents.md) page. For more information about authentication application security content, see [Authentication Application Security Incidents](../../analyze/security-incidents.md).

The Alert Logic Auth0 Log Collector collects the following log data relevant to:

* Successful user logins
* Failed user logins, including the reason for the failure
* Token exchanges (success and failure)
* Login warnings
* User deletions
* Connection errors
* User signup events
* Email verification events
* Password changes
* Rate limiting events
* Operational events
* Operational errors

You must complete the following to successfully configure your Auth0 Log Collector:

1. [Set up Auth0 application](#Set)
2. [Configuring collection from the Alert Logic console](#Configur)

## Set up Auth0 application

To grant Alert Logic access to your Auth0 log data,  you must configure an application within your Auth0 tenant with the appropriate permissions and retrieve the credentials of the application in the [Auth0 management console](https://manage.auth0.com/).

**To create the API**:

1. In the  [Auth0 management console](https://manage.auth0.com/), on the left panel , click **Applications**, and then click **Create Application**.
2. In the **Name** field, enter a descriptive name for this API.
3. In the **Choose an Application** pane, select **Machine to Machine Applications**.
4. Click **CREATE**.
5. On the Authorize Machine to Machine Application panel, click the **Select an API** drop-down menu, and select **Auth0 Management API**.
6. Under the scopes pane, select **read:logs** and **read:logs_users**.
7. Click **Authorize**.

After you have created your application, you must locate the Client ID and the Client Secret from the application.

**To obtain the API Secret Key and API ID**

1. On the left panel, click **Applications**.
2. In the Applications page, locate and click your application.
3. Under **Settings**, make a note of the Domain Client ID and Client Secret, which you will need later.

## Configuring collection from the Alert Logic console

After  you identify the Auth0 domain endpoint and obtain the security token, you must complete the log collection process in the Alert Logic console. This configuration is an account-level integration, which means you can configure more than one instance of Auth0 collection. This capability is  useful when more than one instance of the application exists.

To access the Application Registry page, click the menu icon (![](../../Resources/Images/dashboard/menu-icon.png)) from the Dashboards page. Click ![](../../Resources/Images/dashboard/configure-icon.png)**Configure**, and then click **Application Registry**.

**To add a new application collection**:

1. In the Application Registry, click the **Auth0** tile.
2. In the **Application Name** field, enter a name for this Auth0 collection instance.
3. Under Collection Method and Policy, in the **Auth0 Domain** field, enter the Auth0 domain you previously noted.
4. In the **Auth0 Client ID** field, enter the client ID you noted earlier.
5. In the **Auth0 Client Secret** field, enter the token you noted earlier.
6. (Optional) Enter a **Collection Start** time using a format such as (2020-01-01T16:00:00Z). If the **Collection Start** field is left blank, only logs generated after you configure this collection instance will be collected.             
The collection start time determines how far back you want Alert Logic to collect logs if data already exists in your account. Alert Logic can only collect logs up to 30 days prior to the date you configured this collection instance.
7. Click **ADD**.Wait a few minutes for the application to create and appear in your application list. Do not click **ADD** again.

In the Applications List tab, if you configured your application correctly, within approximately 10 minutes you will see Configured next to the application. For more information about how to add instances or manage existing collecting applications, see [Manage your configured applications](../application-registry.md#Configur).

## Security Content for incidents

Alert Logic builds collectors to capture data from Auth0 and various other applications to create security content that is used to generate incidents for key security use cases. The following security incidents are available for Auth0 Identity and Access Management:

* Administrative Actions
* User Login AD
* User Behavior AD

For more information about authentication application security content, see [Authentication Application Security Incidents](../../analyze/security-incidents.md).
