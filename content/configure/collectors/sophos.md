# Configure Sophos Log Collector 

The Alert Logic Sophos Collector is an AWS-based API Poll (PAWS) log collector library mechanism designed to collect logs from the Sophos service. You can find Sophos logs collected with keyword search in the Alert Logic console [Search: Log Messages](../../analyze/log-message-search.md) page. Alert Logic also generates security incidents from Sophos logs in the [Incidents](../../analyze/incidents.md) page.

The steps to configure the Sophos collector depend on which API you want to collect from: Common API or SIEM API.  For instructions on how to configure Sophos to collect logs from the SIEM API, see [Create a Sophos collector for Common API](#Create-SIEM-API). For instructions on how to configure Sophos to collect logs from Common API, see [Create a Sophos collector for Common API](#Create-SIEM-API).

If you want to collect logs from both the Common  API or SIEM API, you must complete each of these instructions separately to create another Sophos log collection instance.

If you previously configured the Sophos collector, you were only able to successfully collect logs from the Common API. You can now configure the Sophos collector to collect from both SIEM API or Common API.

## Create a Sophos collector for Common API

You must complete the following to successfully configure your Sophos Log Collector:

1. [Obtain a Client ID and a secret key in Sophos Central Admin](#Obtain)
2. [Configuring collection from the Alert Logic console](#Configur)

### Obtain a Client ID and a secret key in Sophos Central Admin

You must create a credential, and then obtain the client ID and secret key in the Sophos Central Admin console.

**To obtain an API client ID and the API key**:

1. Log in to the [Sophos Central Admin](https://central.sophos.com/manage) console.
2. On the left panel, click Global Settings, and then on the main panel, click **API credentials**.
3. Click **Add Credential**.
4. In the **Credential name** field, enter a name.
5. (Optional) In the **Description** field, enter a description.
6. Click **Add**.
7. Next to the Client ID, click **Copy**. Make a note of the Client ID.
8. Click Show Client Secret, and then click **Copy**. Make a note of the Client Secret.

### Configuring collection from the Alert Logic console

After  you obtain the client API ID and API key, you must complete the log collection process in the Alert Logic console. This configuration is an account-level integration, which means you can configure more than one instance of Sophos collection. This capability is  useful when more than one instance of the Sophos application exists in your organization.

To access the Application Registry page, click the menu icon (![](../../Resources/Images/dashboard/menu-icon.png)) from the Dashboards page. Click ![](../../Resources/Images/dashboard/configure-icon.png)**Configure**, and then click **Application Registry**.

**To add a new application collection**:

1. In the Application Registry, click the **Sophos** tile, and then click Sophos** Logs**.
2. In the **Application Name** field, enter a name for this Sophos collection instance.
3. In the **Client ID** field, enter the client ID you noted earlier
4. In the **Client Secret** field, enter the client key you noted earlier.
5. (Optional) Enter a **Collection Start** time using a format such as (2020-01-01T16:00:00Z). If the **Collection Start** field is left blank, only logs generated after you configure this collection instance will be collected.             
The collection start time determines how far back you want Alert Logic to collect logs if data already exists in your account. Alert Logic can only collect logs up to 30 days prior to the date you configured this collection instance.
6. Click **ADD**. Wait a few minutes for the application to create and appear in your application list. Do not click **ADD** again.

In the Applications List tab, if you configured your application correctly, within approximately 10 minutes you will see Configured next to the application. For more information about how to add instances or manage existing collecting applications, see [Manage your configured applications](../application-registry.md#Configur).

## Create a Sophos collector for SIEM API

You must complete the following to successfully configure your Sophos Log Collector:

1. [Obtain a Client ID and a secret key in Sophos Central Admin](#Obtain)
2. [Configuring collection from the Alert Logic console](#Configur)

### Create a token in Sophos Central Admin

You must create a token, and then gather the API Access URL and Headers in the Sophos Central Admin console.

**To obtain an API client ID and the API key**:

1. Log in to the [Sophos Central Admin](https://central.sophos.com/manage) console.
2. On the left panel, click Global Settings, and then on the main panel, click **API Token Management.**
3. Click **Add Token** on the upper-right corner.
4. In the **Token name** field, enter a name.
5. Click **Save**.
6. In the API Token Summary page, click **Copy** to copy the API Access URL.
7. Click **Copy** to copy the Headers.

### Configuring collection from the Alert Logic console

After  you create a token and gather the token information, you must complete the log collection process in the Alert Logic console. This configuration is an account-level integration, which means you can configure more than one instance of Sophos collection. This capability is  useful when more than one instance of the Sophos application exists in your organization.

To access the Application Registry page, click the menu icon (![](../../Resources/Images/dashboard/menu-icon.png)) from the Dashboards page. Click ![](../../Resources/Images/dashboard/configure-icon.png)**Configure**, and then click **Application Registry**.

**To add a new application collection**:

1. In the Application Registry, click the **Sophos** tile, and then click Sophos** SIEM API**.
2. In the **Application Name** field, enter a name for this Sophos collection instance.
3. Under Collection Method and Policy, in the **API Access URL** field, enter the API Access URL you copied earlier.
4. In the **x-api-key Header** field, enter only the x-api-key Header portion from the token header you copied earlier.
5. In the **Authorization Header** field, enter only the remaining portion that begins with "Basic" from the token header you copied earlier.
6. (Optional) Enter a **Collection Start** time using a format such as (2020-01-01T16:00:00Z). If the **Collection Start** field is left blank, only logs generated after you configure this collection instance will be collected.             
The collection start time determines how far back you want Alert Logic to collect logs if data already exists in your account. Alert Logic can only collect logs up to 30 days prior to the date you configured this collection instance.
7. Click **ADD**. Wait a few minutes for the application to create and appear in your application list. Do not click **ADD** again.

In the Applications List tab, if you configured your application correctly, within approximately 10 minutes you will see Configured next to the application. For more information about how to add instances or manage existing collecting applications, see [Manage your configured applications](../application-registry.md#Configur).

## Security Content for incidents

Alert Logic builds collectors to capture data from various applications with the goal of creating content that generates security incidents for key security use cases in the Alert Logic console. The following security incidents are available for Sophos:

* Administrative Actions
* User Login AD
* User Behavior AD
