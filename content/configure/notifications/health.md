#  Health Notifications

Health notifications can alert you, subscribed users, or a configured connector when an agent, appliance, or API collector is collecting data or offline (unhealthy).

    Collection assets that have been configured for less than 1 hour are excluded from health notifications.    ## Key concepts

**Health exposures**:  Health exposures result from configuration or connection problems that disrupt access to  Alert Logic product capabilities by interrupting the ability to collect information from your environment. To learn about the Health page, which lists all health exposures in your environment, see [Health](../../analyze/health.md).

**Notifications**: The Notifications feature in the Alert Logic console can alert you, subscribed users, or a configured [connector](../connectors.md) when health statuses that meet the set criteria  occur.

**Collection assets**: Collection assets are the class of assets that collect information in your environment and transfer that data to Alert Logic for analysis.

## Types of collection assets

| Collector Type | Description |
|---|---|
| Alert Logic agent | Alert Logic provides an agent that gathers data that Alert Logic must collect for analysis, such as log messages and network traffic, as well as metadata and host identification information. You must download the agent, and then deploy it to each host you want to monitor, or collect log messages. Alert Logic provides agents for Windows and Linux hosts. For more information, see [Requirements for the Alert Logic Agent](../../requirements/agent.md#reqsAgent). |
| Appliance | The Alert Logic Network IDS appliance is a physical or virtual appliance that gathers network data and enables network scanning. The Alert Logic Managed Web Application Firewall (WAF) appliance is a physical or virtual appliance that provides  WAF services. The Alert Logic Log Manager appliance is a physical appliance for log management services. The Appliance asset type also includes remote collectors installed on hosts for syslog data collection. For more information, see [Alert Logic Requirements for Virtual and Physical Appliances](../../requirements/appliance-requirements.md). Info Dev and technical edits^^ (original text follows): The Alert Logic Appliance is a physical or virtual appliance that gathers network IDS data, enables network scanning, and provides Alert Logic Managed Web Application Firewall (WAF) services. |
| API Collector | Alert Logic offers integration with applications, including API-based integration with SaaS applications and passive log collecting through syslog forwarding  with most firewall platforms. Available applications include products for authentication, productivity, management, and more. Alert Logic serves as a remote collector to receive log data from SaaS and firewall applications related to different incident types, depending on the product type. For more information on configuring API collectors, see [Application Registry](../application-registry.md). |

## Health exposure categories

For each unhealthy asset listed, you can see the health exposure category: connection or configuration.

### Connection exposures

A connection exposure indicates that an asset such as a network appears to be offline. For example, an agent cannot connect to the appliance, or an appliance cannot connect to the Alert Logic back-end environment. Hosts with expired SSL certificates also appear as connection exposures.

### Configuration exposures

A  configuration exposure indicates an issue in your deployment  that can hinder Alert Logic from delivering service properly, such as:

* No appliance installations
* Hosts with no agent
* Misconfiguration preventing an appliance from connecting to the Alert Logic back-end server
* Hosts that have not been recently scanned
* Insufficient policy and role privileges
* Integrated third-party applications with incorrect access credentials
* AWS Config is not enabled in all regions

## **Open the Create a Health Notification page**

You can create a health notification from the Health page or the Notifications page. Whichever method you use, the process is the same after  you open the Create a Health Notification page.

**To create a health notification from the Health page:**

1. In the Alert Logic console, click the menu icon (![](../../Resources/Images/dashboard/menu-icon.png)).
2. Click ![](../../Resources/Images/dashboard/respond-icon.png)**Respond**, and then click **Health** to access the Health page.
3. Click ![](../../Resources/Images/dashboard/notifications-icon.png)  **NOTIFICATIONS**, and then click **Add Notification**.
4. Complete the fields as described in [Create a Health Notification](#CreateaHealthNotification).

To create a health notification from the Notifications page:

1. In the Alert Logic console, click the menu icon (![](../../Resources/Images/dashboard/menu-icon.png)).
2. Click ![](../../Resources/Images/dashboard/manage-icon.png)**Manage**, and then click **Notifications** to access the Notifications page.
3. On the **Alert Notifications** tab, click the add icon (![](../../Resources/Images/Icons/cdAddPlus.png)), and then click **Health**.
4. Complete the fields as described in [Create a Health Notification](#CreateaHealthNotification).

## **Create a Health Notification**

To create a health notification, you enter details about the notification, set the scope for the notification, and then configure delivery. For more information on collection asset statuses and the types of exposures and remediations associated with each, see [Health notification to exposures and remediations map](#Healthnotificationtoexposuresandremediationsmap).

**To enter details about the health notification:**

1. Type a descriptive name for the health notification.
2. Choose whether you want the notification to be active. Turn it off if you want to save the definition but not receive notifications.
3. For an account without [managed accounts](../../prepare/users-roles.md#multiaccount), your customer account is preselected, and the account selector does not appear. If your account is a managing (parent) account, select one or more accounts for which you want to send notifications. You can use the search bar to help you find:
If you choose **Managed Accounts** or **My Account and Managed Accounts**, future  managed accounts will be automatically  subscribed to receive the notification.  You will not need to edit the notification later to add them manually.
   * **Individual accounts**—Your account and  individual managed accounts
   * **Managed Accounts**—This option selects all your managed accounts, excluding your own account, plus any managed accounts added later on.
   * **My Account and Managed Accounts**—This option selects your account and all your managed accounts, plus any managed accounts added later.
5. Choose  one type of collection asset. For more information about collection assets, see [Types of collection assets](#Typesofcollectionassets).
6. Click **NEXT**.

**To set the scope of the health notification:**

1. Select one or more  statuses for the collection asset. For more information on collection asset statuses and the types of exposures and remediations associated with each, see [Health notification to exposures and remediations map](#Healthnotificationtoexposuresandremediationsmap).
2. (Optional) Select one or more asset scopes. If no asset scope is selected,  you will receive notifications for your entire environment.
3. Click **NEXT**.

**To configure delivery for the health notification:**

1. (Optional) Set  preferences for delaying or suppressing notifications:
   * **Delay**—Use the delay preference to prevent notifications for health exposures that you anticipate, or that have a history of automatically resolving within a set amount of time. Health exposures that are resolved before the set delay do not result in a notification. If you set the delay to one hour for an agent offline status, you will not receive a notification unless the status persists for more than one hour.
   * **Suppression**—Use the suppression preference to prevent mass email notifications for notification rules that you anticipate, or that have a history of occurring multiple times at once. Alert Logic suppresses notifications after the first for this rule  for the set amount of time. If you set suppression to one hour for an agent offline status and 25 agents went offline simultaneously, you would receive only the first notification. You only receive future notifications if a new agent goes offline after the one-hour suppression. With no suppression set, you would receive all 25 notifications.
3. To subscribe users to receive a notification email, click **Subscribed User(s)**, and then, under **Notification Delivery**, select the users that you want to receive the notification. The list includes your name and user names  in the managed accounts selected above. You can use the search bar to help you find recipients.
4. To subscribe a connector, click **Subscribed Connector**, and then, under **Notification Delivery**, select a configured connector. For more information about configuring and using connectors, see [Webhook and Email Connectors](../connectors.md).
5. (Optional) Customize the **Email Subject**. You can change the text and insert variables enclosed with double braces: {{*variable*}}. For the variable list, see [ Health Notifications](#Emailsubjectvariables).
6. Click **SAVE**.

## View and manage Health notifications

You can view and manage health notifications from the Notifications page.  See [Manage Notifications](manage.md) for information about how to:

* Filter the list of notifications
* View notification details
* Edit notifications
* Delete notifications

## Receiving a Health notification

After you receive a notification, you can click **INVESTIGATE** to link directly to the specific remediation detail page associated with the health exposure. The remediation detail page is part of the Health console. For more information, see [Open the remediation detail page](../../analyze/health.md#Opentheremediationdetailpage).

## Health notification to exposures and remediations map

| Collection Asset Type | Collection Asset Status | Exposure Names | Remediation Names |
|---|---|---|---|
| Agent | Offline | Alert Logic Agent is Offline | Enable the agent on this host |
| Not Collecting | No logs have been received from the agent on this host for over 24 hours. | Verify Agent Configuration Does Not Prevent Log Traffic |
| No IDS traffic has been received from the agent on this host for over 24 hours. | Verify Agent Configuration Does Not Prevent IDS Traffic |
| Appliance | Offline | The Alert Logic appliance is offline or unable to reach Alert Logic. | Re-enable this appliance |
| Not Collecting | No logs have been received from the appliance on this host for over 24 hours. | Verify Appliance Configuration Does Not Prevent Log Traffic |
| No IDS traffic has been received from the appliance on this host for over 24 hours. | Verify Appliance Configuration Does Not Prevent IDS Traffic |
| Collector | Offline | Collector reports an error communicating application API (offline). | Verify collector configuration and credentials |
| Not Collecting | Collector hasn't collected any data for the last 24 hours. |

| Exposure Impact/Description | Exposure API name | Notification Rules |
|---|---|---|
| Collector is reporting an error while collecting data. | collector_offline | Collector Offline |
| Collector hasn't collected any data for the last 24 hours. | collector_no_collection | Collector Not Collecting |
| Collector is reporting an error while collecting data. Please see evidence for error description. | collector_collection_error | Collector Error |
| The Alert Logic appliance associated has either stopped or is unable to check in with Alert Logic. Ensure that the host is running and is able to reach Alert Logic. | appliance_offline | Appliance Offline |
| N/A? |  | Appliance Not Collecting |
| The remote collector found a malformed log batch saved on the disk for later transport; any remaining log messages in the batch were lost. This warning is transient and should self-resolve with the next collection cycle | appliance_malformed_syslog | Appliance Error |
| An Alert Logic Agent in your deployment is offline and unable to report potential threats. | agent_offline | Agent Offline |
| N/A? |  | Agent Not Collecting |
| The syslog collector failed to listen on the specified TCP or UDP port | agent_slc_blocked_port | Agent Error |
| A problem was observed with WinPcap installation on the host, or the installed WinPcap version is not working correctly. The agent may attempt to self-remediate by restarting WinPcap driver | agent_ids_pcap_failing | Agent Error |
| The file rotation scheme could not be auto-detected from the files matching the specified pattern, or the specified rotation scheme could not be applied to all files matching the specified pattern | agent_ffc_invalid_file_pattern | Agent Error |
| The Windows Event Log file for the indicated host is damaged and cannot be collected. | agent_elc_corrupted_file | Agent Error |
