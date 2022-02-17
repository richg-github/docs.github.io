# Configure CrowdStrike Log Collector

The Alert Logic CrowdStrike collector is an AWS-based API Poll (PAWS) log collector library mechanism designed to collect logs from the CrowdStrike platform.

    To view logs collected by all CrowdStrike collectors in your environment, click [here](https://console.search.alertlogic.com/#/search/expert/10785703?aaid=10785703&amp;locid=defender-us-denver&amp;sql=SELECT%0A%20%20%20%20time_recv%20AS%20%22Time%20Received%22,%0A%20%20%20%20message%20AS%20%22Message%22,%0A%20%20%20%20application_id%20AS%20%22Application%20ID%22%0AFROM%20logmsgs%0AWHERE%20EXISTS(%20%22Message%22%20)%0A%20%20%20%20AND%0A%22Application%20ID%22%20IN%20%5B%20'',%20'crowdstrike'%20%5D%0AORDER%20BY%20%22Time%20Received%22%20DESC%0ALIMIT%201000&amp;mode=simple&amp;timeframe=3600). You can view logs collected by CrowdStrike collectors in the Search page in the Alert Logic console. To learn more about the Search feature, see [Get Started with Search](../../get-started/search-a.md). To learn how to create correlations to generate incidents or observations from the collected logs, see [Correlations and Notifications](../notifications/log-correlation.md).    
You must complete the following to successfully configure and verify your CrowdStrike log collector:

1. [Obtain an API client ID and secret key](#Obtain)
2. [Make changes to the API ](#Make)
3. [Configure collection in the Alert Logic console](#ConfigurecollectionintheAlertLogicconsole)
4. [Verify successful configuration](#Configuration)

## Obtain an API client ID and secret key

You must have an admin role in CrowdStrike Falcon platform to generate an API client ID and an API secret key in the CrowdStrike Falcon platform.

**To generate the API client ID and secret key**:

1. On the CrowdStrike Falcon platform, navigate to **API Clients and Keys**.
2. In the **OAuth2 API Clients** table, click **Add new API client**.
3. Enter the following details to define your API client:
   1. In the **Client Name** field, enter the client name.
   2. In the **Description** field, enter the description for the client.
5. In the **API Scopes** field, enable the **Read scope** for **Incident API** and enable the **Read scope** for the **Detection API**.
6. Click **Add** to save the API client to generate the Client ID and Secret Key. Copy and paste the **Client ID** and **Secret Key** in a safe place for later.

## Make changes to the API 

You must first authenticate the API, and then make changes to the Incident and Detection APIs to properly poll from them. Copy and paste the [base URL](https://api.crowdstrike.com/) in a safe place for later.

1. You must authenticate the API. For instructions on how to authenticate the API, see [https://developer.crowdstrike.com/crowdstrike/reference/oauth2-1#oauth2accesstoken-1](https://developer.crowdstrike.com/crowdstrike/reference/oauth2-1#oauth2accesstoken-1).
2. You must update the incident query. For instructions on how to update the incident query see [https://developer.crowdstrike.com/crowdstrike/reference/incidents-1#queryincidents-1](https://developer.crowdstrike.com/crowdstrike/reference/incidents-1#queryincidents-1).
3. You must update the detection query. For instructions on how to update the detection query see [https://developer.crowdstrike.com/crowdstrike/reference/detects-1#querydetects-1](https://developer.crowdstrike.com/crowdstrike/reference/detects-1#querydetects-1).

## Configure collection in the Alert Logic console

After you generate the API client ID and the API secret key, you must complete the next steps of the collection configuration process in the Alert Logic console. You can configure more than one instance of the CrowdStrike collector if you need to monitor logs for more than one CrowdStrike account.

To access the Application Registry page, click the menu icon (![](../../Resources/Images/dashboard/menu-icon.png)) from the Dashboards page. Click ![](../../Resources/Images/dashboard/configure-icon.png)**Configure**, and then click **Application Registry**.

**To add a new CrowdStrike collector**:

1. In the Application Registry, click the **CrowdStrike** tile.
2. In the **Application Name** field, enter a descriptive name for the collector.
3. In the **Client ID** field, enter the client ID you generated from [Obtain an API client ID and secret key](#Obtain).
4. In the **Secret Key** field, enter your secret key you generated from [Obtain an API client ID and secret key](#Obtain).
5. Under **API Names**, select the **Incident** and **Detect** logs for Alert Logic to collect from CrowdStrike.
6. (Optional) In the **Collection Start** field, provide a collection start time stamp in (2020-01-01T16:00:00Z) format.
7. Click **ADD**. Wait 10 minutes for the application to be successfully created and appear in your application list. Do not click **ADD** again while the request is processing.

## Verify successful configuration

You can verify that your CrowdStrike collector is configured correctly in the Configured Applications tab within approximately 10 minutes of adding the integration. For more information about how to add instances or manage existing collecting applications, see [Manage your configured applications](../application-registry.md#Configur).

**To view logs collected by a specific CrowdStrike collector:**

1. In the Application Registry, click the **Configured Applications** tab.
2. Click the **View** dropdown menu for the CrowdStrike collector.
3. Click **VIEW LOGS** to open log search results for the collector.

To view logs collected by all CrowdStrike collectors in your environment, click [here](https://console.search.alertlogic.com/#/search/expert/10785703?aaid=10785703&amp;locid=defender-us-denver&amp;sql=SELECT%0A%20%20%20%20time_recv%20AS%20%22Time%20Received%22,%0A%20%20%20%20message%20AS%20%22Message%22,%0A%20%20%20%20application_id%20AS%20%22Application%20ID%22%0AFROM%20logmsgs%0AWHERE%20EXISTS(%20%22Message%22%20)%0A%20%20%20%20AND%0A%22Application%20ID%22%20IN%20%5B%20'',%20'crowdstrike'%20%5D%0AORDER%20BY%20%22Time%20Received%22%20DESC%0ALIMIT%201000&amp;mode=simple&amp;timeframe=3600).

The Health console also indicates whether the application collector  is healthy or unhealthy. For more information, see [Health](../../analyze/health.md).

## Security Content for CrowdStrike logs

In the Applications List tab, if you configured your application correctly, within approximately 10 minutes you will see Configured next to the application. In the Configured Applications tab, if you configured your application correctly, within approximately 10 minutes you will see the application listed. For more information about how to add instances or manage existing collecting applications, see [Manage your configured applications](../application-registry.md#Configur).

The Health console also indicates whether the application collector  is healthy or unhealthy. For more information, see [Health](../../analyze/health.md).
