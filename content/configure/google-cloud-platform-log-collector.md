# Configure Google Cloud Platform Log Collector 

The Alert Logic Google Cloud Platform collector is an AWS-based API Poll (PAWS) log collector library mechanism designed to collect logs from the Google Cloud logs, formerly referred to as Stackdriver. You must generate a Google API, apply the permissions, and then complete the configuration process in the Alert Logic console.

Google Cloud logs do not have host metadata and are formatted in JSON. If you want to collect syslogs, you must use the Alert Logic agent to allow Alert Logic to process them.

Although Alert Logic does not recommend using a Virtual Machine (VM) instance to forward logs to Google Cloud, if you want to collect logs from a VM, you must use a Google logging agent. The Google logging agent sends logs to the VM parent project by default. You must override and send to another project. To learn more about the Google logging agent, see [About the Logging agent](https://cloud.google.com/logging/docs/agent).

## Generate a Google API in Google Cloud Platform

In the Google Cloud Platform console, you must complete a few key tasks for logs to be collected from Google Cloud.

**You must generate a Google API key file**:

1. In the [Google Cloud Platform console,](https://console.cloud.google.com/) go to the Create service account key page.
2. From the Service account list, select **New service account**.
3. In the **Service account name** field, enter a name.
4. From the Role list, select **Project > ****Private Logs Viewer**.        
The Role field authorizes your service account to access resources. You can view and change this field later in the Google Cloud Platform console. If you are developing a production app, specify more granular permissions than Private Logs Viewer. For more information, see [granting roles to service accounts](https://cloud.google.com/iam/docs/granting-roles-to-service-accounts).
5. Click **Create**. A JSON file that contains your key downloads to your computer. Note the JSON key, which you will need later.

## Configuring collection from the Alert Logic console

After you generate your JSON key, you must complete the log configuration process in  the Alert Logic console. This configuration is an account-level integration, which means you can configure more than one instance of Google Cloud collection. This capability is useful when  more than one instance of the application exists.

To access the Application Registry page, click the menu icon (![](../Resources/Images/dashboard/menu-icon.png)) from the Dashboards page. Click ![](../Resources/Images/dashboard/configure-icon.png)**Configure**, and then click **Application Registry**.

**To add a new application collection**:

1. On the Applications List tab, use the drop-down menu to select the application type you want to see.
2. In the Google Cloud tile, click **GET STARTED**.
3. In the **Application Name** field, enter a name for this Google Cloud collection instance.
4. Under Collection Method and Policy, in the **Resource identifiers** field,  enter Google resources from which you want to poll logs. Each element must follow the format <resourceType>/<resourceID> and must be on its own line.
5. In the **Service Account JSON key** field, enter the key associated with service accounts in your Google Cloud account that you noted previously.
6. (Optional) Enter a **Collection Start** time using a format such as 2020-01-01T16:00:00Z. This collection time is the timestamp for when collection begins. The timestamp is a useful if data is in the account before collection was configured.
7. Click **ADD**.

In the Applications List tab, if you configured your application correctly, within approximately 10 minutes you will see "Configured" with a check icon. For more information about how to add instances or manage existing collecting applications, see [Manage your configured applications](application-registry.md#Configur).

## Security Content for incidents

16. Alert Logic builds collectors to capture data from various applications, with the goal of creating security content that is used to generate incidents for key security use cases. As of now, the Security Content team is determining which type incidents can be created for the Google Cloud platform. This information will be made available and updated on this page later in 2020.
