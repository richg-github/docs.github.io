# Configure Mimecast Log Collector

The Alert Logic Mimecast collector is an AWS-based API Poll (PAWS) log collector library mechanism designed to collect logs from the Mimecast platform.

    To view logs collected by all Mimecast collectors in your environment, click [here](https://console.search.alertlogic.com/#/search/expert/acting?mode=simple&amp;sql=SELECT%0A%20%20%20%20time_recv%20AS%20%22Time%20Received%22,%0A%20%20%20%20message%20AS%20%22Message%22%0AFROM%20logmsgs%0AWHERE%20application_id%20%3D%20%27Mimecast%27%0AORDER%20BY%20%22Time%20Received%22%20DESC%0ALIMIT%201000&amp;timeframe=3600). To learn more about the Search feature, see [Get Started with Search](../../get-started/search-a.md). To learn how to create correlations to generate incidents or observations from the collected logs, see [Correlations and Notifications](../notifications/log-correlation.md).    
You must complete the following to successfully configure and verify your Mimecast log collector:

1. [Set up the Mimecast application](#Application)
2. [Configure collection in the Alert Logic console](#ConfigurecollectionintheAlertLogicconsole)
3. [Verify successful configuration](#Configuration)
4. Create incidents in the Alert Logic console

## Set up the Mimecast application

You must identify your regional base URL, enable enhanced logging,  add a custom API application, create a new user profile and application setting, and generate API access and secret Keys in the Mimecast administrator portal.

### Identify your base domain URL

Copy and paste the [base URL](https://integrations.mimecast.com/documentation/api-overview/global-base-urls/) for your host region in a safe place for later.

### Enable enhanced logging for your account

You must enable the log API endpoint in the Mimecast console.

1. Log into the Administration Console.
2. Go to **Administration > Account > Account Settings** menu.
3. Click the **Enhanced Logging** section.
4. Enable the log type(s) you would like to get by using the Alert Logic Mimecast collector.

For more information on enabling the log endpoint, see [SIEM log API endpoint](https://integrations.mimecast.com/documentation/endpoint-reference/logs-and-statistics/get-siem-logs/). For a description of Mimecast SIEM logs, see [Understanding SIEM Logs](https://integrations.mimecast.com/documentation/tutorials/understanding-siem-logs/).

### Add a custom API application for integration with Alert Logic

You must [add an API application](https://community.mimecast.com/s/article/Managing-API-Applications-505230018) in the Mimecast console. This procedure creates an Application ID and Application Key that you target when you configure the Mimecast collector later in the Alert Logic console later.

1. Log into the Administration Console.
2. Navigate to the **Administration | Services | API and Platform Integrations** menu.
3. Click the **Your Application Integrations** tab.
4. Click **Add API Application**.
5. In the details section, provide the following information:
   * **Application Name**— Name of your Alert Logic Integration. Example: "Alert Logic Log Collector"
   * **Category**— SIEM Integration
   * Select the **Enable Extended Session** option so that the access keys generated for the application do not  expire based on the Authentication Profile's Authentication TTL value. This option prevents interruptions to the Alert Logic Mimecast collector.
   * **Description**— Provide an additional description of the integration. For example, "Our cybersecurity Managed Detection and Response (MDR) provider"
7. Click **Next**.
8. In the settings section, provide the following information:
   * Developer: Alert Logic
   * Email: info@alertlogic.com
10. Click **Next**.
11. Verify the information in the Summary page.
12. Click **Add**.
13. Copy and paste the **Application ID** and **Application Key** in a safe place for later.

### Create a user profile for the Alert Logic integration

You must create a user profile with the correct permissions to generate API keys for  Mimecast collector [authentication](https://integrations.mimecast.com/documentation/api-overview/authentication-scripts-server-apps/).

**To create a new user:**

1. Log into the Administration Console.
2. Navigate to the **Administration | Directories | Internal Directories** menu.
3. Click the internal domain you want for your new user, which is used to get API keys later. Example: "@alertlogic.com"
4. Click **New Address** and complete the form to create a new user.
5. Copy and paste the user name (example: "Log_Master@alertlogic.com") and password  in a safe place for later.

**To add the user to the administrative role:**

1. Navigate to the **Administration | Account | Roles** menu.
2. Right-click the **Basic Administrator** role and click **Add users to role**.
3. Select the new user that you created.
4. Click **Add Selected Users**.

**To create a new group to add your users:**

1. Navigate to the **Administration | Directories | Profile Groups** menu.
2. Click the **+** icon on a parent directory to create a new child group directory named "New Folder." If you aren't sure which parent directory to add the group under, use **Root**. To edit the name, click the group and change the name in the text box. Example: "Alert Logic Logs Admin"
3. Click the **Build** tab, and then click **Add Email Addresses**.
4. Enter the email address of the new user that you created. Example: "Log_Master@alertlogic.com".
5. Click **Save and Exit**.

**To create a new authentication profile:**

1. Navigate to the **Administration | Services | Applications** menu.
2. Click the **Authentication Profiles** tab.
3. Click **New Authentication Profile**.
4. In the **Description** field, enter a name for your new profile. Example: "API Authentication Profile for the Alert Logic Log collector."
5. Onthe **Authentication TTL** dropdown menu, click **Never Expires**.
6. Leave the other settings as default.
7. Click **Save and Exit**.

**To create a new application setting:**

You must create a new application setting to bind the user group, authentication profile, and custom API application to each other.

1. Navigate to the **Administration | Services | Applications** menu.
2. Click the **New Application Settings** tab.
3. Click **New Authentication Profile**.
4. In the **Description** field, enter a name for your new setting. Example: "API Application Setting for the Alert Logic Log collector."
5. In the **Group** field, paste the group you created.
6. In the **Authentication Profile** field, select the authentication profile you created.
7. Click **Save and Exit**.

### Create the API Access Key and Secret Key

You must create user associated keys. These keys authorize a user profile for the Alert Logic Mimecast collector to access APIs and get information from Mimecast.

Troubleshooting: You may have to disable SAML Enforce for your Mimecast account to generate User Association Keys. SAML Enforce is used to force all integrations into a single-sign-on with identical keys.1. Navigate to the **Administration | Services | API and Platform Integrations** menu.
2. Click the **Your Application Integrations** tab.
3. Click the application you created in [Add a custom API application for integration with Alert Logic](#AddacustomAPIapplicationforintegrationwithAlertLogc).
4. Click **Create Keys**.
5. For **Email Address**, enter the user profile e-mail address you created in [Create a user profile for the Alert Logic integration](#CreateauserprofileforAlertLogicintegration).
6. Click **Next**.
7. In the Authentication dialog box, provide the following information:
   * Type: Cloud.
   * Password: Enter the user profile password you created in [Create a user profile for the Alert Logic integration](#CreateauserprofileforAlertLogicintegration).
9. Click **Next.**
10. If prompted, complete MFA in the verification dialog.
11. Click **Next**.
12. Copy and paste the **Access Key** and **Secret Key** in a safe place for later.

**Troubleshooting:** If you receive an error during this step, you must reach out to Mimecast customer service to perform a workaround that only Super Administrator users and Mimecast employees can perform. Tell your customer support agent to reference ticket #00395754 for guidance.## Configure collection in the Alert Logic console

After you [Set up the Mimecast application](#Application), you must complete the next step of the collection configuration process in the Alert Logic console. You can configure more than one instance of the Mimecast collector if you need to monitor logs for more than one Mimecast account.

To access the Application Registry page, click the menu icon (![](../../Resources/Images/dashboard/menu-icon.png)) from the Dashboards page. Click ![](../../Resources/Images/dashboard/configure-icon.png)**Configure**, and then click **Application Registry**.

**To add a new Mimecast collector**:

1. In the Application Registry, click the **Mimecast** tile.
2. In the **Application Name** field, enter a descriptive name for the collector.
3. In the **Mimecast Domain** field, paste the [base URL](https://integrations.mimecast.com/documentation/api-overview/global-base-urls/) you verified in [Identify your base domain URL](#URL)
4. In the **Application ID** field paste the application ID you created in [Add a custom API application for integration with Alert Logic](#AddacustomAPIapplicationforintegrationwithAlertLogc).
5. In the **Application Key** field, paste the application key you created in [Add a custom API application for integration with Alert Logic](#AddacustomAPIapplicationforintegrationwithAlertLogc).
6. In the **API Access Key** field, paste the access key you created in [Create the API Access Key and Secret Key](#Keys).
7. In the **API Secret Key** field, paste the secret key you created in [Create the API Access Key and Secret Key](#Keys).
8. Under **Application Names**, select which types of logs you want Alert Logic to collect from Mimecast.
9. (Optional) In the **Collection Start** field, provide a collection start time stamp in (2020-01-01T16:00:00Z) format.
10. Click **ADD**. Wait 10 minutes for the application to be successfully created and appear in your application list. Do not click **ADD** again while the request is processing.

## Verify successful configuration

You can verify that your Mimecast collector is configured correctly in the Configured Applications tab within approximately 10 minutes of adding the integration. For more information about how to add instances or manage existing collecting applications, see [Manage your configured applications](../application-registry.md#Configur).

**To view logs collected by a specific Mimecast collector:**

1. In the Application Registry, click the **Configured Applications** tab.
2. Click the **View** dropdown menu for the Mimecast collector.
3. Click **VIEW LOGS** to open log search results for the collector.

To view logs collected by all Mimecast collectors in your environment, click [here](https://console.search.alertlogic.com/#/search/expert/acting?mode=simple&amp;sql=SELECT%0A%20%20%20%20time_recv%20AS%20%22Time%20Received%22,%0A%20%20%20%20message%20AS%20%22Message%22%0AFROM%20logmsgs%0AWHERE%20application_id%20%3D%20%27Mimecast%27%0AORDER%20BY%20%22Time%20Received%22%20DESC%0ALIMIT%201000&amp;timeframe=3600).

The Health console also indicates whether the application collector  is healthy or unhealthy. For more information, see [Health](../../analyze/health.md).

## Security Content for Mimecast Logs

In the Applications List tab, if you configured your application correctly, within approximately 10 minutes you will see Configured next to the application. In the Configured Applications tab, if you configured your application correctly, within approximately 10 minutes you will see the application listed. For more information about how to add instances or manage existing collecting applications, see [Manage your configured applications](../application-registry.md#Configur).

The Health console also indicates whether the application collector  is healthy or unhealthy. For more information, see [Health](../../analyze/health.md).

## Security content for Incidents

Alert Logic builds collectors to capture data from AWS Network Firewall and various other applications to create security content that is used to generate incidents for key security use cases. The following security incidents are available for AWS Network Firewall:

* Administrative Actions?
* User Login AD?
* User Behavior AD?

For more information about authentication application security content, see [Authentication Application Security Incidents](../../analyze/security-incidents.md).
