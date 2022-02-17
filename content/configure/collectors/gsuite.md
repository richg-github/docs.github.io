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

A single Alert Logic G Suite collector can collect logs from any or all the content streams that you configure in the Alert Logic console.  You can find G Suite logs collected with keyword search in the Alert Logic console [Search: Log Messages](../../analyze/log-message-search.md) page.

## Create a service account JSON key in Google Cloud Platform

You must complete a few key tasks in the Google Cloud Platform for logs to be collected. You must have a Google Cloud Platform account set up. For information about how to set up a Google Cloud Platform account, see [Get Started with Google Cloud Platform](https://console.cloud.google.com/getting-started).

1. Log in to the [Google Cloud Platform console](https://console.cloud.google.com/).
2. Create a Google Cloud project.  For further instructions, see [Creating and Managing Projects](https://cloud.google.com/resource-manager/docs/creating-managing-projects#creating_a_project).
3. Enable Admin API for this project on this [link](https://console.cloud.google.com/apis/library/admin.googleapis.com).
4. Create a service account in the IAM service page. The service account does not require a role. For further instructions, see go to [Creating a service account](https://developers.google.com/identity/protocols/OAuth2ServiceAccount#creatinganaccount).
5. Create a JSON based credential for the service account. A JSON file that contains your key downloads to your computer. Note the location of JSON file, which you will need later.
6. Delegate domain-wide authority to the service account. Add the scope as [https://www.googleapis.com/auth/admin.reports.usage.readonly](https://www.googleapis.com/auth/admin.reports.usage.readonly) and [https://www.googleapis.com/auth/admin.reports.audit.readonly](https://www.googleapis.com/auth/admin.reports.audit.readonly). For further instructions, go to [Delegating domain-wide authority to the service account](https://developers.google.com/identity/protocols/OAuth2ServiceAccount#delegatingauthority).

## Create a custom role and enable API access in G Suite 

In G Suite, you must create a custom role and enable API access to collect logs. You must have a G Suite account set up.

1. Log in to [G Suite](https://admin.google.com/).
2. You must create a custom admin role with the **Reports** privilege. For further instructions, see [Create, edit, and delete custom admin roles](https://support.google.com/a/answer/2406043?hl=en&amp;ref_topic=9832445).         
To learn more about G Suite privileges, see [Administrator privilege definitions](https://support.google.com/a/answer/1219251).
3. Create an administrative user account, and then assign the role you created to that user account. Make note of the user email address for later steps. For further instructions, see [Add an administrator](https://support.google.com/domains/answer/6304528?hl=en&amp;ref_topic=6317570).
4. Enable API access for G Suite. To learn how to manage API access in G Suite, see [Control which third-party &amp; internal apps access G Suite data](https://support.google.com/a/answer/60757?authuser=3).

## Configure collection in the Alert Logic console

After you set up your G Suite and Google Cloud platform, you must complete the log collection configuration process in the Alert Logic console. This configuration is an account-level integration, which means you can configure more than one instance of G Suite collection. This capability is useful when  more than one instance of the application exists.

To access the Application Registry page, click the menu icon (![](../../Resources/Images/dashboard/menu-icon.png)) from the Dashboards page. Click ![](../../Resources/Images/dashboard/configure-icon.png)**Configure**, and then click **Application Registry**.

**To add a new application collection**:

1. In the Application Registry click the **Google Cloud** tile, and then click **Google Suite Applications**.
2. In the **Application Name** field, enter a name for this G Suite collection instance.
3. Under Collection Method and Policy, in the **Delegated User Email Address** field, enter the email address of the user you created earlier.
4. In the **Service account JSON key** field, enter the contents of the Google JSON file that you downloaded previously from generating a key.
5. Select the applications from which you want to collect logs.
6. (Optional) Enter a **Collection Start** time using a format such as (2020-01-01T16:00:00Z). If the **Collection Start** field is left blank, only logs generated after you configure this collection instance will be collected.             
The collection start time determines how far back you want Alert Logic to collect logs if data already exists in your account. Alert Logic can only collect logs up to 30 days prior to the date you configured this collection instance.
7. Click **ADD**.Wait a few minutes for the application to create and appear in your application list. Do not click **ADD** again.

In the Applications List tab, if you configured your application correctly, within approximately 10 minutes you will see Configured next to the application. For more information about how to add instances or manage existing collecting applications, see [Manage your configured applications](../application-registry.md#Configur).

## Security content for Incidents

Alert Logic builds collectors to capture data from various applications, with the goal of creating security content that is used to generate incidents for key security use cases. Currently, the Alert Logic Security Content team is determining which type incidents can be created for the G Suite product. This information will be made available and updated on this page later in 2020.
