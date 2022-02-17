# Web Log Analytics (WLA) Configuration

Alert Logic Web Log Analytics (WLA) is a log-based application attack detection solution that protects your web applications from common application vulnerabilities. WLA reduces the need for tuning and minimizes false-positives using the combination of a machine learning-based analysis and detection engine and signatures. To learn more about WLA, see [About Alert Logic Web Log Analytics (WLA)](../get-started/about-wla.md).

Alert Logic generates   incidents detected from WLA in the  [Incidents](../analyze/incidents.md) page. You can also search for WLA logs in the [Search](../get-started/search-a.md) page in the Alert Logic console. You can access the [Web Log Analytics Dashboard](../analyze/dashboard/web-log-analytics.md), which provides visibility into incidents and observations detected from WLA in your environment.

## Before you configure WLA access log 

To deploy WLA, you must have a Managed Detection and Response Professional or Enterprise subscription. To learn more about Alert Logic Managed Detection and Response products, see [Get Started with Alert Logic   Subscriptions and Add-ons](../get-started/subscriptions-addons.md).  WLA currently supports IIS, Apache2, and Nginx web servers.

You must have an Alert Logic agent or a local remote collector already installed. If you do not have either one already installed, you can do so before you begin deploying WLA. For more information about Alert Logic agents, see [Install the Alert Logic Agent for Windows](../prepare/alert-logic-agent-windows.md) and [Install the Alert Logic Agent for Linux](../prepare/alert-logic-agent-linux.md).For more information about agents, see [Install the Alert Logic Agent for Linux](../prepare/alert-logic-agent-linux.md), [Install the Alert Logic Agent for Windows](../prepare/alert-logic-agent-windows.md), or [Automate Alert Logic Agent Installation with AWS Systems Manager Distributor](../prepare/agent-install-automated-aws.md). For more information about Alert Logic remote collectors, see [Install the  Remote Collector for Linux](../prepare/remote-log-collector-linux.md) and [Install the Remote Collector for Windows](../prepare/remote-log-collector-windows.md).

Linux users who want to collect syslogs must forward their local syslog to the agent on TCP port 1514.

Alert Logic recommends you also have the  following prepared before deploying WLA:

* All application URLs in scope for protection
* List of servers per application
* File system locations of application log files on each server
* Configured proxies, content delivery networks (CDNs), load balancers, or other relevant upstream network systems to insert the X-Forwarded-For header

For large environments, Alert Logic recommends that you use a Alert Logic Managed Web Application Firewall (WAF). For more information, see [Alert Logic Managed Web Application Firewall (WAF) Basics](inline-waf/basics.md).

## IIS 8.5/10 WLA access log configuration

WLA supports Microsoft W3C log formats. For Alert Logic WLA to capture W3C logs for Windows, you must install a third-party agent, Filebeat.

To deploy WLA on an IIS web server:

1. Open IIS Manager. For instructions on how to access IIS Manager, see [Configure Logging in IIS](https://docs.microsoft.com/en-us/iis/manage/provisioning-and-managing-iis/configure-logging-in-iis#to-configure-logging-at-the-site-level-by-using-the-ui).
2. On the left pane, in the Connections, select your website.
3. On the right side, under IIS, click **Logging**.
4. On the Logging page, in the Log file section under Format,  set the log file format to **W3C**.
5. Click **Select Fields**.
6. Ensure the **Directory** field is <kbd>%SystemDrive%\inetpub\logs\LogFiles</kbd>.
7. In the **W3C Logging Fields** dialog box, select all fields, except cs(Cookie).
8. Under Custom Fields, click **Add Field**.
9. Add the Content-Type Header custom field:
   1. In **Field Name**, enter a name for the Content-Type Header.
   2. For the **Source Type**, select **Request Header**.
   3. For **Source**, select **Content-Type**.
11. Add the X-Forwarded-For Header custom field:
   1. In **Field Name**, enter a name for the  X-Forwarded-For Header.
   2. For the **Source Type**, select **Request Header**.
   3. For **Source**, enter the **X-Forwarded-For**.
13. Click **Save**, and then click **Apply**.

### Filebeat

**To install Filebeat**:

1. Refer to [these instruction](https://www.elastic.co/guide/en/beats/filebeat/current/filebeat-installation.html) to download and install Filebeat.			
The Filebeat instructions mention installing Elastic Stack. You can skip this step and proceed to downloading Filebeat.
2. After you download and install Filebeat, replace the <kbd>C:\Program Files\Filebeat\filebeat.yml</kbd> configuration file with this file: [filebeat.yml File.txt](../pdf-files/filebeat.yml File.txt).
3. Configure flat file collection from the Application Logs page in the Alert Logic console. When you add the application log, enter these values:
For more information, see [Configure a flat file collector in the Alert Logic console](#ConfigureaflatfilecollectorintheAlertLogicconsole).
   * For **Application File Path**: <kbd>c:\inetpub\logs\wla</kbd>
   * For **File Name or Pattern**: <kbd>iis.log</kbd>
5. Wait five to 10 minutes for access logs to register in the Alert Logic console. Confirm log messages contain values for host and vhost client IP, XFF, referer, and user agent to verify your host configurations. For more information, see [Search log confirmation in the Alert Logic console](#SearchlogconfirmationintheAlertLogicconsole).

## Linux Apache2 WLA access log configuration

WLA supports Apache Common Log Format and Combined Log Format. Alert Logic provides the custom <kbd>wla_access_log</kbd> format to use with Apache, which includes all of the recommended fields. If you chose not to use the <kbd>wla_access_log</kbd> format, you must ensure the maximum security value fields are added to existing log format configurations.

    WLA does not support Apache Tomcat web server.    
To deploy WLA on a Linux Apache2 web server:

1. Access the CLI of the host you want to configure. You can use Secure Shell (SSH) or any other appropriate CLI. 
You must have sudo/root access to modify the Apache2 configuration and review local access log messages.
2. Locate the appropriate configuration file for the application you want to protect:
   * For RPM based OS, the file is usually located in <kbd>/etc/httpd/conf/httpd.conf</kbd>.
   * For Debian based OS, the file is usually located in <kbd>/etc/apache2/sites-available/</kbd>.
      * If only one website is hosted on the server, the file is located in <kbd>/etc/apache2/apache2.conf</kbd>.
4. Locate the appropriate configuration file for the application you want to protect. The file is usually located in <kbd>/etc/httpd/conf/httpd.conf</kbd>.Steps and examples in this procedure are for RPM based OS. For Debian based OS, the file is usually located in <kbd>/etc/apache2/sites-available/</kbd>. If only one website is hosted on the server, the file is located in <kbd>/etc/apache2/apache2.conf</kbd>.
5. Open the configuration file for editing, and then find the <kbd>LogFormat</kbd> directive.
6. Replace the existing log format with the Alert Logic <kbd>wla_access_log</kbd> format or add the recommended fields to your existing configuration. 			
Example of the <kbd>wla_access_log</kbd> format for HTTPD version greater than or equal to 2.2.30:| LogFormat "@WLALOG \"%{%Y-%m-%dT%T}t.%{msec_frac}t%{%z}t\", \"%{host}i\", \"%a\", \"%{x-forwarded-for}i\", \"%m\", \"%U%q\", \"%>s\", \"%b\", \"%{content-length}i\", \"%{referer}i\", \"%{user-agent}i\", \"%{content-type}i\"" wla_access_log |

Example of the <kbd>wla_access_log</kbd> format for HTTPD version less than 2.2.30:| LogFormat "@WLALOG \"%{%Y-%m-%dT%T}t%{%z}t\", \"%{host}i\", \"%a\", \"%{x-forwarded-for}i\", \"%m\", \"%U%q\", \"%>s\", \"%b\", \"%{content-length}i\", \"%{referer}i\", \"%{user-agent}i\", \"%{content-type}i\"" wla_access_log |

Example of Combined Log Format:| LogFormat "%h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-agent}i\" \"%{X-Forwarded-For}i\"" combined_proxy |
7. You must add a new line at the bottom of the configuration file to ensure the new <kbd>LogFormat</kbd> is applied and logged to the correct file.  In the example below, the <kbd>LogFormat</kbd> was added to line 8, and the new line was added to line 29 under `logs/access_log`. This example is based on an RPM based 	OS. Use your CustomLog path for line 29.
| 1 | <IfModule log_config_module> |
| 2 | # |
| 3 | # The following directives define some format nicknames for use with |
| 4 | # a CustomLog directive (see below). |
| 5 | # |
| 6 | LogFormat "%h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\"" combined |
| 7 | LogFormat "%h %l %u %t \"%r\" %>s %b" common |
| 8 | LogFormat "@WLALOG \"%{%Y-%m-%dT%T}t.%{msec_frac}t%{%z}t\", \"%{host}i\", \"%a\", \"%{x-forwarded-for}i\", \"%m\", \"%U%q\", \"%>s\", \"%b\", \"%{content-length}i\", \"%{referer}i\", \"%{user-agent}i\", \"%{content-type}i\"" wla_access_log |
| 9 |  |
| 10 | <IfModule logio_module> |
| 11 | # You need to enable mod_logio.c to use %I and %O |
| 12 | LogFormat "%h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\" %I %O" combinedio |
| 13 | </IfModule> |
| 14 |  |
| 15 | # |
| 16 | # The location and format of the access logfile (Common Logfile Format). |
| 17 | # If you do not define any access logfiles within a <VirtualHost> |
| 18 | # container, they will be logged here.  Contrariwise, if you *do* |
| 19 | # define per-<VirtualHost> access logfiles, transactions will be |
| 20 | # logged therein and *not* in this file. |
| 21 | # |
| 22 | #CustomLog "logs/access_log" common |
| 23 |  |
| 24 | # |
| 25 | # If you prefer a logfile with access, agent, and referer information |
| 26 | # (Combined Logfile Format) you can use the following directive. |
| 27 | # |
| 28 | # CustomLog "logs/access_log" combined |
| 29 | CustomLog "logs/access_log" wla_access_log |
| 30 |  |
| 31 | </IfModule> |
| 32 |  |

9. Save and close the file.
10. Restart your Apache service.
11. Verify the generation of WLA logs with:
<kbd>tail -n 25</kbd>*/path/to/CustomLog*
12. Configure flat file collection from the Application Logs page in the Alert Logic console. When you add the application log, enter these values:
For more information, see [Configure a flat file collector in the Alert Logic console](#ConfigureaflatfilecollectorintheAlertLogicconsole).
   * For **Application File Path**: The path is usually <kbd>/var/log/httpd</kbd>. For Debian based OS, the path is usually <kbd>/var/log/apache2</kbd>.
   * For **File Name or Pattern**: <kbd>access_log</kbd>
14. Wait five to 10 minutes for access logs to register in the Alert Logic console. Confirm log messages contain values for host and vhost client IP, XFF, referer, and user agent to verify your host configurations. For more information, see [Search log confirmation in the Alert Logic console](#SearchlogconfirmationintheAlertLogicconsole).

## Linux Nginx WLA access log configuration

WLA supports Nginx Common Log Format and Combined Log Format. Alert Logic provides the custom <kbd>wla_access_log</kbd> format to use with Nginx, which includes all of the recommended fields. If you chose not to use the <kbd>wla_access_log</kbd> format, you must ensure the maximum security value fields are added to existing log format configurations.

To deploy WLA on a Linux Nginx web server:

1. Access the CLI of the host for which you want to configure. You can use Secure Shell (SSH) or any other appropriate CLI. 
You must have sudo/root access to modify the Nginx configuration and review local access log messages.
2. Locate the appropriate configuration file for the application you want to protect. The file is usually located in <kbd>/etc/nginx/sites-available/</kbd>. If only one website is hosted on the server, the file is located in <kbd>/etc/nginx/nginx.conf</kbd>.
3. Open the configuration file for editing, and then find the <kbd>log_format</kbd>.
4. Replace the existing log format with the Alert Logic <kbd>wla_access_log</kbd> format or add the recommended fields to your existing configuration.				
Do not click **Copy** as it distorts the code. You must manually copy and paste the code below for it to resolve to a valid code.
Example of a <kbd>wla_access_log</kbd>:| 1 | map $time_iso8601 $time_iso8601_p1 { |
| 2 | ~([^+]+) $1; |
| 3 | } |
| 4 | map $time_iso8601 $time_iso8601_p2 { |
| 5 | ~\+([0-9:]+)$ $1; |
| 6 | } |
| 7 | map $msec $millisec { |
| 8 | ~\.([0-9]+)$ $1; |
| 9 | } |
| 10 | log_format wla_access_log '@WLALOG "$time_iso8601_p1.$millisec+$time_iso8601_p2", ' |
| 11 | '"$http_host", "$remote_addr", ' |
| 12 | '"$http_x_forwarded_for", "$request_method", ' |
| 13 | '"$request_uri", "$status", "$body_bytes_sent", ' |
| 14 | '"$http_content_length", "$http_referer", ' |
| 15 | '"$http_user_agent", "$http_content_type"'; |
| 16 |  |

Example of a Combined Log Format:| 1 | log_format combined_proxy '$remote_addr - $remote_user [$time_local] ' |
| 2 | '"$request" $status $body_bytes_sent ' |
| 3 | '"$http_referer" "$http_user_agent" ' |
| 4 | '"$http_x_forwarded_for"'; |
| 5 |  |
5. You must edit the file to ensure the new <kbd>log_format</kbd> is logged to the correct file. You must modify or add the following line <kbd>access_log  /var/log/nginx/access.log wla_access_log;</kbd> as the main line. Your file will look similar to the example below.

  | http { |
  | #    log_format  main  '$remote_addr - $remote_user [$time_local] "$request" ' |
  | #                      '$status $body_bytes_sent "$http_referer" ' |
  | #                      '"$http_user_agent" "$http_x_forwarded_for"'; |
  |  |
  | map $time_iso8601 $time_iso8601_p1 { |
  | ~([^+]+) $1; |
  | } |
  | map $time_iso8601 $time_iso8601_p2 { |
  | ~\+([0-9:]+)$ $1; |
  | } |
  | map $msec $millisec { |
  | ~\.([0-9]+)$ $1; |
  | } |
  |  |
  | log_format wla_access_log '@WLALOG "$time_iso8601_p1.$millisec+$time_iso8601_p2", ' |
  | '"$http_host", "$remote_addr", ' |
  | '"$http_x_forwarded_for", "$request_method", ' |
  | '"$request_uri", "$status", "$body_bytes_sent", ' |
  | '"$http_content_length", "$http_referer", ' |
  | '"$http_user_agent", "$http_content_type"'; |
  |  |
  | access_log  /var/log/nginx/access.log wla_access_log; |
  |  |
6. Save and close the file.
7. Restart the Nginx service.
8. Configure flat file collection from the Application Logs page in the Alert Logic console. When you add the application log, enter these values:
For more information, see [Configure a flat file collector in the Alert Logic console](#ConfigureaflatfilecollectorintheAlertLogicconsole).
   * For **Application File Path**: <kbd>/var/log/nginx</kbd>
   * For **File Name or Pattern**: <kbd>access.log</kbd>
10. Wait five to 10 minutes for access logs to register in the Alert Logic console. Confirm log messages contain values for host and vhost client IP, XFF, referer, and user agent to verify your host configurations. For more information, see [Search log confirmation in the Alert Logic console](#SearchlogconfirmationintheAlertLogicconsole).

## Configure a flat file collector in the Alert Logic console

You must configure a collection method and policy from the deployment from which you want to collect in the Alert Logic console. The collection method and policy you configure determine which flat file log messages to collect, how to separate log messages within a flat file, and how to read the time of each log message. Rules determine the asset tags, assets, or topology elements from which Alert Logic collects logs.

To access the log collection setup, from the navigation menu, click ![](../Resources/Images/dashboard/configure-icon.png)**Configure**, and then click the deployment for which you want to configure collections. On the left navigation panel, click **Logs**, and then click **Application Logs**.

When you add the application log, see the instructions for WLA access log configuration relevant to your deployment's web server in this document for the values to enter in the **Application File Path** and **File Name or Pattern** fields.

For WLA deployments on IIS web servers, you must use the file path pattern processed by the Filebeat agent.

For more information about the Application Logs page, see [Application Logs for Flat File Configuration](application-logs.md).

## Search log confirmation in the Alert Logic console

To confirm that you configured WLA and  you are collecting logs, search for your messages in the Search page in the Alert Logic console. You can use this link to [open the query in the Alert Logic console](https://console.search.alertlogic.com/#/search/expert/acting?mode=simple&amp;sql=SELECT%0A%20%20%20%20time_recv%20AS%20%22Time%20Received%22,%0A%20%20%20%20message%20AS%20%22Message%22,%0A%20%20%20%20parsed.rule_name%20AS%20%22Message%20Type%22%0AFROM%20logmsgs%0AWHERE%20EXISTS(%20%22Message%22%20)%0A%20%20%20%20AND%0A%22Message%20Type%22%20%3D%20%27WLA%20Access%20Log%27%0AORDER%20BY%20%22Time%20Received%22%20DESC%0ALIMIT%201000&amp;timeframe=3600). When you click the link, it opens the Search page with the query already inserted for you:

`[Message Type] = 'WLA Access Log'`

You can narrow the search with a whitelist like the destination hosts for which you configured the log collection.

<kbd>[destination_host]</kbd> = <kbd>"mutillidae.alqalabs.com" OR [destination_host]</kbd> = <kbd>"bwapp.alqalabs.com" OR [destination_host]</kbd> = <kbd>"gb.alqalabs.com")</kbd>

Review the log entry timestamps to verify log collection, and review log entries to confirm inclusion of security value fields like host and vhost client IP, XFF, referer, and user agent.

For more information about the Search page, see [Get Started with Search](../get-started/search-a.md).
