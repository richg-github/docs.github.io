# Configure Okta Log Collector 

The Alert Logic Okta Collector is an AWS-based API Poll (PAWS) log collector library mechanism designed to collect logs from the Okta platform. You can find Okta logs collected with keyword search in the Alert Logic console [Search: Log Messages](../../analyze/log-message-search.md) page. Alert Logic also generates security incidents from Okta logs in the [Incidents](../../analyze/incidents.md) page. For more information about authentication application security content, see [Authentication Application Security Incidents](../../analyze/security-incidents.md).

The Alert Logic Okta collector can collect the following log data relevant to:

* Event log information
* User information
* Group and Group Membership Information
* Application and Application Assignment information

You must complete the following to successfully configure your Okta Log Collector:

1. [Obtain API key from Okta](#Setup)
2. [Configuring collection from the Alert Logic console](#Configur)

## Obtain API key from Okta

You must identify the appropriate Okta domain endpoint from where you want to collect. In the Okta management console, you have to obtain the security API key. The default value  is [https://dev-123.oktapreview.com](https://dev-123.oktapreview.com/).

## Configuring collection from the Alert Logic console

After  you determine the Okta domain location and obtain the API key, you must complete the log collection process in the Alert Logic console. This configuration is an account-level integration, which means you can configure more than one instance of Okta collection. This capability is  useful when more than one instance of the Okta application exists in your organization.

To access the Application Registry page, click the menu icon (![](../../Resources/Images/dashboard/menu-icon.png)) from the Dashboards page. Click ![](../../Resources/Images/dashboard/configure-icon.png)**Configure**, and then click **Application Registry**.

**To add a new application collection**:

1. In the Application Registry, click the Okta tile.
2. In the **Application Name** field, enter a name for this Okta collection instance.
3. Under Collection Method and Policy, in the ** Okta Domain** field, enter the Okta domain location.
4. In the **API Key** field, enter the API Key you noted earlier.
5. (Optional) Enter a **Collection Start** time using a format such as (2020-01-01T16:00:00Z). If the **Collection Start** field is left blank, only logs generated after you configure this collection instance will be collected.             
The collection start time determines how far back you want Alert Logic to collect logs if data already exists in your account. Alert Logic can only collect logs up to 30 days prior to the date you configured this collection instance.
6. Click **ADD**. Wait a few minutes for the application to create and appear in your application list. Do not click **ADD** again.

In the Applications List tab, if you configured your application correctly, within approximately 10 minutes you will Configured next to the application. For more information about how to add instances or manage existing collecting applications, see [Manage your configured applications](../application-registry.md#Configur).

## Security Content for incidents

Alert Logic builds collectors to capture data from Okta and various other applications to create security content that is used to generate incidents for key security use cases. The following security incidents are available for Okta:

* Administrative Actions
* User Login AD
* User Behavior AD

For more information about authentication application security content, see [Authentication Application Security Incidents](../../analyze/security-incidents.md).
