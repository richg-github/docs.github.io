# Configure Microsoft Office 365 Log Collector

The instructions in this document are for a new setup  of the Microsoft Office 365 log collector. For instructions on how to update Office 365 log collection by using the Alert Logic console, see [Update to the new collector](#Update). If you need to reference instructions or information for the older setup of the log collector, see [Set Up Collection of Microsoft Office 365 Logs](../prepare/office365-log-collector.md).

The Alert Logic Microsoft Office 365 collector is an AWS-based API Poll (PAWS) log collector library mechanism designed to collect logs. To collect Office 365 logs, you must first create and set up an Alert Logic application in Microsoft Azure. To perform the setup required to grant Alert Logic permission to collect Office 365 logs, you must have access to a Microsoft Office 365 account with administrative privileges. You complete the configuration process in the Alert Logic console.

The Alert Logic Microsoft Office 365 collector can collect from these specific Office 365 content streams:

* Audit logs from Azure Active Directory
* Audit logs from Microsoft Office 365 Exchange
* Audit logs from SharePoint
* General audit logs

A single Office 365 collector can collect logs from any or all the content streams that you configure in the Alert Logic console. These audit logs are collected through Microsoft Stream. For more information on Microsoft Stream, go to [Audit logs in Microsoft Stream](https://docs.microsoft.com/en-us/stream/audit-logs).

## Register a new Office 365 web application

In the Office 365 portal, you must register a new Office 365 web application to collect Office 365 logs.

**To register an Office 365 web application:**

1. Log into the [Office 365 portal](https://portal.office.com/) as an Active Directory tenant administrator.
2. In the left menu,  click **Azure Active Directory**.
3. Select **App Registrations**, and then click **+ New application registration**.
4. Provide the following information in the fields:
   * Enter a name for the application —for example, alo365collector.
   * Under **Supported account types**, select **Single tenant** .
   * Under **Redirect URI (optional)**, leave the Redirect URI field blank.
6. Click **Register**. Note the Application (client) ID, for example, a261478c-84fb-42f9-84c2-de050a4babe3, and the Directory (tenant) ID.

## Set up Active Directory security permissions

You must set up Active Directory security permissions for the application you created so it can read threat intelligence data and activity reports for your organization.

**To set up Active Directory permissions:**

1. On the main panel under the new application, click **View API Permissions**, and then click **+ Add a permission**.
2. Locate and click **Office 365 Management APIs**.
3. In **Application permissions**, expand and select **ActivityFeed.Read**, **ActivityReports.Read** (both), **ServiceHealth.Read**, and **ThreatIntelligence.Read** (both).
4. Ensure all necessary permissions are selected, and then click **Add permissions**.
5. Click **Grant admin consent**, and then click **Accept** to confirm.
      Only the Active Directory tenant administrator can grant permissions to an Azure Active Directory application.      7. On the left navigation area, select **Certificates &amp; secrets**, and then click **+ New client secret**.
8. Type a key **Description** and set the expiration to **Never**.
9. Click **Add**.
10. Save the value (client secret), which you will need later.

## Configure collection in the Alert Logic console

After you register a new Office 365 application and set up permissions, you must complete the log collection configuration process in the Alert Logic console. This configuration is an account-level integration, which means you can configure more than one instance of Office 365 collection. This capability is useful when  more than one instance of the application exists.

To access the Application Registry page, click the menu icon (![](../Resources/Images/dashboard/menu-icon.png)) from the Dashboards page. Click ![](../Resources/Images/dashboard/configure-icon.png)**Configure**, and then click **Application Registry**.

**To add a new application collection**:

1. On the Applications List tab, use the drop-down menu to select the application type you want to see.
2. In the Office 365 tile, click **GET STARTED**.
3. In the **Application Name** field, enter a name for this Office 365 collection instance.
4. Under Collection Method and Policy, in the **Client ID** field, enter the Azure Client ID associated with your registered Office 365 application.
5. In the **Client Secret**, enter your client secret.
6. In the **Tenant ID** field, enter your tenant ID. To find your Office 365 tenant ID, see [Find your Office 365 tenant ID](https://support.office.com/en-gb/article/find-your-office-365-tenant-id-6891b561-a52d-4ade-9f39-b492285e2c9b).
7. Select the content streams from which you want to collect logs.
8. (Optional) Enter a **Collection Start** time using a format such as 2020-01-01T16:00:00Z. This collection time is the timestamp for when collection begins. The timestamp is a useful tool if data is in the account before collection was configured. Data for up to seven previous days is potentially available.
9. Click **ADD**.                    Alert Logic Office 365 accounts for some third-party product APIs that may fail if attempting to pull log data for an older timeframe that is not available. The Alert Logic Office 365 collector does not attempt an invalid request to the API, and instead moves the target collection date to the earliest valid date available.

In the Applications List tab, if you configured your application correctly, within approximately 10 minutes you will see "Configured" with a check icon. For more information about how to add instances or manage existing collecting applications, see [Manage your configured applications](application-registry.md#Configur).

## Security content for Incidents

Alert Logic builds collectors to capture data from various applications, with the goal of creating security content that is used to generate incidents for key security use cases. Currently, the Alert Logic Security Content team is determining which type incidents can be created for the Office 365 product. This information will be made available and updated on this page later in 2020.

## Update to the new collector
