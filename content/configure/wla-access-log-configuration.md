# Web Log Analytics (WLA) Access Configuration

Alert Logic offers a log-based application attack detection solution. WLA is a combination of the anomaly detection, ActiveRules signatures, and advance correlation to provide coverage for most of the Open Web Application Security Project (OWASP) Top 10. WLA allows your organization to save on resources infrastructure, reduce the need for tuning, and provides almost no false-positives from the machine-learning based analysis and detection engine.

To deploy WLA, you must have Managed Detection and Response Professional or Enterprise subscription. To learn more about Alert Logic Managed Detection and Response products, see [Get Started with Alert Logic   Subscriptions and Add-ons](../get-started/subscriptions-addons.md).

The general workflow to configure WLA is the following:

1. For Apache or Nginx, you must modify LogFormat directives. If you are using an Microsoft IIS web server, install and configure a Filebeat agent.
2. [Install the Remote Collector for Windows](../prepare/remote-log-collector-windows.md), if you do not already have one installed.
3. Configure a flat-file collection policy in the Alert Logic console.
4. In the Alert Logic console, in the [Search: Log Messages](../analyze/log-message-search.md) page, confirm the log messages are there and parsed correctly.

To begin configuring WLA you must have:

* A configuration management tool, such as Chef, Ansible, Terraform, or Puppet
* Gather URLs application in scope for protection
* Apache, Nginx, IIS, WSM webserver
* Required API tokens for authentication
* Content delivery networks like Akamai, CloudFront oe network-based DDoS service deployed in front of the applications

## WLA parsers

WLA parsers are not anchored and can match supported log formats in substrings. This is tolerant for logging metadata that commonly prepend log messages, and does not break support if you append custom fields to your log messages. The following are the parser, output formats, and their supported web servers:

| Parser | Web Server | Format |
|---|---|---|
| wla_access_log (Recommended configuration) | Apache, Nginx, IIS (filebeat) | Alert Logic WLA access logs |
| combined_proxy | Apache, Nginx | Common log file |
| iis_default | IIS | IIS log |
| iis_custom | IIS | W3C extended log |
| alb |  | AWS application load balancer log |
| wsm |  | Alert Logic Managed Web Application Firewall (WAF) deny logs |

### Configuration using WLA access log 

The following log format supplies all recommended fields for WLA:

<kbd>@WLALOG "TIMESTAMP", "HOST", "CLIENT_IP", "X_FORWARDED_FOR", "METHOD", "URI", "STATUS_CODE", "SENT_BYTES", "RECEIVED_BYTES", "REFERRER", "USER_AGENT", "CONTENT_TYPE"</kbd>

Supported fields for WLA_access_log include:

<kbd>TIMESTAMP, HOST, CLIENT_IP, X_FORWARDED_FOR, METHOD, URI, STATUS_CODE, SENT_BYTES, RECEIVED_BYTES, REFERRER, USER_AGENT, CONTENT_TYPE</kbd>

#### Apache HTTPD WLA access log configuration

<kbd>LogFormat "@WLALOG \"%{%Y-%m-%dT%T}t%{%z}t\", \"%{host}i\", \"%a\", \"%{x-forwarded-for}i\", \"%m\", \"%U%q\", \"%&amp;gt;s\", \"%b\", \"%{content-length}i\", \"%{referer}i\", \"%{user-agent}i\", \"%{content-type}i\"" wla_access_log</kbd>

#### Nginx WLA access log configuration

<kbd>log_format wla_access_log '@WLALOG "$time_iso8601", "$http_host", "$remote_addr", '</kbd>

<kbd> '"$http_x_forwarded_for", "$request_method", ' </kbd>
<kbd>'"$request_uri", "$status", "$body_bytes_sent", ' </kbd>

<kbd>'"$http_content_length", "$http_referer", ' </kbd>

<kbd>'"$http_user_agent", "$http_content_type"';</kbd>

#### IIS 8.5 WLA access log configuration

Open IIS Manager, and in per site logging configuration, set the log file format to **W3C**. Ensure that the log file directory is %SystemDrive%\inetpub\logs\LogFiles. Click **Select Fields**, and enable all fields, except cs(Cookie).

Under Custom Fields, add the following custom fields in order:

1. Content-Type Header
   * Source: Content-Type
   * Log Field: Content-Type
   * Source Type: Request Header
4. X-Forwarded-For Header
   * Log Field: X-Forwarded-For
   * Source Type: Request Header
   * Source: X-Forwarded-For
6. Save, and then apply settings.

##### Filebeat

To install Filebeat, see [these instruction](https://www.elastic.co/guide/en/beats/filebeat/current/filebeat-installation.html), and then replace C:\Program Files\Filebeat\filebeat.yml with [here](../pdf-files/filebeat-IIS-WLA-conf.txt).

### Configuration using Common log file format

The combined_proxy parser matches log formats based on [Common log file format](https://www.w3.org/Daemon/User/Config/Logging.html#common_logfile_format), and is shared across many applications. The parser supports the minimum fields in Common log file format, and optionally the extended fields <kbd>REFERRER</kbd>, <kbd>USER_AGENT</kbd>, and <kbd>X_FORWARDED_FOR</kbd>.

Combined proxy parsers can be used for the following web servers:

* Apache HTTP
* NGINX
* Microsoft Intenet Information Services (IIS)

Supported fields combined_proxy parser include:

<kbd>CLIENT_IP, METHOD, URI, HTTP_VERSION, STATUS_CODE, SENT_BYTES, REFERRER, USER_AGENT, X_FORWARDED_FOR</kbd>

#### Apache HTTP Common log file format configuration

For Apache HTTP, the built-in common log and combined log formats  are supported by the combined_proxy parser. The fields from the default formats can be parsed with no custom configuration.

To include the recommended fields use this log format directive:

<kbd>LogFormat "%h %l %u %t \"%r\" %&amp;gt;s %b \"%{Referer}i\" \"%{User-agent}i\" \"%{X-Forwarded-For}i\"" combined_proxy</kbd>

#### Nginx Common log file format configuration

For Nginx, the built-in common log and combined log formats are supported by combined_proxy parser. The fields from the default formats can be parsed. To include the recommended fields use this configuration:

<kbd>log_format combined_proxy '$remote_addr - $remote_user [$time_local] ' </kbd>

<kbd>'"$request" $status $body_bytes_sent ' </kbd>

<kbd>'"$http_referer" "$http_user_agent" ' </kbd>

<kbd>'"$http_x_forwarded_for"';</kbd>

#### Microsoft IIS  in NCSA Common log file format configuration

Microsoft Internet Information Services (IIS) servers that are configured to output logs in NCSA Common file format are matched and processed by combined_proxy parser.

### Configuration using IIS logging 

Microsoft IIS that are configured to output logs in [IIS log format](https://docs.microsoft.com/en-us/windows/win32/http/iis-logging) are matched and processed by iis_default log parser.

Supported fields for iis_default parsers include:

<kbd>CLIENT_IP, TIMESTAMP, STATUS_CODE, METHOD, URI_PATH, URI_QUERY</kbd>

### Configuration using W3C Extended format 

The Microsoft IIS commonly observed logs are generated in [W3C Extended formats](https://www.w3.org/TR/WD-logfile.html) are matched and processed by iis_custom parser. For configuration instructions, see [Configuration using WLA access log ](#WLA_acce).

Supported fields for iis_custom parser include:

<kbd>TIMESTAMP, METHOD, URI_PATH, URI_QUERY, CLIENT_IP, HTTP_VERSION, USER_AGENT, REFERRER, HOST, STATUS_CODE</kbd>

### AWS application load balancer (ALB)

AWS Application Load Balancer (ALB) generates access log file that are matched and processed by alb parser. For more information about ALB access logs, see [Load balancer access log entries](https://docs.aws.amazon.com/elasticloadbalancing/latest/application/load-balancer-access-logs.html#access-log-entry-format).

Supported fields for alb parser include:

<kbd>TYPE, TIMESTAMP, CLIENT_IP, PROCESS_TIME, TARGET_PROCESS_TIME, RESPONSE_PROCESS_TIME, STATUS_CODE, TARGET_STATUS_CODE, RECEIVED_BYTES, SENT_BYTES, METHOD, URI, HTTP_VERSION, USER_AGENT, CIPHER, SSL_PROTOCOL, HOST, ACTION, REDIRECT_URL, ERROR</kbd>

### WAF deny logs

This parser matches Web Security Manager (WSM) deny logs.

## Install Alert Logic remote collector

After you have made the necessary changes to your web server or server software, if you have not already, you must install the Alert Logic remote collector for Windows. For instructions, see [Install the Remote Collector for Windows](../prepare/remote-log-collector-windows.md).

## Configure a flat file collector in the Alert Logic console

You must configure a collection method and policy from the deployment from which you want to collect in the Alert Logic console. The collection method and policy you configure determines which flat file log messages to collect, how to separate log messages within a flat file, and how to read the time of each log message. Rules determine the asset tags, assets, or topology elements from which Alert Logic collects logs. For more information about the Application Logs page, see [Application Logs for Flat File Configuration](application-logs.md).

## Search log confirmation in the Alert Logic console

To confirm that you have configured WLA access logs and  your messages are parsed correctly, search for your messages in the [Search: Log Messages](../analyze/log-message-search.md) page in the Alert Logic console.

The following are examples of fields you can use:

| Access log field  | Usage |
|---|---|
| CLIENT_IP (string): | The IP address and port of the client. |
| CONTENT_TYPE (string): | The value of the ContentType HTTP header. |
| DATA (string): | WAF log field, request content. |
| DOMAIN (string): | The configured domain name for the server. Mostly for ALB logs. |
| ERROR (string): | Any error that occurred while processing the request, specifically if proxying. |
| HOST (string): | HTTP request host. This ideally is the value of the Host header. |
| HTTP_VERSION (string): | HTTP request protocol version. |
| METHOD (string): | HTTP request method. |
| PORT (int32): | Server listening port number. |
| PROCESS_TIME (int64): | The total time for a request from the client. |
| RECEIVED_BYTES (int64): | The number of bytes received from the client. |
| REFERRER (string): | The value of the Referer HTTP header. |
| REQUEST_ID (string): | WAF log field, the WAF unique request id. |
| SENT_BYTES (int64): | The number of bytes sent to the client. |
| STATUS_CODE (int32): | Server response status code. |
| TIMESTAMP (string): | The time and date when a request completed. |
| USER_AGENT (string): | The value of the User-Agent HTTP header. |
| VIOLATION_TYPE (string): | WAF log field, they type of violation that triggered the block event. |
| X_FORWARDED_FOR (string): | The value of the X-Forwarded-For HTTP header. |
