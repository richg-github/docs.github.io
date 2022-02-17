# Configure Cisco Duo Log Collector 

The Alert Logic Cisco Duo Collector is an AWS-based API Poll (PAWS) log collector library mechanism designed to collect logs from the Cisco Duo platform. You can find Cisco Duo logs collected with keyword search in the Alert Logic console [Search: Log Messages](../../analyze/log-message-search.md) page. Alert Logic also generates security incidents from Cisco Duo logs in the [Incidents](../../analyze/incidents.md) page. For more information about authentication application security content, see [Authentication Application Security Incidents](../../analyze/security-incidents.md).

The Alert Logic Cisco Duo collector polls the following APIs for various types of data:

* [Authentication](https://duo.com/docs/adminapi#authentication-logs)
* [Administrator](https://duo.com/docs/adminapi#administrator-logs)
* [Telephony](https://duo.com/docs/adminapi#telephony-logs)
* [OfflineEnrollment](https://duo.com/docs/adminapi#offline-enrollment-logs)

You must complete the following to successfully configure your Cisco Duo Log Collector:

1. [Obtain an integration key, secret key, and API hostname from Cisco Duo ](#Obtain)
2. [Configuring collection from the Alert Logic console](#Configur)

## Obtain an integration key, secret key, and API hostname from Cisco Duo 

Create a Duo account to obtain an integration key (client ID), secret key, and API hostname. Only administrators with the Owner role have access to the Admin API. You must contact Duo support after you create an account to set it to the appropriate role.

**To obtain an integration key, secret key, and API hostname****:**

1. Create a [Duo account](https://signup.duo.com/), and then contact Duo support to request Admin API access.
2. After you are granted the appropriate role, sign in to [Duo Admin Panel](https://admin.duosecurity.com/login), and then on the left panel, click **Applications**.
3. Click **Protect an Application**, and then locate the entry for Admin API in the applications list.
4. Click **Protect** to configure the application. Make a note of your integration key (client ID), secret key, and API hostname.
5. In the **Permissions** section, select which permissions you want to grant to the Admin API application.
6. Click **Save Changes**.

## Create an Alert Logic access key

You must generate an access key that allows the Cisco Duo API  to connect to the Alert Logic server. You can do this from the Alert Logic console.

Access keys contain the two components you need to configure access to the Alert Logic back end—the access key ID and a secret key. You need both values to configure a log source.

Access key components:

* Access key ID—Numerical identification for the access key you generated. You can retrieve this value from the Alert Logic console.
* Secret key—Encrypted account information that provides permission for data to flow from AWS to the Alert Logic back end. You cannot retrieve this value after you initially generate the access key. If you lose your secret key, you must generate a new access key.

After you generate a new access key, the Alert Logic console allows you to retrieve only the access key ID. You must store both the access key ID and the secret access key immediately after you generate the access key. You can choose to copy and paste the access key ID and the secret key to a file, or you can automatically save your access key information to a .CSV file that you can save to a secure location.

    If you lose your access key ID or your secret key, you can no longer use the access key to configure new integrations and must generate a new access key.     
To generate and store an access key:

1. In the Alert Logic console, click ![](../../Resources/Images/dashboard/manage-icon.png)Manage, and then click **Users**.
2. Scroll to the user account you want to modify, and then click **VIEW**.
3. In the account information slideout panel, click the **Access Keys** tab.
4. In the **Access Keys** tab, click **GENERATE NEW KEY**.
5. From the Access Key Created window, click **DOWNLOAD KEY FILE**.

To learn how to manage access keys, see [Create and Manage Alert Logic Access Keys ](../../prepare/access-key-management.md).

## Configuring collection from the Alert Logic console

After  you create the API secret key and an API ID, you must complete the log collection process in the Alert Logic console. This configuration is an account-level integration, which means you can configure more than one instance of Cisco Duo collection. This capability is  useful when more than one instance of the Cisco Duo application exists in your organization.

To access the Application Registry page, click the menu icon (![](../../Resources/Images/dashboard/menu-icon.png)) from the Dashboards page. Click ![](../../Resources/Images/dashboard/configure-icon.png)**Configure**, and then click **Application Registry**.

**To add a new application collection**:

1. In the **Applications Registry**, click the **Cisco** tile, and then click  Cisco Duo.
2. In the **Application Name** field, enter a name for this Cisco Duo collection instance.
3. Under Collection Method and Policy, in the **Cisco Duo Domain** field, enter the Cisco Duo domain location.
4. In the **Client ID**, enter the integration key you noted earlier
5. In the **Secret Key** field, enter the API Key you noted earlier.
6. Under **Objective Names**, select from which Cisco Duo resources you want to poll.
7. (Optional) Enter a **Collection Start** time using a format such as (2020-01-01T16:00:00Z). If the **Collection Start** field is left blank, only logs generated after you configure this collection instance will be collected.             
The collection start time determines how far back you want Alert Logic to collect logs if data already exists in your account. Alert Logic can only collect logs up to 30 days prior to the date you configured this collection instance.
8. Click **ADD**. Wait a few minutes for the application to create and appear in your application list. Do not click **ADD** again.

In the Applications List tab, if you configured your application correctly, within approximately 10 minutes you will Configured next to the application. For more information about how to add instances or manage existing collecting applications, see [Manage your configured applications](../application-registry.md#Configur).

## Security Content for incidents

Alert Logic builds collectors to capture data from Cisco Duo and various other applications to create security content that is used to generate incidents for key security use cases. The following security incidents are available for Cisco Duo:

* Administrative Actions
* User Login AD
* User Behavior AD

For more information about authentication application security content, see [Authentication Application Security Incidents](../../analyze/security-incidents.md).
