# Configure Salesforce Log Collector

The Alert Logic Salesforce Collector is an AWS-based API Poll (PAWS) log collector library mechanism designed to collect logs from the Salesforce Customer relationship management (CRM) platform. You must complete a few tasks in the Salesforce platform, install the Salesforce collector using the Alert Logic CloudFormation template, and then complete the configuration process in the Alert Logic console to collect logs. You can find Salesforce logs collected with keyword search in the Alert Logic console. Alert Logic also generates security incidents from Salesforce logs in the Incidents page.

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

## Set up Salesforce 

Attach JWT to Salesforce

### Configure a Permission Set

**You must generate a digital certificate**:

1. Click the cog icon in the top right of the Salesforce console, then click **Setup**.
2. In Administration, expand **Users** to expand the tab, and then click **Permission Sets**.
3. Click the permission set you want to grant access to
4. Click **System Permissions**, and select the following:
   * Apex REST Services
   * API Enabled
   * View Event Log Files
   * Manage Users (Required for LoginHistory objects only to view associated geo-data)

**To create a****Client App**:

1. Click the cog in the top right, then click **Setup**.
2. In the sidebar, click Apps > click App Manager
3. Click ‘New Connected App’
4. In the Basic Information section, fill in the required fields
5. In the API section, check ‘Enable OAuth Settings’, check ‘Enable for Device Flow’ and enter a call-back URL. ScreenShot
6. Check the ‘Use Digital Signatures’ checkbox and click Choose File and upload the server.crt file that contains your digital certificate.
7. Add ‘Perform requests on your behalf at any time’ and ‘Access and manage your data’ in the selected OAuth scopes
8. Cick ‘Save’ at the bottom
9. Click Manage.
10. Click Edit Policies.
11. In the OAuth Policies section, select Admin approved users are pre-authorized for Permitted Users, and click OK.
12. Click Save.
13. Click Manage Profiles and then click Manage Permission Sets. Select the previously created permission set.

###  CloudFormation Template (CFT)

Refer to [CF template readme](https://github.com/alertlogic/paws-collector/blob/master/collectors/salesforce/cfn/README-SALESFORCE.md) for installation instructions.

You must complete some key items before attempting to configure log collection from Salesforce in the Alert Logic console.

### Determine your API location

You must select the API location. You have the option to poll one of two APIs depending on the type of Salesforce account:

* Salesforce account (https://login.salesforce.com)
* Salesforce sandbox account (https://test.salesforce.com)

These options are present in the Alert Logic console, but you must make a decision prior to configuring integration so you know what to expect and the implications for either choice.

### Salesforce authentication information 

You must create authentication information  for the Alert Logic collector to use for polling the Salesforce API in [salesforce.com](http://salesforce.com/).

**You must have the following**:

1. A Client ID associated with a connected app in your Salesforce account.
2. The connected app must have the OAuth scopes "api" and "refresh token" or "full".
3. A permission set and a profile associated with the following system permissions allowed:
   * Apex REST Services
   * API Enabled
   * View Event Log Files
   * Manage Users (required for LoginHistory objects only to view associated geo-data)
5. The User ID associated with your Salesforce account must have:
   * The default "System Administrator" privileges for the Salesforce account, or
   * The configured permission set and profile associated with the connected app specified in the previous step assigned to the permissions allowed.
   * A Secret Key, which is an RSA private key associated with the connected app certificate

## Configuring collection from the Alert Logic console

After you decide on the API location and create authentication information in Salesforce.com, you must complete the final steps for collection in the Alert Logic console. This configuration is an account-level integration, which means you can configure more than one instance of Salesforce. This capability is useful when more than one instance of the application exists.

To access the Application Registry page, click the menu icon (![](../Resources/Images/dashboard/menu-icon.png)) from the Dashboards page. Click ![](../Resources/Images/dashboard/configure-icon.png)**Configure**, and then click **Application Registry**.

**To add a new application collection**:

1. On the Applications List tab, use the drop-down menu to select the application type you want to see.
2. In the Salesforce tile, click **GET STARTED**.
3. In the **Application Name** field, enter a name for this Salesforce collection instance.
4. Under Collection Method and Policy, select which URL (API location you decided on earlier) from which you want to poll.
5. In the **Client ID** field, enter your client ID.
6. In the **User ID** field, enter your user ID.
7. In the **Secret Key** field, enter your secret key.
8. Select the objects from which you want to collect.
9. (Optional) Enter a **Collection Start** time using a format such as 2020-01-01T16:00:00Z. This collection time is the timestamp for when collection begins. The timestamp is a useful tool if there is data in the account before collection was configured.
10. Click **ADD**.

In the Applications List tab, if you configured your application correctly, within approximately 10 minutes you will see "Configured" with a check icon. For more information about how to add instances or manage existing collecting applications, see [Manage your configured applications](application-registry.md#Configur).

## Security Content for incidents

30. Alert Logic builds collectors to capture data from various applications, with the goal of creating security content that is used to generate incidents for key security use cases. As of now, the Security Content team is determining which type incidents can be created for the Salesforce  platform. This information will be made available and updated on this page later in 2020.
