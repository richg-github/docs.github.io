# Configure Salesforce Log Collector

The Alert Logic Salesforce Collector is an AWS-based API Poll (PAWS) log collector library mechanism designed to collect logs from the Salesforce Customer relationship management (CRM) platform.

You can find Salesforce logs collected with keyword search in the Alert Logic console [Search: Log Messages](../../analyze/log-message-search.md) page. Alert Logic also generates security incidents from Salesforce logs in the [Incidents](../../analyze/incidents.md) page. For more information about authentication application security content, see [Authentication Application Security Incidents](../../analyze/security-incidents.md).

The Alert Logic Salesforce collector polls the following APIs for various types of data:

* [LoginHistory](https://developer.salesforce.com/docs/atlas.en-us.api.meta/api/sforce_api_objects_loginhistory.htm)
* [EventLogFile](https://developer.salesforce.com/docs/atlas.en-us.api.meta/api/sforce_api_objects_eventlogfile.htm)
* [LoginEvent](https://developer.salesforce.com/docs/atlas.en-us.224.0.platform_events.meta/platform_events/sforce_api_objects_loginevent.htm)
* [LoginGeo](https://developer.salesforce.com/docs/atlas.en-us.api.meta/api/sforce_api_objects_logingeo.htm)
* [User](https://developer.salesforce.com/docs/atlas.en-us.object_reference.meta/object_reference/sforce_api_objects_user.htm)
* [ApiEvent](https://developer.salesforce.com/docs/atlas.en-us.platform_events.meta/platform_events/sforce_api_objects_apievent.htm)
* [LogoutEvent](https://developer.salesforce.com/docs/atlas.en-us.platform_events.meta/platform_events/sforce_api_objects_logoutevent.htm)
* [LoginAsEvent](https://developer.salesforce.com/docs/atlas.en-us.platform_events.meta/platform_events/sforce_api_objects_loginasevent.htm)
* [API Throttling](https://help.magentrix.com/articles/knowledge/Error-REQUEST_LIMIT_EXCEEDED-1-5-2017)

You must complete the following to successfully configure your Salesforce Log Collector:

1. [Set up Salesforce ](#Set)
2. [Configuring collection from the Alert Logic console](#Configur)

## Set up Salesforce 

Before you begin, ensure you have System Administrator privileges for the Salesforce account, and have a digital certificate generated. You must configure the permission set, create a client app, and then edit the policies and permission sets in the [Salesforce console](http://salesforce.com/).

### Configure a Permission Set in Salesforce

**To configure a permission set**:

1. In the Salesforce console, click the cog icon on the upper-right corner, and then click **Setup**.
2. In Administration, click **Users**, and then click **Permission Sets**.
3. Click the permission set for which you want to grant access.
4. Click **System Permissions**, and select the following:
   * Apex REST Services
   * API Enabled
   * View Event Log Files
   * Manage Users (Required for LoginHistory objects only to view associated geo-data)

### Create a Connected App

You must select the API location (URL callback). You have the option to poll one of two APIs depending on the type of Salesforce account:

* Salesforce account (https://login.salesforce.com)
* Salesforce sandbox account (https://test.salesforce.com)

Ensure your digital certificate is generated, which you will need to create the connected app. If you need a  digital certificate, you can reference the [Salesforce Create a Private Key and Self-Signed Digital Certificate  guide](https://developer.salesforce.com/docs/atlas.en-us.sfdx_dev.meta/sfdx_dev/sfdx_dev_auth_key_and_cert.htm) to generate your own self-signed certificate.

**To create a Connected App**:

1. From Setup, click **Apps**, and then click **App Manager**.
2. Click **New Connected App**.
3. In the Basic Information section, fill out the required fields:
   1. Enter a name for the connected app.
   2. Enter an API name.
   3. Enter the contact email.
   4. You can fill out the remaining fields in this section, although you are not required.
5. In the API section, select **Enable OAuth Settings**.
6. Select **Enable for Device Flow**, and then in the Callback URL field, enter the callback URL (API location) that Salesforce calls back to Alert Logic during OAuth.
7. Select the **Use Digital Signatures**, and then click **Choose File** to upload the server.crt file that contains your digital certificate.
8. Add **Perform requests on your behalf at any time** and **Access and manage your data** in the selected OAuth scopes.
9. Click **Save**.

### Manage policies

You must edit the policies to allow your approved users as permitted users to the connected app you just created.

**To edit your policies**:

1. Click **Manage**.
2. Click **Edit Policies**.
3. In the OAuth Policies section, select **Admin approved users are pre-authorized for Permitted Users**, and then click **OK**.
4. Click **Save**.

### Manage permission sets

You must manage the permission set to apply the permission set you created earlier.

**To manage permission sets**:

1. Click **Manage Profiles**.
2. Click **Manage Permission Sets**.
3. Select the permission set you created earlier.
4. Click **Save**.

## Configuring collection from the Alert Logic console

After you decide on the API location and create authentication information in Salesforce.com, you must complete the final steps for collection in the Alert Logic console. This configuration is an account-level integration, which means you can configure more than one instance of Salesforce. This capability is useful when more than one instance of the application exists.

To access the Application Registry page, click the menu icon (![](../../Resources/Images/dashboard/menu-icon.png)) from the Dashboards page. Click ![](../../Resources/Images/dashboard/configure-icon.png)**Configure**, and then click **Application Registry**.

**To add a new application collection**:

1. In the Application Registry, click the **Salesforce** tile.
2. In the **Application Name** field, enter a name for this Salesforce collection instance.
3. Under Collection Method and Policy, choose which callback URL from which you want to poll.
4. In the **Client ID** field, enter your client ID.
5. In the **User ID** field, enter your user ID.
6. In the **Secret Key** field, enter the RSA private key associated with the certificate associated with your Connected App you configured earlier.
7. Select the objects from which you want to collect.			
You must enable Salesforce event monitoring on your account to access the following objects: * EventLogFile
* LoginEvent
* LoginGeo
* LogoutEvent
* LoginAsEvent
8. (Optional) Enter a **Collection Start** time using a format such as (2020-01-01T16:00:00Z). If the **Collection Start** field is left blank, only logs generated after you configure this collection instance will be collected.             
The collection start time determines how far back you want Alert Logic to collect logs if data already exists in your account. Alert Logic can only collect logs up to 30 days prior to the date you configured this collection instance.
9. Click **ADD**.Wait a few minutes for the application to create and appear in your application list. Do not click **ADD** again.

In the Applications List tab, if you configured your application correctly, within approximately 10 minutes you will see Configured next to the application. For more information about how to add instances or manage existing collecting applications, see [Manage your configured applications](../application-registry.md#Configur).

## Security Content for incidents

34. Alert Logic builds collectors to capture data from Salesforce and various other applications to create security content that is used to generate incidents for key security use cases. The following security incidents are available for Salesforce:
* Administrative Actions
* User Login AD
* User Behavior AD

For more information about authentication application security content, see [Authentication Application Security Incidents](../../analyze/security-incidents.md).
