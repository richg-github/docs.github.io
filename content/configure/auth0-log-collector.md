# Configure Auth0 Log Collector 

The Alert Logic Auth0 Collector is an AWS-based API Poll (PAWS) log collector library mechanism designed to collect logs from the Auth0 Identity and Access Management platform.  You must complete a few tasks in the Auth0 management console, install the Auth0 collector using the Alert Logic CloudFormation template, and then complete the configuration process in the Alert Logic console to collect logs. You can find Auth0 logs collected with keyword search in the Alert Logic console.Alert Logic also generates security incidents from Salesforce logs in the Incidents page.

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

## Set up Auth0

In the [Auth0 management console](https://manage.auth0.com/), you must identify and enter the API location of the appropriate Auth0 Domain endpoint from which to collect logs, define permissions, and then obtain the secret key and client ID.

**To create the API**:

1. In the  Auth0 dashboard, on the left panel , click **APIs**, and then click **Create API**.
2. In the **Name** field, enter a name for this API.
3. In the **Identifier** field, enter an identifier for your API, for example, https://quickstarts/api. Make a note of the location, which you will need later.
4. In the **Signing Algorithm** field, leave it as **RS256**.
5. Click **CREATE**.

You can define allowed permissions from the Permissions tab in the APIs section.  Permissions allow you to define how resources are accessed on behalf of the user with a given access token. For example, you can choose to grant read access to the messages resource if users have the manager access level, and a write access to that resource if they have the administrator access level.

**To define permissions**:

1. In the APIs section, click the **Permissions** tab.
2. In the **Permissions** field, enter a permission (for example **read:messages**).
3. In the **Description** field, enter a short description for that permission.

After you define permissions, you must locate the client ID and the client secret from the application.

**To obtain the API Secret Key and API ID**

1. On the left panel, click **Applications**.
2. In the Applications page, locate and click your application.
3. Make a note of the client ID and client secret, which you will need later.

## Install the Auth0 collector from the CloudFormation template

You must install the Auth0 collector using the Alert Logic CloudFormation template. Download the [Alert Logic custom  CloudFormation template](https://github.com/alertlogic/paws-collector/blob/master/collectors/auth0/cfn/auth0-collector.template). You must have administrative permissions in AWS and your Alert Logic account.

**To deploy the Auth0 collector from the CloudFormation template:**

1. Log into the [AWS Console](http://aws.amazon.com/), and open the [AWS CloudFormation console](https://console.aws.amazon.com/cloudformation).
2. Click the region in which you want to deploy the CloudFormation template. Currently, Alert Logic only supports US regions us-east-1, us-east-2, us-west-1, and us-west-2.
3. Click **Create Stack**.
4. Under Choose a template section, select **Specify an Amazon S3 template URL**, and then enter the following URL: <kbd>https://s3.amazonaws.com/alertlogic-collectors-us-east-1/cfn/auth0-collector.template</kbd>
5. Click **Next**.
6. In the **Specify Details** window, provide the following required parameters:
   * **Stack name**—Accept the default, or use any preferred name
   * **AlApiEndpoint**—Use predefined <kbd>api.global-services.global.alertlogic.com</kbd>
   * **AlApplicationId**—Use <kbd>auth0</kbd> (Alert Logic Application Id for collector logs)
   * **AlDataResidency**—Use <kbd>default</kbd>
   * **AlertlogicAccessKeyId**—<kbd>access_key_id</kbd> returned from AIMS
   * **AlertlogicCustomerId**—(Optional) Alert Logic customer ID which collected data should be reported for. If not, set customer ID is derived from AIMs tokens
   * **AlertlogicSecretKey**— <kbd>secret_key</kbd> returned from AIMS
   * **Auth0ClientId**—Auth0 Client ID
   * **Auth0ClientSecret**—Auth0 Client secret
   * **Auth0Domain**—Auth0 domain
   * **CollectionStartTs**—xample <kbd>2019-11-21T16:00:00Z</kbd> Timestamp when log collection starts
   * **CollectorId**—default <kbd>none</kbd> Optional. A collector UUID if known.
   * **PackagesBucketPrefix**—Example <kbd>alertlogic-collectors</kbd> S3 bucket name prefix where collector packages are located.
8. Click **Next**.
9. On the **Options** panel, click **Next**.
10. In the **Review** panel, perform a predeployment check.
11. Select **I acknowledge that AWS CloudFormation might create IAM resources**, and then click **Create**.
12. On the CloudFormation Stacks panel, filter results based on the stack name you created, and then select your stack.

A successful deployment returns a status of <kbd>CREATE_COMPLETE</kbd>.

    You must repeat the collector installation procedure for each region in which you want to install the Auth0 collector.    You may install only one collector in each AWS region. If you try to deploy the template multiple times in the same region, you will receive an error. 
Refer to [CloudFormation template readme](https://github.com/alertlogic/paws-collector/blob/master/collectors/auth0/cfn/README-AUTH0.md) for more information and verification instructions.

## Configuring collection from the Alert Logic console

After  you identify the Auth0 domain endpoint and obtain the security token, you must complete the log collection process in the Alert Logic console. This configuration is an account-level integration, which means you can configure more than one instance of Auth0 collection. This capability is  useful when more than one instance of the application exists.

To access the Application Registry page, click the menu icon (![](../Resources/Images/dashboard/menu-icon.png)) from the Dashboards page. Click ![](../Resources/Images/dashboard/configure-icon.png)**Configure**, and then click **Application Registry**.

**To add a new application collection**:

1. On the Applications List tab, use the drop-down menu to select the application type you want to see.
2. In the Auth0 tile, click **GET STARTED**.
3. In the **Application Name** field, enter a name for this Auth0 collection instance.
4. Under Collection Method and Policy, in the **Auth0 Domain** field, enter the Auth0 domain location of the Auth0 API identifier that you previously noted from which collect logs.
5. In the **Auth0 Client ID** field, enter the client ID you noted earlier.
6. In the **Auth0 Client Secret** field, enter the token you noted earlier.
7. (Optional) Enter a **Collection Start** time using a format such as (2020-01-01T16:00:00Z). This collection time is the timestamp for when collection begins. The timestamp is a useful tool if data is in the account before collection was configured.
8. Click **ADD**.

In the Applications List tab, if you configured your application correctly, within approximately 10 minutes you will see "Configured" with a check icon. For more information about how to add instances or manage existing collecting applications, see [Manage your configured applications](application-registry.md#Configur).

## Security Content for incidents

Alert Logic builds collectors to capture data from various applications with the goal of creating content that generates security incidents for key security use cases in the Alert Logic console. The following security incidents are available for Auth0 Identity and Access Management:

* Administrative Actions
* User Login AD
* User Behavior AD
