# Alert Logic Managed Web Application Firewall (WAF) Basics

Alert Logic Managed Web Application Firewall (WAF) is a web server protection  that actively blocks attacks on your web servers.

**To access WAF  in the **Alert Logic console:

1. In the Alert Logic console, enter your  credentials.
2. Click the ![](../../Resources/Images/dashboard/configure-icon.png)**Configure** menu item, and then click WAF.

You can check the operational status of the Alert LogicWAF in the Service Status page in the Alert Logic console. Alert Logic recommends that you subscribe to the Service Status page and all your Alert Logic components, including WAF. For more information about the Service Status page and how to subscribe, see [Service Status](../../analyze/service-status.md).

## WAF websites

The WAF Websites page allows you to search and apply filters to narrow the list of results on the page. You can perform a website or IP address search across all displayed websites by using the search bar. To search websites,  type the website or IP address you want to investigate in the search bar, and then click **Search**.

You can apply filters based on customer and/or appliance to conduct an investigation into websites. You can combine these custom search parameters to refine your results.

To define filters for websites:

1. In the WAF page, click **Websites**.
2. Click **Filters**. A filters area will expand and display choices.
3. In the **All Appliances** list, select the appliance, and then select whether to include (**In**) or exclude (**Not In**).
4. Click **Filter**.

To reset customer and appliance filters to default, click **Clear Filters**.

### Manage a website

You can manage website options regarding WAF, ADC, learning, logs, and reports. To learn how to manage options, see [WAF](manual/ch_waf.md), and [Application Delivery Controller (ADC)](manual/ch_adc.md).

## Web Security Manager appliances

To search appliances with filters:

1. In the WAF page, click **Appliances**.
2. Click **Filters**. A filters area will expand and display choices.
3. In the **All Appliances** list, select the appliance.
4. Click **Filter**.

To reset customer and appliance filters to default, click **Clear Filters**.

### Define appliance configuration filters 

You can use filters to customize the configuration sections shown for appliances listed on the WAF management interface. Viewable sections include network, date/time settings, logging to external host, and more.

To define appliance configuration filters:

1. In the WAF page, click **Appliances**.
2. Click **View Config** for the appliance you wan to configure.
3. Click the configuration section you want to view. (Click the configuration section again to hide it.)

To view all configuration sections, click **Show All**. To hide all configuration sections, click **Hide All**.

### Manage an appliance

You can manage WAF appliance options such as  operating modes. To manage a WAF appliance, in the WAF page, click **Appliances**. In the table of appliances, within the corresponding row, click **Manage Appliance**. To learn how to manage your appliance, see [Websites](manual/ref_services.md).

## Manage SSL certificates

When you create a website proxy for an existing HTTPS web server, you must export the SSL certificate from the web server and import it into WAF. WAF supports importing PKCS12, PEM (Apache), and intermediate encoded server certificates.

To manage a WAF certificate, in the WAF page, click **Certificates**, and then click **Manage Certificate** for the certificate you want to manage. You can also use the search bar to find a specific certificate. To learn howto configure your SSL certificates, see [Manage Your SSL Certificates](manage-certificates.md).

## Deny logs

Deny logs list the requests that WAF denied based on your security policies when the appliance is configured to Protect mode.  If the appliance is configured to Detect mode, deny logs continue to be generated but the traffic is not blocked.

When you first configure WAF, Alert Logic recommends that you start in detect mode and study deny logs before you create security policies. If you study the deny logs, you can determine which requests are false positives that you can whitelist and which requests represent threats you want to block.

### Dashboard Deny Log page

For the security administrator, you must have the ability to monitor the deny log for all websites. The deny summary window provides summarized log data for all configured websites. The window consists of two sections:

* An interactive graph with a drill down functionality that summarizes all deny log events in a column graph.
* A more detailed interactive list with drill down functionality that shows deny log events for all websites above a configured risk level (default medium).

Both elements allow you to narrow in on events in the specific website's deny log.

To access the Dashboards Deny Logs page, in the WAF page, click **Websites**, and then click **Manage Website** on the website you want to manage. You can filter by appliance, or use the search bar to look for a website. In the WAF management interface, on the left panel, under Dashboards, click **Deny Log**. For more information about the Dashboard Deny Log page, see [Deny Log ](manual/ch_dashboards.md#ref_dashboards_deny_log.md).

### View the website deny log 

The Deny log page provides access to all denied requests to the proxy. Filtering functions allows for fine grained filtering of log information to find a deny log.

To access the Deny log page, in the WAF page, click **Websites**, and then click **Manage Website** on the website you want to manage.  In the WAF management interface, on the upper bar, hover over **Log**, and then click **Deny log**. For more information about the Dashboard Deny Log page, see [Deny Log ](manual/ch_dashboards.md#ref_dashboards_deny_log.md).

#### Deny logs list

The Deny log page displays all the request resources for the selected proxy that WAF blocked for the website. Failed requests are shown in the deny log, which allows you to  identify broken internal and external links, and broken robots not using the 404 not found message.

Total number of log entries matching the current filter criteria (if specified) is indicated on the upper-right corner of the list. If the total number of records is larger than the entries per page selection, you can  select how many entries you want to view per page in the Show drop-down list, or go to the next page.

Click the inspect icon (![](../../Resources/Images/wsm/alDenyLogDetailsIcon.png)) to view more details for a log entry. The deny logs are organized by columns with the following information:

* Time
* Source IP
* Host
* Risk
* Class
* Action
* Response
* URL Path

You can select log entries to add to the access policy. This allows further requests based on the information in the log entries you selected. After you select all of the log entries to add to the access policy, click **Add selected to ACL** on the lower-right corner.

To delete all log data for the website, click **Flush log**. To generate an HTML version of the logs, select the logs you want in the report, and then click **Log report**.

### Filter the list of deny logs

The Deny log page allows you to filter and narrow the list of results on the page. You can apply any combination of the following filter types to find a deny log:

* Request details
* Response
* Attack classification
* Policy violation
* Country from where the request originated

To define filters for deny logs,  click **Filters** to view the options. You can combine custom search parameters. In the Request section, you can enter specific information related to the log, including ID, reference ID, path, IP, host, date, risk, and deny action. In the Response section, you can select from compromise risk or unlikely.

For the Attack classification, Policy violation, and Country sections, select parameters from the list, and then **Add**, or **Add All** to include all the parameters in the list. You can also **Remove**, or **Remove All** from the list on the right.

After you make your changes, click **Apply**.  To clear the options, click **Reset** and revert to the default filters. Click **Close** to close the filter section.
