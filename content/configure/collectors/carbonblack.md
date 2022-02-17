# Configure Carbon Black Log Collector 

The Alert Logic Carbon Black collector is an AWS-based API Poll (PAWS) log collector library mechanism designed to collect logs from the Carbon Black cloud. You can find Carbon Black logs collected with keyword search in the Alert Logic console[Search: Log Messages](../../analyze/log-message-search.md) page. Alert Logic also generates security incidents from Carbon Black Endpoint Standard logs in the [Endpoint Security Incidents](../../analyze/endpoint-incidents.md) page.

The steps to configure the Carbon Black collector depend on which API you want to collect from: Carbon Black Alerts API, Carbon Black Audit API, or both Carbon Black EDR and Endpoint Standard logs via an Amazon S3 bucket.  For instructions on how to configure Carbon Black to collect logs for your specific API see:

* [Create a Carbon Black collector for Alerts API](#AlertsAPI)
* [Create a Carbon Black collector for Audit Log collection](#AuditLogs)
* [Create a Carbon Black collector for EDR and Endpoint Standard log collection via Amazon S3 bucket](#EDRLogs)

If you previously configured the Carbon Black collector, you were only able to successfully collect logs from the Carbon Black Alerts API. You can now configure the  collector to collect from both  EDR and Endpoint Standard logs.

## Create a Carbon Black collector for Alerts API

You must complete the following to successfully configure your Carbon Black collector for the Alerts API:

1. [Create the Carbon Black API key and API ID](#Create2)
2. [Determine your Carbon Black API URL ](#domain)
3. [Configure collection for Alerts API from the Alert Logic console](#Configur)

### Create the Carbon Black API key and API ID

In the Carbon Black Cloud console, you must create an API secret key and an API ID to collect logs from the Alerts API.

**To create an API secret key and API ID**:

1. In the  Carbon Black Cloud console, go to **Settings**, click **API Access**, and then click **API Keys**.
2. Click **Add API**.
3. In the **Name** field, enter a name for this API.
4. In the **Access Level type** drop-down list, select **API**.
5. Click **SAVE**. Make note of the API secret key and the API ID.

### Determine your Carbon Black API URL 

The API URL for the Alerts API you use depends on the region of the Carbon Black domain location. Refer to the table below to see which is the appropriate API URL:

| Environment (Region)	 | URL |
|---|---|
| Prod01 (North America) | https://api.confer.net |
| Prod02 (North America) | https://api5.conferdeploy.net |
| Prod05 (North America) | https://api-prod05.conferdeploy.net |
| Prod06 (UK and EU) | https://api-prod06.conferdeploy.net |
| ProdNRT (Asia Pacific) | https://api-prodnrt.conferdeploy.net |

### Configure collection for Alerts API from the Alert Logic console

After  you create the API secret key, create an API ID, and determine the appropriate Carbon Black API URL, you must complete the log collection process in the Alert Logic console. This configuration is an account-level integration, which means you can configure more than one instance of Carbon Black collection. This capability is  useful when more than one instance of the Carbon Black application exists in your organization.

To access the Application Registry page, click the menu icon (![](../../Resources/Images/dashboard/menu-icon.png)) from the Dashboards page. Click ![](../../Resources/Images/dashboard/configure-icon.png)**Configure**, and then click **Application Registry**.

**To add a new application collection for the Alerts API**:

1. In the Applications Registry, click the **VMWare** tile, and then click Carbon Black** Search Alerts Logs**.
2. In the **Application Name** field, enter a name for this Carbon Black collection instance.
3. Under Collection Method and Policy, in the **Carbon Black Domain** field, enter the Carbon Black domain location.
4. In the **API Key** field, enter the API Key you noted earlier.
5. In the **Organization Key** field, enter the Org Key you noted earlier.
6. In the **API Secret** field, enter the token you noted earlier.
7. (Optional) Enter a **Collection Start** time using a format such as (2020-01-01T16:00:00Z). If the **Collection Start** field is left blank, only logs generated after you configure this collection instance will be collected.             
The collection start time determines how far back you want Alert Logic to collect logs if data already exists in your account. Alert Logic can only collect logs up to 30 days prior to the date you configured this collection instance.
8. Click **ADD**. Wait a few minutes for the application to create and appear in your application list. Do not click **ADD** again.

In the Applications List tab, if you configured your application correctly, within approximately 10 minutes you will see Configured next to the application. For more information about how to add instances or manage existing collecting applications, see [Manage your configured applications](../application-registry.md#Configur).

## Create a Carbon Black collector for Audit Log collection

You must complete the following to successfully configure your Carbon Black collector for the Audit Log collection:

1. [Create the Carbon Black API key and API ID](#Create2)
2. [Determine your Carbon Black API URL ](#Determin)
3. [Configure collection for Alerts API from the Alert Logic console](#Configur)

### Create the Carbon Black API key and API ID, and gather the org key 

In the Carbon Black Cloud console, you must create an API secret key and an API ID, and gather the organization key to collect audit logs.

**To create an API secret key  and API ID, and find the org key**:

1. In the  Carbon Black Cloud console, go to **Settings**, click **API Access**, and then click **API Keys**.
2. Your Org Key is listed on the upper left corner. Make a note of it.
3. Click **Add API**.
4. In the **Name** field, enter a name for this API.
5. In the **Access Level type** drop-down list, select **Custom**, and then in the **Custom Access Level** drop-down list, select **View All**.
6. Click **SAVE**. Make note of the API secret key and the API ID.

### Determine your Carbon Black API URL 

The API URL for audit logs depends on the region of the Carbon Black domain location. Refer to the table below to see which is the appropriate API URL:

| Environment (Region)	 | URL |
|---|---|
| Prod01 (North America) | https://dashboard.confer.net |
| Prod02 (North America) | https://defense.conferdeploy.net |
| Prod05 (North America) | https://defense-prod05.conferdeploy.net |
| Prod06 (UK and EU) | https://defense-eu.conferdeploy.net |
| ProdNRT (Asia Pacific) | https://defense-prodnrt.conferdeploy.net |

### Configure collection for Audit logs in the Alert Logic console

After  you create the API secret key and an API ID, gather the organization key, and determine the API URL, you must complete the log collection process in the Alert Logic console. This configuration is an account-level integration, which means you can configure more than one instance of Carbon Black collection. This capability is  useful when more than one instance of the Carbon Black application exists in your organization.

To access the Application Registry page, click the menu icon (![](../../Resources/Images/dashboard/menu-icon.png)) from the Dashboards page. Click ![](../../Resources/Images/dashboard/configure-icon.png)**Configure**, and then click **Application Registry**.

**To add a new application collection for audit logs**:

1. In the Applications Registry, click the **VMWare** tile, and then click Carbon Black** Audit Logs**.
2. In the **Application Name** field, enter a name for this Carbon Black collection instance.
3. Under Collection Method and Policy, in the **Carbon Black Domain** field, enter the Carbon Black domain location.
4. In the **API Key** field, enter the API Key you noted earlier.
5. In the **API Secret** field, enter the token you noted earlier.
6. (Optional) Enter a **Collection Start** time using a format such as (2020-01-01T16:00:00Z). If the **Collection Start** field is left blank, only logs generated after you configure this collection instance will be collected.             
The collection start time determines how far back you want Alert Logic to collect logs if data already exists in your account. Alert Logic can only collect logs up to 30 days prior to the date you configured this collection instance.
7. Click **ADD**. Wait a few minutes for the application to be successfully created and appear in your application list. Do not click **ADD** again while the request is processing.

In the Applications List tab, if you configured your application correctly, within approximately 10 minutes you will see Configured next to the application. For more information about how to add instances or manage existing collecting applications, see [Manage your configured applications](../application-registry.md#Configur).

## Create a Carbon Black collector for EDR and Endpoint Standard log collection via Amazon S3 bucket

You must have the following information that you retrieve from the AWS console to successfully configure your Carbon Black collector for both EDR and Endpoint Standard logs collection:

* **Role ARN**—IAM role granting Alert Logic access to your S3 bucket.
* **External ID**—The external ID if one is assigned to the IAM role.
* **S3 bucket name**—The name of the S3 bucket that stores the collected logs required.
* **S3 object key prefix** (Optional)—The object key prefix to limit log collection to a folder.
* **SNS topic ARN**—The ARN Amazon SNS topic that receives S3 notifications.
* **SNS topic region**—The AWS region of the SNS topic and  the S3 bucket.

### Configure collection for EDR and Endpoint Standard log collection via Amazon S3 bucket in the Alert Logic console

After  you  gather the required information from the AWS console and determine the SNS topic region, you must complete the log collection process in the Alert Logic console. This configuration is an account-level integration, which means you can configure more than one instance of Carbon Black collection. This capability is  useful when more than one instance of the Carbon Black application exists in your organization.

To access the Application Registry page, click the menu icon (![](../../Resources/Images/dashboard/menu-icon.png)) from the Dashboards page. Click ![](../../Resources/Images/dashboard/configure-icon.png)**Configure**, and then click **Application Registry**.

**To add a new application collection for audit logs**:

1. In the Applications Registry, click the **VMWare** tile, and then click Carbon Black** EDR and Endpoint Standard**.
2. In the **Application Name** field, enter a name for this Carbon Black collection instance.
3. Under Collection Method and Policy, in the **Role ARN** field, enter the ARN you copied from the AWS console after you created the IAM role.
4. In the **External ID** field, enter the external ID assigned in the IAM role.
5. In the **S3 Bucket Name** field, enter the name of S3 bucket.
6. (Optional) In the ****S3 object key prefix**** field, enter the object key prefix if you want to limit log collection to a specific folder.
7. In the **SNS Topic ARN** field, enter the name of the ARN Amazon SNS topic that receives S3 notifications.
8. Under  the SNS Topic Region, select the region of the SNS topic and  the S3 bucket.
9. Click **ADD**. Wait a few minutes for the application to be successfully created and appear in your application list. Do not click **ADD** again while the request is processing.

In the Applications List tab, if you configured your application correctly, within approximately 10 minutes you will see Configured next to the application. For more information about how to add instances or manage existing collecting applications, see [Manage your configured applications](../application-registry.md#Configur).
