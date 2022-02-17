# Configure Salesforce Log Collector

The Alert Logic Salesforce Collector is an AWS-based API Poll (PAWS) log collector library mechanism designed to collect logs from the Salesforce Customer relationship management (CRM) platform. You must complete the following to successfully configure your Salesforce Log Collector:

* [Set up Salesforce ](#Set)
* [Create an Alert Logic access key](#Create)
* [Install the Salesforce collector from the CloudFormation template](#Install)
* [Configuring collection from the Alert Logic console](#Configur)

You can find Salesforce logs collected with keyword search in the Alert Logic console. Alert Logic also generates security incidents from Salesforce logs in the Incidents page. The Alert Logic Salesforce collector polls the following APIs for various types of data:

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

Ensure your digital certificate is generated, which you will need to create the connected app.

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

## Create an Alert Logic access key

You must generate an access key that allows the Salesforce connected app you created to connect to the Alert Logic server. You can do this from the Alert Logic console.

Access keys contain the two components you need to configure access to the Alert Logic back end—the access key ID and a secret key. You need both values to configure a log source.

Access key components:

* Access key ID—Numerical identification for the access key you generated. You can retrieve this value from the Alert Logic console.
* Secret key—Encrypted account information that provides permission for data to flow from AWS to the Alert Logic back end. You cannot retrieve this value after you initially generate the access key. If you lose your secret key, you must generate a new access key.

After you generate a new access key, the Alert Logic console allows you to retrieve only the access key ID. You must store both the access key ID and the secret access key immediately after you generate the access key. You can choose to copy and paste the access key ID and the secret key to a file, or you can automatically save your access key information to a .CSV file that you can save to a secure location.

    If you lose your access key ID or your secret key, you can no longer use the access key to configure new integrations and must generate a new access key.     
To generate and store an access key:

1. In the Alert Logic console, click ![](../Resources/Images/dashboard/manage-icon.png)Manage, and then click **Users**.
2. Scroll to the user account you want to modify, and then click **VIEW**.
3. In the account information slideout panel, click the **Access Keys** tab.
4. In the **Access Keys** tab, click **GENERATE NEW KEY**.
5. From the Access Key Created window, click **DOWNLOAD KEY FILE**.

To learn how to manage access keys, see [Create and Manage Alert Logic Access Keys](../prepare/access-key-management.md).

## Install the Salesforce collector from the CloudFormation template

You must install the Salesforce collector using the Alert Logic CloudFormation template. Download the [Alert Logic custom  CloudFormation template](https://github.com/alertlogic/paws-collector/blob/master/collectors/salesforce/cfn/salesforce-collector.template). You must have administrative permissions in AWS and your Alert Logic account.

**To deploy the Salesforce collector from the CloudFormation template:**

1. Log into the [AWS Console](http://aws.amazon.com/), and open the [AWS CloudFormation console](https://console.aws.amazon.com/cloudformation).
2. Click the region in which you want to deploy the CloudFormation template. Currently, Alert Logic only supports US regions us-east-1, us-east-2, us-west-1, and us-west-2.
3. Click **Create Stack**.
4. Under Choose a template section, select **Specify an Amazon S3 template URL**, and then enter the following URL: <kbd>https://s3.amazonaws.com/alertlogic-collectors-us-east-1/cfn/salesforce-collector.template</kbd>
5. Click **Next**.
6. In the **Specify Details** window, provide the following required parameters:
   * **Stack name**—Accept the default, or use any preferred name
   * **AlApiEndpoint**—Use predefined <kbd>api.global-services.global.alertlogic.com</kbd>
   * **AlApplicationId**—Use <kbd>salesforce</kbd> (Alert Logic Application Id for collector logs)
   * **AlDataResidency**—Use <kbd>default</kbd>
   * **AlertlogicAccessKeyId**—<kbd>access_key_id</kbd> returned from AIMS
   * **AlertlogicCustomerId**—(Optional) Alert Logic customer ID which collected data should be reported for. If not, set customer ID is derived from AIMs tokens
   * **AlertlogicSecretKey**— <kbd>secret_key</kbd> returned from AIMS
   * **CollectionStartTs**—xample <kbd>2019-11-21T16:00:00Z</kbd> Timestamp when log collection starts
   * **CollectorId**—default <kbd>none</kbd> Optional. A collector UUID if known.
   * **PackagesBucketPrefix**—Example <kbd>alertlogic-collectors</kbd> S3 bucket name prefix where collector packages are located.
   * **PawsAuthType**—Target API authentication type. Supported types: ssws, oauth2
   * **PawsCollectorTypeName**—use <kbd>salesforce</kbd>
   * **SalesforceClientId**—Salesforce Client ID
   * **SalesforceEndpoint**—Salesforce Endpoint
   * **SalesforceObjectNames**—Define Object name, pass JSON formatted list. Possible values are ["LoginHistory", "EventLogFile","ApiEvent", "LoginEvent","LogoutEvent", "LoginAsEvent"]
   * **SalesforceSecret**—Salesforce Secret
   * **SalesforceUserID**—Salesforce User ID
8. Click **Next**.
9. On the **Options** panel, click **Next**.
10. In the **Review** panel, perform a predeployment check.
11. Select **I acknowledge that AWS CloudFormation might create IAM resources**, and then click **Create**.
12. On the CloudFormation Stacks panel, filter results based on the stack name you created, and then select your stack.

A successful deployment returns a status of <kbd>CREATE_COMPLETE</kbd>.

You must repeat the collector installation procedure for each region in which you want to install the Salesforce collector.    You may install only one collector in each AWS region. If you try to deploy the template multiple times in the same region, you will receive an error.     
Refer to [CloudFormation template readme](https://github.com/alertlogic/paws-collector/blob/master/collectors/salesforce/cfn/README-SALESFORCE.md) for more information and verification instructions.

## Configuring collection from the Alert Logic console

After you decide on the API location and create authentication information in Salesforce.com, you must complete the final steps for collection in the Alert Logic console. This configuration is an account-level integration, which means you can configure more than one instance of Salesforce. This capability is useful when more than one instance of the application exists.

To access the Application Registry page, click the menu icon (![](../Resources/Images/dashboard/menu-icon.png)) from the Dashboards page. Click ![](../Resources/Images/dashboard/configure-icon.png)**Configure**, and then click **Application Registry**.

**To add a new application collection**:

1. On the Applications List tab, use the drop-down menu to select the application type you want to see.
2. In the Salesforce tile, click **GET STARTED**.
3. In the **Application Name** field, enter a name for this Salesforce collection instance.
4. Under Collection Method and Policy, select which callback URL from which you want to poll.
5. In the **Client ID** field, enter your client ID.
6. In the **User ID** field, enter your user ID.
7. In the **Secret Key** field, enter your secret key.
8. Select the objects from which you want to collect.
9. (Optional) Enter a **Collection Start** time using a format such as 2020-01-01T16:00:00Z. This collection time is the timestamp for when collection begins. The timestamp is a useful tool if there is data in the account before collection was configured.
10. Click **ADD**.

In the Applications List tab, if you configured your application correctly, within approximately 10 minutes you will see "Configured" with a check icon. For more information about how to add instances or manage existing collecting applications, see [Manage your configured applications](application-registry.md#Configur).

## Security Content for incidents

49. Alert Logic builds collectors to capture data from various applications, with the goal of creating security content that is used to generate incidents for key security use cases. As of now, the Security Content team is determining which type incidents can be created for the Salesforce  platform. This information will be made available and updated on this page later in 2020.
