# Configure G Suite Log Collector

The Alert Logic G Suite collector is an AWS-based API Poll (PAWS) log collector library mechanism designed to collect logs. You must complete tasks in G Suite and Google Cloud Platform, and then finish the configuration process in the Alert Logic console. The Alert Logic G Suite collector can collect from these specific G Suite applications:

* Login
* Admin
* Access Transparency
* Calendar
* Drive
* Google Plus
* Token
* Groups
* Groups Enterprise
* Mobile
* Rules
* User Accounts

A single Alert Logic G Suite collector can collect logs from any or all the content streams that you configure in the Alert Logic console.

## How Alert Logic G Suite collectors work

The Alert Logic G Suite Collector uses the Google Admin Activity Reports API to capture the audit logs for administrative activities. By polling this API, Alert Logic can report on the following event types for G Suite:

* APPLICATION_SETTINGS
* CALENDAR_SETTINGS
* CHAT_SETTINGS
* CHROME OS_SETTINGS
* CONTACTS_SETTINGS
* DELEGATED_ADMIN
* DOCS_SETTINGS
* DOMAIN_SETTINGS
* EMAIL_SETTINGS
* GROUP_SETTINGS
* LICENSES_SETTINGS
* MOBILE_SETTINGS
* ORG_SETTINGS
* SECURITY_SETTINGS
* SITES_SETTINGS
* USER_SETTINGS

You can select the options listed for collecting from specific applications in the Alert Logic console when you configure your G Suite collector. Selecting all of the event types allows you to gain visibility into each of the event reports listed above.

## Create a custom role and enable API access in G Suite 

In G Suite, you must create a custom role and enable API access to collect logs.

1. Log in to [G Suite](https://admin.google.com/).
2. You must create a custom admin role with the **Reports** privilege. For further instructions, see [Create, edit, and delete custom admin roles](https://support.google.com/a/answer/2406043?hl=en&amp;ref_topic=9832445).         
To learn more about G Suite privileges, see [Administrator privilege definitions](https://support.google.com/a/answer/1219251).
3. Create an administrative user account, and then assign the role you created to that user account. For further instructions, see [Add an administrator](https://support.google.com/domains/answer/6304528?hl=en&amp;ref_topic=6317570).
4. Enable API access for G Suite. To learn how to manage API access in G Suite, see [Control which third-party &amp; internal apps access G Suite data](https://support.google.com/a/answer/60757?authuser=3).

## Create a service account JSON key in Google Cloud Platform

You must complete a few key tasks in the Google Cloud Platform for logs to be collected. You must have a Google Cloud Platform account set up. For information about how to set up a Google Cloud Platform account, see [Get Started with Google Cloud Platform](https://console.cloud.google.com/getting-started).

1. Log in to the [Google Cloud Platform console](https://console.cloud.google.com/).
2. Create a Google Cloud project.  For further instructions, see [Creating and Managing Projects](https://cloud.google.com/resource-manager/docs/creating-managing-projects#creating_a_project).

Alert Logic recommends you use the same administrative user account you created in the previous section.4. Enable Admin API at [https://console.cloud.google.com/apis/library/admin.googleapis.com](https://console.cloud.google.com/apis/library/admin.googleapis.com).
5. Create a service account. For further instructions, see go to [Creating a service account](https://developers.google.com/identity/protocols/OAuth2ServiceAccount#creatinganaccount).        
Alert Logic recommends that you download the JSON credential file.
6. Delegate domain-wide authority to the service account, and then add the scope as [https://www.googleapis.com/auth/admin.reports.audit.readonly](https://www.googleapis.com/auth/admin.reports.audit.readonly). For further instructions, go to [Delegating domain-wide authority to the service account](https://developers.google.com/identity/protocols/OAuth2ServiceAccount#delegatingauthority).

## Configure collection in the Alert Logic console

After you set up your G Suite and Google Cloud platform, you must complete the log collection configuration process in the Alert Logic console. This configuration is an account-level integration, which means you can configure more than one instance of G Suite collection. This capability is useful when  more than one instance of the application exists.

To access the Application Registry page, click the menu icon (![](../Resources/Images/dashboard/menu-icon.png)) from the Dashboards page. Click ![](../Resources/Images/dashboard/configure-icon.png)**Configure**, and then click **Application Registry**.

**To add a new application collection**:

1. On the Applications List tab, use the drop-down menu to select the application type you want to see.
2. In the G Suite tile, click **GET STARTED**.
3. In the **Application Name** field, enter a name for this G Suite collection instance.
4. Under Collection Method and Policy, in the **Delegated User Email Address** field, enter the email address you used to set up the user administrative account that you set up in G Suite.
5. In the **Service account JSON key** field, enter the Google JSON key associated with the service account you created in the Google Cloud Platform.
6. Select the applications from which you want to collect logs.
7. (Optional) Enter a **Collection Start** time using a format such as 2020-01-01T16:00:00Z. This collection time is the timestamp for when collection begins. The timestamp is a useful tool if data is in the account before collection was configured. Data for up to seven previous days is potentially available.
8. Click **ADD**.

In the Applications List tab, if you configured your application correctly, within approximately 10 minutes you will see "Configured" with a check icon. For more information about how to add instances or manage existing collecting applications, see [Manage your configured applications](application-registry.md#Configur).

## Security content for Incidents

Alert Logic builds collectors to capture data from various applications, with the goal of creating security content that is used to generate incidents for key security use cases. Currently, the Alert Logic Security Content team is determining which type incidents can be created for the G Suite product. This information will be made available and updated on this page later in 2020.
